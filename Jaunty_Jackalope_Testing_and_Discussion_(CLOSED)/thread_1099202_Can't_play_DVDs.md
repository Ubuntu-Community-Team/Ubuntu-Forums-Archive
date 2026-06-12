---
title: "Can't play DVDs"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-03-17
I have just tried to play a DVD for the first time on one of my 4 different jaunty boxes and I cannot.  I have ubuntu restricted exras installed and also manually ran the '/usr/share/doc/libdvdread4/install-css.sh' and neither meathod works.

VLS command line outputs:
```

[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Xlib:  extension "RANDR" missing on display ":0.0".
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SHOOTER_AC_169
libdvdnav: DVD Serial Number: 36A78A82
libdvdnav: DVD Title (Alternative): SHOOTER_AC_169
libdvdnav: Unable to find map file '/home/lordveovis/.dvdnav/SHOOTER_AC_169.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000140
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000592
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000615
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000062e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002d2d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0002145b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000214df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000bb268
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000c8094
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003a1533
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.1.3/src/ifo_read.c:1704 ***
```

---

### Post by Nullack on 2009-03-18
resindvd is the free gstreamer dvd navigation library which is in the bad gstreamer plugins set. Its not robust and not feature complete. Development is occuring at a glacial pace.

IMHO your better off builder mplayer through the guide in this forum from svn, which brings in the latest ffmpeg libraries as well, and running a good front end like smplayer.

---

