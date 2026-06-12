---
title: "konqueror, nsplugin, flash, hulu.com"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-04-10
Konqueror seems to have problems playing video from hulu.com. I have the 64bit flash plugin installed and konqueror sees it. Videos on youtube work and the flash works on the hulu.com home page. But when I try to watch a video nothing pops up. I tried killing nspuginviewer while firefox was running and then went to hulu and got the same problem... thus leads me to believe that the problem lies in the nsplugins.

Here is the out put from running konqueror in the terminal and trying to watch a hulu video: ```
DOW (window)' failed
nspluginviewer(24768) NSPluginInstance::NPSetWindow: results in  0
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  4
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x31cc7c0 , url= "http://www.hulu.com/vc.swf" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "ALLOWSCRIPTACCESS", "WMODE", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/vc.swf", "1", "1", "undefined", "vcs", "vcs", "high", "always", "transparent", "http://www.hulu.com/") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x31cc080
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://www.hulu.com/masthead.swf"
konqueror(24760) NSPluginInstance::pluginResized: 920 377
konqueror(24760) NSPluginInstance::resizeEvent: 920 377 true true true
nspluginviewer(24768) NSPluginInstance::resizePlugin: 922 920 377 377 true
nspluginviewer(24768) PluginHostXEmbed::resizePlugin: 104857745 83889848 920 377

(<unknown>:24768): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
nspluginviewer(24768) NSPluginInstance::NPSetWindow: results in  0
nspluginviewer(24768) NSPluginInstance::resizePlugin: 920 920 377 377 true
konqueror(24760) NSPluginInstance::pluginResized: 1 1
konqueror(24760) NSPluginInstance::resizeEvent: 1 1 false true false
konqueror(24760) NSPluginInstance::showEvent: 1 1 true true false
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  5
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://www.hulu.com/masthead.swf"
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 12 (X_ConfigureWindow)
  Resource id:  0x6400091
nspluginviewer(24768) PluginHostXEmbed::setupWindow: 83890044 1 1

(<unknown>:24768): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
nspluginviewer(24768) NSPluginInstance::NPSetWindow: results in  0

(<unknown>:24768): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:24768): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWindow'

(<unknown>:24768): Gtk-CRITICAL **: gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:24768): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(<unknown>:24768): Gtk-CRITICAL **: gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:24768): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://www.hulu.com/vc.swf"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://www.hulu.com/vc.swf"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  6
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x3aa4840 , url= "http://www.hulu.com/guid.swf" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "ALLOWSCRIPTACCESS", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/guid.swf", "1", "1", "undefined", "pguid", "pguid", "high", "always", "http://www.hulu.com/") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x2dc7480
konqueror(24760) NSPluginInstance::pluginResized: 1 1
konqueror(24760) NSPluginInstance::resizeEvent: 1 1 false true false
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://www.hulu.com/home/featured"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://www.hulu.com/home/featured"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://assets.hulu.com/mastheads/logo_art_parks_and_recreation.png"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://assets.hulu.com/mastheads/logo_art_parks_and_recreation.png"
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://assets.hulu.com/mastheads/masthead_art_parks_pilot.jpg"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://assets.hulu.com/mastheads/masthead_art_parks_pilot.jpg"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://assets.hulu.com/episodes/background_art_grey.jpg"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://assets.hulu.com/episodes/background_art_grey.jpg"
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://t2.hulu.com/crossdomain.xml"
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://t.hulu.com/crossdomain.xml"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://t2.hulu.com/crossdomain.xml"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://t.hulu.com/crossdomain.xml"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://t.hulu.com/beacon/v2/siteinteraction?event=mastheadload&value=0&param=home&dict=target%3Ahttp%253A//www.hulu.com/watch/67259%3Bcomputer%3A6FBA275B6B7E4FB49F261B8CF7027542&cb=0.11951991124078631"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://t.hulu.com/beacon/v2/siteinteraction?event=mastheadload&value=0&param=home&dict=target%3Ahttp%253A//www.hulu.com/watch/67259%3Bcomputer%3A6FBA275B6B7E4FB49F261B8CF7027542&cb=0.11951991124078631"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://t2.hulu.com/v3/siteinteraction/mastheadload?value=0&param=home&target=http%3A//www.hulu.com/watch/67259&computerguid=6FBA275B6B7E4FB49F261B8CF7027542&cb=0.3151894239708781"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://t2.hulu.com/v3/siteinteraction/mastheadload?value=0&param=home&target=http%3A//www.hulu.com/watch/67259&computerguid=6FBA275B6B7E4FB49F261B8CF7027542&cb=0.3151894239708781"
konqueror(24760) NSPluginInstance::~NSPluginInstance: -> NSPluginInstance::~NSPluginInstance
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) NSPluginInstance::~NSPluginInstance: release
konqueror(24760) NSPluginLoader::release: NSPluginLoader::release ->  5
konqueror(24760) NSPluginInstance::~NSPluginInstance: <- NSPluginInstance::~NSPluginInstance
konqueror(24760) NSPluginInstance::~NSPluginInstance: -> NSPluginInstance::~NSPluginInstance
konqueror(24760) NSPluginInstance::~NSPluginInstance: release
konqueror(24760) NSPluginLoader::release: NSPluginLoader::release ->  4
konqueror(24760) NSPluginInstance::~NSPluginInstance: <- NSPluginInstance::~NSPluginInstance
konqueror(24760) NSPluginInstance::~NSPluginInstance: -> NSPluginInstance::~NSPluginInstance
konqueror(24760) NSPluginInstance::~NSPluginInstance: release
konqueror(24760) NSPluginInstance::~NSPluginInstance: <- NSPluginInstance::~NSPluginInstance
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(24760) NSPluginLoader::release: NSPluginLoader::release ->  3
konqueror(24760) NSPluginLoader::release: NSPluginLoader::release ->  2
konqueror(24760) NSPluginLoader::release: NSPluginLoader::release ->  1
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  2
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x341a010 , url= "http://www.hulu.com/loadplayer.swf?cb=2009-4-11-3" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "ALLOWSCRIPTACCESS", "BGCOLOR", "FLASHVARS", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/loadplayer.swf?cb=2009-4-11-3", "1", "1", "undefined", "load", "load", "high", "sameDomain", "#000000", "content_id=a7246fa64dc09d503547b55587a526db", "http://www.hulu.com/watch/67342/the-three-stooges-collection-brideless-groom") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x3609a20
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  3
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x2fa5610 , url= "http://www.hulu.com/copytoclipboard.swf" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "ALLOWSCRIPTACCESS", "FLASHVARS", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/copytoclipboard.swf", "134", "20", "undefined", "copytoclipboard", "copytoclipboard", "high", "always", "callback=getWidgetCode", "http://www.hulu.com/watch/67342/the-three-stooges-collection-brideless-groom") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x31fb7d0
konqueror(24760) NSPluginInstance::pluginResized: 1 1
konqueror(24760) NSPluginInstance::resizeEvent: 1 1 false true false
konqueror(24760) NSPluginInstance::resizeEvent: 100 30 false false false
konqueror(24760) NSPluginInstance::showEvent: 1 1 true true false
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  4
nspluginviewer(24768) PluginHostXEmbed::setupWindow: 83896162 1 1

(<unknown>:24768): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
nspluginviewer(24768) NSPluginInstance::NPSetWindow: results in  0
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  5
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x3bf7930 , url= "http://www.hulu.com/vc.swf" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "ALLOWSCRIPTACCESS", "WMODE", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/vc.swf", "1", "1", "undefined", "vcs", "vcs", "high", "always", "transparent", "http://www.hulu.com/watch/67342/the-three-stooges-collection-brideless-groom") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x3c27170
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://www.hulu.com/loadplayer.swf?cb=2009-4-11-3"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://www.hulu.com/loadplayer.swf?cb=2009-4-11-3"
konqueror(24760) NSPluginInstance::pluginResized: 1 1
konqueror(24760) NSPluginInstance::resizeEvent: 1 1 false true false
konqueror(24760) NSPluginInstance::showEvent: 1 1 true true false
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  6
nspluginviewer(24768) PluginHostXEmbed::setupWindow: 83896818 1 1

(<unknown>:24768): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
nspluginviewer(24768) NSPluginInstance::NPSetWindow: results in  0
nspluginviewer(24768) NSPluginInstance::timer: getting  "http://www.hulu.com/vc.swf"
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  "Requesting http://www.hulu.com/vc.swf"
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPNewStream: results in  0
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
nspluginviewer(24768) NSPluginInstance::NPDestroyStream: results in  0
konqueror(24760) PluginPart::statusMessage: PluginPart::statusMessage  ""
konqueror(24760) NSPluginLoader::instance: NSPluginLoader::instance ->  7
konqueror(24760) NSPluginLoader::newInstance: -> NSPluginLoader::NewInstance( parent= 0x30c7710 , url= "http://www.hulu.com/FNQBVXR" , mime= "application/x-shockwave-flash" ,  ("TYPE", "SRC", "WIDTH", "HEIGHT", "STYLE", "ID", "NAME", "QUALITY", "__KHTML__PLUGINBASEURL") ("application/x-shockwave-flash", "/FNQBVXR", "790", "368", "undefined", "pl", "pl", "high", "http://www.hulu.com/watch/67342/the-three-stooges-collection-brideless-groom") )
konqueror(24760) NSPluginLoader::newInstance: -> ownID ":1.696"  viewer ID: "org.kde.nspluginviewer-24760"
konqueror(24760) NSPluginLoader::lookup: Looking up plugin for mimetype  "application/x-shockwave-flash" :  "/usr/lib/mozilla/libflashplayer.so"
nspluginviewer(24768) NSPluginInstance::NPGetValue: results in  0
konqueror(24760) NSPluginLoader::newInstance: <- NSPluginLoader::NewInstance =  0x30c47c0
konqueror(24760) NSPluginInstance::pluginResized: 790 368
konqueror(24760) NSPluginInstance::resizeEvent: 790 368 false true false

```

---

### Post by kurros on 2009-04-11
Why are you using nspluginviewer if you have the 64-bit flash plugin?

---

### Post by taavikko on 2009-04-11
> **kurros said:**
> Why are you using nspluginviewer if you have the 64-bit flash plugin?

It's konquerors way to use netscape plugins.

I couldn't test hulu since they require registration and videos are available only in the US. 

Off course could have used proxy and such, but too much hassle :D

---

