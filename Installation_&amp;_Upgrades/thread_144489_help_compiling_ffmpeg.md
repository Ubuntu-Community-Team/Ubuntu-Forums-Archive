---
title: "help compiling ffmpeg"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by IGNIZ on 2006-03-14
hi, i'm triyng to compile ffmpeg 0.4.9-pre1 but i get this error:

```
common.h:67: error: array type has incomplete element type
common.h:71: error: array type has incomplete element type
make[1]: *** [common.o] Error 1
```

i read on this forum that someone had a similar problem and he solved compiling a cvs, now, the cvs download from ffmpeg site is down so:

is there a method to compile the version i have?
someone has a cvs version higher than 0.4.9?&#12288;(i need 0.4.9 at least)
is there some repository with cvs or 0.4.9-pre1?

---

### Post by linear on 2006-03-14
A version labeled "3:0.cvs20050918-4ubuntu1" is in the Breezy universe repository.

---

### Post by IGNIZ on 2006-03-14
unfortunately it's old, i need a newer one to compile another program

---

### Post by linear on 2006-03-15
0.4.9 is older still, the people who maintain ffmpeg don't believe in releases.
 
Are you sure the cvs repository is down? It appeared to be browseable today.

---

### Post by IGNIZ on 2006-03-15
[quote=linear]0.4.9 is older still, the people who maintain ffmpeg don't believe in releases.
 
Are you sure the cvs repository is down? It appeared to be browseable today.[/quote]

[http://ffmpeg.sourceforge.net/download.php](http://ffmpeg.sourceforge.net/download.php)

i saw here, where can i get the cvs? i can't find one

---

### Post by linear on 2006-03-16
These instructions are what I had in mind:
>  
FFmpeg CVS
Note that the FFmpeg CVS repository is hosted by the MPlayer project, rather than by Sourceforge, for... historical reasons. In order to use the standard CVS client to check out the source code: 
 
cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg

 
Also browseable at this link:
 
[http://www1.mplayerhq.hu/cgi-bin/cvsweb.cgi/?cvsroot=FFMpeg]("http://www1.mplayerhq.hu/cgi-bin/cvsweb.cgi/?cvsroot=FFMpeg")

---

### Post by IGNIZ on 2006-03-16
[quote=linear]These instructions are what I had in mind:

 
Also browseable at this link:
 
[http://www1.mplayerhq.hu/cgi-bin/cvsweb.cgi/?cvsroot=FFMpeg]("http://www1.mplayerhq.hu/cgi-bin/cvsweb.cgi/?cvsroot=FFMpeg")[/quote]

ok it works but now i found out that i need version 0.4.9-pre1 that gives me that odd error, some tip to compile that specific version

---

### Post by linear on 2006-03-16
In that case:

[http://prdownloads.sourceforge.net/ffmpeg/ffmpeg-0.4.9-pre1.tar.gz?download](http://prdownloads.sourceforge.net/ffmpeg/ffmpeg-0.4.9-pre1.tar.gz?download)

---

### Post by IGNIZ on 2006-03-17
[quote=linear]In that case:

[http://prdownloads.sourceforge.net/ffmpeg/ffmpeg-0.4.9-pre1.tar.gz?download]("http://prdownloads.sourceforge.net/ffmpeg/ffmpeg-0.4.9-pre1.tar.gz?download")[/quote]

this version gives me the error i wrote on first post so i can't compile it...

---

### Post by linear on 2006-03-17
Sorry, didn't understand the problem. In an earlier post, you said you were trying to compile something else that required ffmpeg 0.4.9; can you change that dependency (if it's in the configure file)?

---

### Post by IGNIZ on 2006-03-18
i guess this is not so good to do, if the program require that version there must me a reason, so i just need someone who succesfully compiled version 0.4.9 of ffmpeg

---

