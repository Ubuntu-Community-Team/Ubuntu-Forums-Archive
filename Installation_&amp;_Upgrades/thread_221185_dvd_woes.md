---
title: "dvd woes"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by Jjohn on 2006-07-22
Hi All,
      I am reposting this from the amd64 board.
Acer 500x laptop

VLC seems to be reading dvd files as text. This causes the disc to spin endlessly with no out put. I graphically installed vlc and ALL the plug-ins including libdvdcss but still no output.
totem xine reports that I may need libdvdcss. Can any one help please.
Regards John..

Edit/Delete Message

---

### Post by gerbman on 2006-07-22
What is the exact error output of totem/xine? Have you run the install script for libdvdcss? You can do this by:```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by Jagot on 2006-07-23
[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by Jjohn on 2006-07-23
Hi Gerbman.
          Yes I think I do have the libdvdreadcss I reinstalled it. Seemed like a lot of similar output as it was making..
Here are some of the error msgs I get:
Errors from Xine engine and vlc

Couldn't display "/media/cdrom0/video_ts/video_ts.bup".

Couldn't open "video_ts.vob
The filename "video_ts.vob" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


Error message from totem-xine
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?



Totem could not play 'file:///media/cdrom0/video_ts/vts_01_0.vob'. the movie could not be read



Cannot open vts_01_1.vob](*,)

---

### Post by Jjohn on 2006-07-23
Jagot, 
      Thanks the server is overloaded at the time I tried. Will go back later  for a read.
Thank you

---

### Post by Jjohn on 2006-07-23
Jagot 
     this is the document I am working from and getting too much hassle.
I did the amd64 option but am unsure of if it was a success.
Is it possible to probe libreaddvdcss2 to see if it is working/installed??:confused:

---

