---
title: "Opera10 sound but no picture in e.g. youtube"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-07-01
Hi

The title pretty much states the problem (Firefox works fine). When I run opera from a terminal I get 

[COLOR="Blue"](npviewer.bin:26046): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
[/COLOR]


[COLOR="#0000ff"](npviewer.bin:26046): Gdk-WARNING **: GdkWindow 0x4600256 unexpectedly destroyed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 8445 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/COLOR]
when I try to play a video

This is what I get at the same point from Firefox

*** NSPlugin Viewer  *** WARNING: grmpf, despite much effort, I could not determine the actual plugin area size...


Any clues?

---

### Post by MacUntu on 2009-07-01
Opera 10.00 Beta 2 Build 4458 ([http://snapshot.opera.com/unix/snapshot-4458/intel-linux/opera_10.00.4458.gcc4.qt3_i386.deb](http://snapshot.opera.com/unix/snapshot-4458/intel-linux/opera_10.00.4458.gcc4.qt3_i386.deb)) works fine.

---

### Post by ronacc on 2009-07-01
can you reference a specific video ? opera 10(64bit) + 64bit flash plays youtube videos ok for me , sound and picture .

---

### Post by ubername on 2009-07-01
All videos show this behaviour as far as I can tell (I haven't found one which works.)

Running 64bit ubuntu,

This from opera:about 

Version
10.00 Beta 2
Build
4458
Platform
Linux
System
x86_64, 2.6.30-10-generic
Qt library
3.3.8b
Java
Java Runtime Environment installed

---

### Post by ronacc on 2009-07-01
see here and get the 64bit flash  .  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   . just unzip and put libflashplayer.so in your opera plugins dir , you can also put it in your mozilla plugins dir .

---

### Post by ubername on 2009-07-01
> **ronacc said:**
> see here and get the 64bit flash  .  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)   . just unzip and put libflashplayer.so in your opera plugins dir , you can also put it in your mozilla plugins dir .

Thanks, sorted

---

