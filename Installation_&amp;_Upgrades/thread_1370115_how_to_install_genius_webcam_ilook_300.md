---
title: "how to install genius webcam ilook 300 ?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by gabak on 2010-01-01
hi
i have this webcam and CHEESE say it have nt found a webcam of course SKYPE either so none of them can see it.
i have read a lot of forums but nobody has an answer.

this is what lsusb say:
Bus 005 Device 002: ID 093a:2628 Pixart Imaging, Inc. 

Also i have read a while ago that there is a kind of emulator for windows like it can install driver that are made for windows into linux but i dont trust that.
is there an easy way to make it work?

---

### Post by cile87 on 2010-08-31
I have the same problem. I tried downloading & compiling v4l and it still didn't work. I basicly followed this procedure:
[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

but it still didn't work for me.

---

### Post by Stemp on 2011-01-10
The 093a:2628 webcams use the gspca pac7311 driver, and should work OOTB.
If not, try to compile the gspca snapshot.
[Gspca Snapshot]("http://stemp.wordpress.com/2010/05/17/gspca-snapshot/") is in French, but shouldn't be difficult to understand :)

---

