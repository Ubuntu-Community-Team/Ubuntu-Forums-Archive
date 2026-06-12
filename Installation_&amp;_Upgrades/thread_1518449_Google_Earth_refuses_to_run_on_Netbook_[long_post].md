---
title: "Google Earth refuses to run on Netbook [long post]"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by eltonw on 2010-06-26
I downloaded and installed **Google Earth 5**, on my Asus EEE 1000 PC. However, it fails to launch, since it *insists* on running in 1024 x 768 mode. [COLOR="DarkRed"]The netbook only goes up to 1024 x 600[/COLOR]. 

Previously, one could safely ignore this warning and still run the application in Karmic Kola.

However, it is quite clear that **[COLOR="Olive"][SIZE="2"]it will *NOT* run in Lucid Lynx[/SIZE][/COLOR]**.

"Fatal error in __driConfigOptions line 1, column 0: unknown encoding.
Google Earth has caught signal 6.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

 .googleearth/crashlogs/crashlog-4c264c75.txt"

=================================================================
Major Version 5
Minor Version 2
Build Number 0001
Build Date Jun 10 2010
Build Time 16:15:55
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 34
OS Patch Version 0
Crash Signal 6
Crash Time 1277578357
Up Time 28.0614

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd030b)[0xb77a330b]
[0xb77fc400]
/lib/tls/i686/cmov/libc.so.6(abort+0x182)[0xb5ad0a82]
/usr/lib/dri/i915_dri.so(+0x237bf)[0xac8427bf]
/usr/lib/dri/i915_dri.so(+0x50802)[0xac86f802]
/usr/lib/dri/i915_dri.so(+0x21ab9)[0xac840ab9]
/usr/lib/mesa/libGL.so.1(+0x3d939)[0xb4e42939]
/usr/lib/mesa/libGL.so.1(+0x1a18b)[0xb4e1f18b]
/usr/lib/mesa/libGL.so.1(+0x1576a)[0xb4e1a76a]
/usr/lib/mesa/libGL.so.1(glXChooseVisual+0x36)[0xb4e1b566]
./librender.so(+0x4d673)[0xb50a0673]
./librender.so(_ZN12RenderWidget4initEv+0x116)[0xb50a1056]
./librender.so(_ZN12RenderWidgetC1EP7QWidgetPKc6QFlagsIN2Qt10WindowTypeEE+0x16c)[0xb50a1eac]
./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x82)[0xb5084432]
./libgoogleearth_free.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x94)[0xb77802d4]
./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0xabb)[0xb6c497ef]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0xb6bf9e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x16f)[0xb6c038a3]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0xb747bd50]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0xcc)[0xb6c4c55c]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x74)[0xb6c4c264]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1f2)[0xb6c4c482]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1d9)[0xb6c4c469]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x74)[0xb6c4c264]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1f2)[0xb6c4c482]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1d9)[0xb6c4c469]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x74)[0xb6c4c264]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1f2)[0xb6c4c482]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1d9)[0xb6c4c469]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1d9)[0xb6c4c469]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x1d9)[0xb6c4c469]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x45)[0xb6c4c4d5]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x33b)[0xb6c4ca97]
./libQtGui.so.4(_ZN7QWidget10showNormalEv+0x4a)[0xb6c3ce9e]
./libgoogleearth_free.so(_ZN10MainWindow18readScreensizeInfoEv+0xc35)[0xb7768225]
./libgoogleearth_free.so(_ZN5earth6client11Application12SetupMainWinENS0_3Kvw7ProductEb+0x29e)[0xb77a761e]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x42f)[0xb77ae47f]
./libgoogleearth_free.so(earthmain+0x27d)[0xb77a273d]
./googleearth-bin(_init+0x122)[0x80486c2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb5ab9bd6]
./googleearth-bin(_init+0x91)[0x8048631]

=================================================================

---

### Post by barrieluv on 2010-06-27
As you don't appear to be asking for help, I would like to state that Google Earth 5.1.3533.1731-0medibuntu1 works fine for me on my 1005HA's Lucid install.  The message regarding my resolution pops up and I can choose to ignore it.

---

### Post by catanzag on 2010-08-05
Hi,

I had the same error on my Aspire One D250 netbook with Lucid 10.04 and with google earth 5.2.1.1329 (beta) installed with make-googleearth-package from testing repository; I solved it following the suggestion found [here]("http://www.google.com/support/forum/p/earth/thread?tid=467f457376d88888&hl=en") and reported below, it is not a problem of screen resolution: assuming you installed it under /opt/google-earth/


```
cd /opt/google-earth/
wget http://librarian.launchpad.net/7037027/libGL.so.1 -O libGL.so.1
```

Hope this can help you

BR

catanzag

---

### Post by xcurtisx on 2010-08-26
This didn't work for me. The lib file referenced seems to no long exist?

---

