PORTNAME=		atds3
DISTVERSION=	1.5.0
CATEGORIES=		net

USE_GITHUB=		yes
GH_ACCOUNT=		leiniercs
GH_TAGNAME=		v1.5.0

LICENSE=		BSD3CLAUSE
LICENSE_FILE= 	${WRKSRC}/LICENSE

MAINTAINER=		leiniercs@gmail.com
COMMENT=		Administrador de Transferencias para toDus (S3)

USES=			compiler ssl gl xorg qt:5 qmake
USE_GL+=		gl
USE_QT+=		qmake_build buildtools_build core gui widgets declarative quickcontrols quickcontrols2 svg sql sql-sqlite3 network websockets multimedia

QMAKE_ARGS+=	QMAKE_INSTALL_PREFIX=${LOCALBASE} CONFIG-=debug CONFIG-=qml_debug CONFIG-=separate_debug_info CONFIG+=qtquickcompiler CONFIG+=release

BUILD_DEPENDS=	qmake:devel/qt5-qmake
LIB_DEPENDS=	libssl.so:security/openssl libcrypto.so:security/openssl
RUN_DEPENDS=	7z:archivers/p7zip rar:archivers/rar

pre-configure:
	protoc --experimental_allow_proto3_optional --proto_path=${WRKSRC}/documentos/protobuf --cpp_out=${WRKSRC} todus.proto
	mv ${WRKSRC}/todus.pb.h ${WRKSRC}/cabeceras
	mv ${WRKSRC}/todus.pb.cc ${WRKSRC}/fuentes

.include <bsd.port.mk> 
