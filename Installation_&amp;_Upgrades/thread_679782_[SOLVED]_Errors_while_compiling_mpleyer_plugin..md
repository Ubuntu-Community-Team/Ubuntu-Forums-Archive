---
title: "[SOLVED] Errors while compiling mpleyer plugin."
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by macaholic on 2008-01-27
First off, I use 64-bit ubuntu, with 64-bit swiftweasel 3.0b2, and I have a patched mplayer built from the source. My issue is that I want to have the mplayer plugin, but it won't compile correctly. So i run "./configure --prefix=/usr --with-mozilla-home=/usr/lib/mozilla-trunk", and everything seems to be normal, but when I try to "make" it, I get errors.
```
/usr/lib/firefox/xpidl -w -m header -I /usr/share/idl/firefox -I Source -e Source/nsIScriptableMplayerPlugin.h Source/nsIScriptableMplayerPlugin.idl
g++ -c -o plugin.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIMemory.h:58: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -c -o nsScriptablePeer.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  Source/nsScriptablePeer.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o npp_gate.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/npp_gate.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
g++ -c -o np_entry.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/np_entry.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
g++ -c -o npn_gate.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/npn_gate.cpp
g++ -c -o plugin-support.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin-support.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
Source/plugin-support.cpp: In function ‘void unEscapeXML(char*)’:
Source/plugin-support.cpp:26: warning: unused variable ‘p’
Source/plugin-support.cpp: In function ‘void fullyQualifyURL(nsPluginInstance*, char*, char*)’:
Source/plugin-support.cpp:629: warning: format ‘%i’ expects type ‘int’, but argument 4 has type ‘long int’
g++ -c -o plugin-setup.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   -DSTD Source/plugin-setup.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o plugin-list.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin-list.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
Source/plugin-list.cpp: In function ‘void buildPlaylist(nsPluginInstance*, char*, Node*)’:
Source/plugin-list.cpp:309: warning: unused variable ‘entry’
Source/plugin-list.cpp:309: warning: unused variable ‘href’
Source/plugin-list.cpp:309: warning: unused variable ‘repeat’
Source/plugin-list.cpp:316: warning: unused variable ‘entry_counter’
Source/plugin-list.cpp:316: warning: unused variable ‘loopentry’
g++ -c -o plugin-ui.o -Wall -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/nspr -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string   -I/usr/include/firefox -g -O2      -g -O2  -Iinclude -fPIC  -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  Source/plugin-ui.cpp
Source/plugin-ui.cpp:6:21: error: X11/xpm.h: No such file or directory
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:57: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor

```
There seems to be alot of "has virtual functions but non-virtual destructor", I have no idea what this means, so any help would be greatly appreciated.

---

### Post by macaholic on 2008-01-27
Got it to work after messing around a bit, apparently i needed the "libxpm-dev" package installed.

---

