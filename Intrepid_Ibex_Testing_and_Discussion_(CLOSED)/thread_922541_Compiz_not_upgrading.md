---
title: "Compiz not upgrading"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kienzan on 2008-09-17
Hey Everyone! 

I updated the update manager this mourning and I got the "Not all updates could be installed, run a partial upgrade" window. I looked to see what wouldn't upgrade and it was compiz! I went into synaptic and terminal and tried upgrading from there and got this:

compiz:
 Depends: compiz-gnome but it is not going to be installed
 Depends: compiz-fusion-plugins-main but it is not going to be installed
 Depends: compiz-fusion-plugins-extra but it is not going to be installed
 Depends: libcompizconfig0 but it is not going to be installed

Now I tried installing them but got the same kinds of errors, kinda like a paradox of failure to upgrade =\

Is there anyway through this? Is there any .deb files I could get of this latest version?

---

### Post by kienzan on 2008-09-17
This is compiz 0.7.8 we are talking about. I downloaded the .tar.gz file and tried ./configure. Everything seemed to work then tried sudo make and got this:

make[2]: Leaving directory `/home/kienzan/Desktop/compiz-0.7.8/include'
Making all in src
make[2]: Entering directory `/home/kienzan/Desktop/compiz-0.7.8/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kienzan/Desktop/compiz-0.7.8/src'
Making all in libdecoration
make[2]: Entering directory `/home/kienzan/Desktop/compiz-0.7.8/libdecoration'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kienzan/Desktop/compiz-0.7.8/libdecoration'
Making all in plugins
make[2]: Entering directory `/home/kienzan/Desktop/compiz-0.7.8/plugins'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/libpng12 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/share/qt3/include -I/usr/include/kde -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DFUSE_USE_VERSION=26 -DALL_LINGUAS="\"af ar bg bn bn_IN bs ca cs cy da de el en_GB en_US es eu et fi fr gl gu he hi hr hu id it ja ka km ko lo lt mk mr nb nl or pa pl pt pt_BR ro ru sk sl sr sv ta tr uk vi xh zh_CN zh_TW zu\"" -DLOCALEDIR="\"/usr/local/share/locale\"" -DPLUGINDIR=\"/usr/local/lib/compiz\" -DIMAGEDIR=\"/usr/local/share/compiz\" -I../include -I../include -DMETADATADIR=\"/usr/local/share/compiz\"    -g -O2 -Wall -D_FORTIFY_SOURCE=2 -MT kconfig.lo -MD -MP -MF .deps/kconfig.Tpo -c -o kconfig.lo kconfig.cpp
 g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/libpng12 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/share/qt3/include -I/usr/include/kde -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DFUSE_USE_VERSION=26 "-DALL_LINGUAS=\"af ar bg bn bn_IN bs ca cs cy da de el en_GB en_US es eu et fi fr gl gu he hi hr hu id it ja ka km ko lo lt mk mr nb nl or pa pl pt pt_BR ro ru sk sl sr sv ta tr uk vi xh zh_CN zh_TW zu\"" -DLOCALEDIR=\"/usr/local/share/locale\" -DPLUGINDIR=\"/usr/local/lib/compiz\" -DIMAGEDIR=\"/usr/local/share/compiz\" -I../include -I../include -DMETADATADIR=\"/usr/local/share/compiz\" -g -O2 -Wall -D_FORTIFY_SOURCE=2 -MT kconfig.lo -MD -MP -MF .deps/kconfig.Tpo -c kconfig.cpp  -fPIC -DPIC -o .libs/kconfig.o
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kglobal.h:22,
                 from kconfig.cpp:20:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from kconfig.cpp:20:
/usr/include/kglobal.h:23:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from kconfig.cpp:21:
/usr/include/kstandarddirs.h:26:30: error: QtCore/QStringList: No such file or directory
/usr/include/kstandarddirs.h:28:23: error: QtCore/QMap: No such file or directory
In file included from kconfig.cpp:22:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/kconfig.h:31:26: error: QtCore/QString: No such file or directory
/usr/include/kconfig.h:32:27: error: QtCore/QVariant: No such file or directory
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
/usr/include/kconfig.h:34:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
In file included from kconfig.cpp:20:
/usr/include/kglobal.h:385: error: expected initializer before '&' token
/usr/include/kglobal.h:404: error: expected initializer before '&' token
/usr/include/kglobal.h:465: error: 'QString' does not name a type
In file included from kconfig.cpp:21:
/usr/include/kstandarddirs.h:187: error: 'SearchOptions' has not been declared
/usr/include/kstandarddirs.h:192: error: expected ';' before 'virtual'
/usr/include/kstandarddirs.h:203: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:212: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:221: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:247: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:271: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:298: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:318: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:336: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:351: error: 'quint32' does not name a type
/usr/include/kstandarddirs.h:371: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:394: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:416: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:442: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:456: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:478: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:500: error: 'QStringList' has not been declared
/usr/include/kstandarddirs.h:500: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:526: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:534: error: 'QStringList' does not name a type
/usr/include/kstandarddirs.h:553: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:572: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:584: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:624: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:629: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:634: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:639: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:647: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:653: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:659: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:665: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:674: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:683: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:692: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:705: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:721: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:739: error: 'QString' does not name a type
/usr/include/kstandarddirs.h:757: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:767: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:773: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:773: error: 'void KStandardDirs::addPrefix(int)' cannot be overloaded
/usr/include/kstandarddirs.h:203: error: with 'void KStandardDirs::addPrefix(int)'
/usr/include/kstandarddirs.h:774: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:774: error: 'void KStandardDirs::addXdgConfigPrefix(int)' cannot be overloaded
/usr/include/kstandarddirs.h:212: error: with 'void KStandardDirs::addXdgConfigPrefix(int)'
/usr/include/kstandarddirs.h:775: error: expected ',' or '...' before '&' token
/usr/include/kstandarddirs.h:775: error: 'void KStandardDirs::addXdgDataPrefix(int)' cannot be overloaded
/usr/include/kstandarddirs.h:221: error: with 'void KStandardDirs::addXdgDataPrefix(int)'
/usr/include/kstandarddirs.h: In member function 'bool KStandardDirs::addResourceType(const char*, const char*, const char*, bool)':
/usr/include/kstandarddirs.h:277: error: 'QLatin1String' was not declared in this scope
/usr/include/kstandarddirs.h: At global scope:
/usr/include/kstandarddirs.h:781: error: expected constructor, destructor, or type conversion before '(' token
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/kconfigbase.h:66: error: 'WriteConfigFlags' has not been declared
/usr/include/kconfigbase.h:71: error: expected ';' before 'virtual'
/usr/include/kconfigbase.h:86: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:88: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:88: error: 'bool KConfigBase::hasGroup(int) const' cannot be overloaded
/usr/include/kconfigbase.h:86: error: with 'bool KConfigBase::hasGroup(int) const'
/usr/include/kconfigbase.h:97: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:98: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:98: error: 'KConfigGroup KConfigBase::group(int)' cannot be overloaded
/usr/include/kconfigbase.h:97: error: with 'KConfigGroup KConfigBase::group(int)'
/usr/include/kconfigbase.h:104: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:105: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:105: error: 'const KConfigGroup KConfigBase::group(int) const' cannot be overloaded
/usr/include/kconfigbase.h:104: error: with 'const KConfigGroup KConfigBase::group(int) const'
/usr/include/kconfigbase.h:112: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:113: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:113: error: 'void KConfigBase::deleteGroup(int)' cannot be overloaded
/usr/include/kconfigbase.h:112: error: with 'void KConfigBase::deleteGroup(int)'
/usr/include/kconfigbase.h:114: error: 'WriteConfigFlags' has not been declared
/usr/include/kconfigbase.h:161: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:162: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:162: error: 'bool KConfigBase::isGroupImmutable(int) const' cannot be overloaded
/usr/include/kconfigbase.h:161: error: with 'bool KConfigBase::isGroupImmutable(int) const'
/usr/include/kconfigbase.h:168: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:169: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:170: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:171: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:172: error: expected ',' or '...' before '&' token
/usr/include/kconfigbase.h:180: error: expected constructor, destructor, or type conversion before '(' token
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/kconfig.h:84: error: 'OpenFlags' has not been declared
/usr/include/kconfig.h:86: error: expected ';' before 'explicit'
/usr/include/kconfig.h:89: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:104: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:113: error: 'QString' does not name a type
/usr/include/kconfig.h:147: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:162: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:194: error: 'QString' does not name a type
/usr/include/kconfig.h:202: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:250: error: expected ';' before '<' token
/usr/include/kconfig.h:253: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:254: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:255: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:256: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:257: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:272: error: expected ',' or '...' before '&' token
/usr/include/kconfig.h:276: error: expected ';' before 'Q_DECLARE_PRIVATE'
/usr/include/kconfig.h:277: error: expected `;' before '}' token
/usr/include/kconfig.h:278: error: expected constructor, destructor, or type conversion before '(' token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/ksharedptr.h:187: error: expected constructor, destructor, or type conversion before 'bool'
/usr/include/ksharedptr.h:193: error: expected constructor, destructor, or type conversion before 'bool'
/usr/include/ksharedptr.h:199: error: expected constructor, destructor, or type conversion before 'void'
/usr/include/ksharedptr.h:210: error: expected constructor, destructor, or type conversion before 'void'
In file included from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/ksharedconfig.h:37: error: expected class-name before '{' token
/usr/include/ksharedconfig.h:53: error: expected ',' or '...' before '&' token
/usr/include/ksharedconfig.h:58: error: expected ',' or '...' before '&' token
/usr/include/ksharedconfig.h:65: error: expected ',' or '...' before '&' token
/usr/include/ksharedconfig.h:66: error: expected ',' or '...' before '&' token
/usr/include/ksharedconfig.h:68: error: expected ',' or '...' before '&' token
In file included from /usr/include/kapplication.h:45,
                 from kconfig.cpp:22:
/usr/include/kcomponentdata.h:100: error: invalid use of incomplete type 'struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'struct QByteArray'
In file included from kconfig.cpp:22:
/usr/include/kapplication.h:82: error: expected class-name before '{' token
/usr/include/kapplication.h:83: error: 'Q_OBJECT' does not name a type
/usr/include/kapplication.h:190: error: 'QSessionManager' has not been declared
/usr/include/kapplication.h:197: error: 'QSessionManager' has not been declared
/usr/include/kapplication.h:241: error: 'QWidget' has not been declared
/usr/include/kapplication.h:284: error: 'QWidget' has not been declared
/usr/include/kapplication.h:290: error: expected ',' or '...' before '*' token
/usr/include/kapplication.h:374: error: 'QObject' has not been declared
/usr/include/kapplication.h:374: error: 'QEvent' has not been declared
/usr/include/kapplication.h:396: error: expected `:' before 'Q_SLOTS'
/usr/include/kapplication.h:402: error: 'Q_SCRIPTABLE' was not declared in this scope
/usr/include/kapplication.h:402: error: expected ';' before 'void'
/usr/include/kapplication.h:405: error: expected ';' before 'void'
/usr/include/kapplication.h:406: error: expected ';' before 'void'
/usr/include/kapplication.h:436: error: expected primary-expression before 'void'
/usr/include/kapplication.h:436: error: expected ';' before 'void'
/usr/include/kapplication.h:471: error: 'd' is not a type
/usr/include/kapplication.h:472: error: expected ';' before 'Q_PRIVATE_SLOT'
/usr/include/kapplication.h:474: error: expected `;' before '}' token
In file included from /usr/share/qt3/include/qiodevice.h:46,
                 from /usr/share/qt3/include/qfile.h:45,
                 from kconfig.cpp:24:
/usr/share/qt3/include/qcstring.h:119: error: conflicting declaration 'typedef class QMemArray<char> QByteArray'
/usr/include/kcomponentdata.h:25: error: 'struct QByteArray' has a previous declaration as 'struct QByteArray'
/usr/share/qt3/include/qcstring.h: In function 'QByteArray qCompress(const QByteArray&)':
/usr/share/qt3/include/qcstring.h:125: error: return type 'struct QByteArray' is incomplete
/usr/share/qt3/include/qcstring.h:126: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qcstring.h:126: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qcstring.h: In function 'QByteArray qUncompress(const QByteArray&)':
/usr/share/qt3/include/qcstring.h:127: error: return type 'struct QByteArray' is incomplete
/usr/share/qt3/include/qcstring.h:128: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qcstring.h:128: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qcstring.h: At global scope:
/usr/share/qt3/include/qcstring.h:146: error: invalid use of incomplete type 'struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'struct QByteArray'
/usr/share/qt3/include/qcstring.h: In copy constructor 'QCString::QCString(const QCString&)':
/usr/share/qt3/include/qcstring.h:150: error: type 'QByteArray' is not a direct base of 'QCString'
/usr/share/qt3/include/qcstring.h: In member function 'QCString& QCString::operator=(const QCString&)':
/usr/share/qt3/include/qcstring.h:252: error: 'assign' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'QCString& QCString::operator=(const char*)':
/usr/share/qt3/include/qcstring.h:255: error: 'duplicate' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'bool QCString::isNull() const':
/usr/share/qt3/include/qcstring.h:258: error: 'data' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'bool QCString::isEmpty() const':
/usr/share/qt3/include/qcstring.h:261: error: 'data' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'uint QCString::length() const':
/usr/share/qt3/include/qcstring.h:264: error: 'data' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'QCString QCString::copy() const':
/usr/share/qt3/include/qcstring.h:270: error: 'data' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In member function 'QCString::operator const char*() const':
/usr/share/qt3/include/qcstring.h:294: error: 'data' was not declared in this scope
/usr/share/qt3/include/qcstring.h: In function 'bool operator==(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:302: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:302: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator==(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:305: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator==(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:308: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator!=(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:311: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:311: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator!=(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:314: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator!=(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:317: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:320: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:320: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:323: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:326: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<=(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:329: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:329: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<=(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:332: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator<=(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:335: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:338: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:338: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:341: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:344: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>=(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:347: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h:347: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>=(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:350: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'bool operator>=(const char*, const QCString&)':
/usr/share/qt3/include/qcstring.h:353: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'const QCString operator+(const QCString&, const QCString&)':
/usr/share/qt3/include/qcstring.h:358: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'const QCString operator+(const QCString&, const char*)':
/usr/share/qt3/include/qcstring.h:365: error: 'const class QCString' has no member named 'data'
/usr/share/qt3/include/qcstring.h: In function 'const QCString operator+(const QCString&, char)':
/usr/share/qt3/include/qcstring.h:379: error: 'const class QCString' has no member named 'data'
In file included from /usr/share/qt3/include/qfile.h:46,
                 from kconfig.cpp:24:
/usr/share/qt3/include/qstring.h: In member function 'QString& QString::insert(uint, const QByteArray&)':
/usr/share/qt3/include/qstring.h:900: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qstring.h:901: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qstring.h: In member function 'QString& QString::operator+=(const QByteArray&)':
/usr/share/qt3/include/qstring.h:922: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
/usr/share/qt3/include/qstring.h:923: error: invalid use of incomplete type 'const struct QByteArray'
/usr/include/kcomponentdata.h:25: error: forward declaration of 'const struct QByteArray'
In file included from /usr/include/X11/Xlib-xcb.h:8,
                 from ../include/compiz-core.h:36,
                 from kconfig.cpp:26:
/usr/include/X11/Xlib.h: At global scope:
/usr/include/X11/Xlib.h:519: error: conflicting declaration 'typedef struct _XDisplay Display'
/usr/include/kapplication.h:41: error: 'Display' has a previous declaration as 'typedef void Display'
kconfig.cpp:30: error: expected initializer before '*' token
kconfig.cpp: In function 'void kconfigSetOption(CompObject*, CompOption*, const char*)':
kconfig.cpp:198: error: 'class KConfig' has no member named 'setGroup'
kconfig.cpp:203: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp:207: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp:210: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp:218: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp:227: error: 'QValueList' was not declared in this scope
kconfig.cpp:227: error: expected primary-expression before 'int'
kconfig.cpp:227: error: expected `;' before 'int'
kconfig.cpp:230: error: 'list' was not declared in this scope
kconfig.cpp:232: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp:232: error: 'list' was not declared in this scope
kconfig.cpp:243: error: aggregate 'QStringList list' has incomplete type and cannot be defined
kconfig.cpp:250: error: 'class KConfig' has no member named 'writeEntry'
kconfig.cpp: In function 'int kconfigReadOptionValue(CompObject*, KConfig*, CompOption*, CompOptionValue*)':
kconfig.cpp:351: error: 'class KConfig' has no member named 'readBoolEntry'
kconfig.cpp:354: error: 'class KConfig' has no member named 'readNumEntry'
kconfig.cpp:357: error: 'class KConfig' has no member named 'readDoubleNumEntry'
kconfig.cpp:366: error: 'class KConfig' has no member named 'readEntry'
kconfig.cpp:379: error: 'QValueList' was not declared in this scope
kconfig.cpp:379: error: expected primary-expression before 'int'
kconfig.cpp:379: error: expected `;' before 'int'
kconfig.cpp:381: error: 'list' was not declared in this scope
kconfig.cpp:381: error: 'class KConfig' has no member named 'readIntListEntry'
kconfig.cpp:406: error: aggregate 'QStringList list' has incomplete type and cannot be defined
kconfig.cpp:408: error: 'class KConfig' has no member named 'readListEntry'
kconfig.cpp: In function 'void kconfigGetOption(CompObject*, CompOption*, const char*)':
kconfig.cpp:460: error: 'class KConfig' has no member named 'setGroup'
kconfig.cpp:462: error: 'class KConfig' has no member named 'hasKey'
kconfig.cpp: In function 'int kconfigInitCore(CompPlugin*, CompCore*)':
kconfig.cpp:617: error: invalid conversion from 'const char*' to 'int'
kconfig.cpp:617: error:   initializing argument 1 of 'KConfig::KConfig(int)'
kconfig.cpp:628: error: 'class KStandardDirs' has no member named 'saveLocation'
kconfig.cpp: In function 'int kconfigInit(CompPlugin*)':
kconfig.cpp:709: error: 'kInstance' was not declared in this scope
kconfig.cpp:709: error: expected type-specifier before 'KInstance'
kconfig.cpp:709: error: expected `;' before 'KInstance'
kconfig.cpp: In function 'void kconfigFini(CompPlugin*)':
kconfig.cpp:725: error: 'kInstance' was not declared in this scope
make[2]: *** [kconfig.lo] Error 1
make[2]: Leaving directory `/home/kienzan/Desktop/compiz-0.7.8/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kienzan/Desktop/compiz-0.7.8'
make: *** [all] Error 2
kienzan@kienzan-desktop:~/Desktop/compiz-0.7.8$

---

### Post by taavikko on 2008-09-17
Just wait patiently, and dependencys will be solved.
every morning and night
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by kienzan on 2008-09-17
Oh so it's nothing on my part? Okay I def can wait patiently haha!

---

### Post by kienzan on 2008-09-17
Noone else is having this problem are they?

---

