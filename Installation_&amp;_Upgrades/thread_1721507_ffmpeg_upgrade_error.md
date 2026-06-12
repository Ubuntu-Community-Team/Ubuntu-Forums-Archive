---
title: "ffmpeg upgrade error?"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by Legendman3 on 2011-04-04
Today i opened upgrade manager and found some updates grayed out. I could not click them so i went to synaptic to try and install them and got this error:

```
ffmpeg:
 Depends: libavcodec52 but it is not going to be installed or
     libavcodec-extra-52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
  Depends: libavdevice52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavdevice-extra-52 but it is not going to be installed
  Depends: libavfilter0 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavfilter-extra-0 but it is not going to be installed
  Depends: libavformat52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavformat-extra-52 but it is not going to be installed
 Depends: libavutil49 but it is not going to be installed or
     libavutil-extra-49 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
  Depends: libpostproc51 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
     libpostproc-extra-51 but it is not going to be installed
  Depends: libswscale0 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
     libswscale-extra-0 but it is not going to be installed
```I am running ubuntu 10.04. Any idea whats going on?

---

### Post by technokoopa on 2011-04-04
The dependency problem is the fact that not all components of ffmpeg are upgraded yet, such as libavcodec-extra-52, libavcodec-unstripped-52, libswscale-extra-0, and libavutil-extra-49 which are found in the medibuntu repository. These were installed due to video editting software installed. These components have not been upgraded yet and until they do, ffmpeg cannot be upgraded. You have to be patient.

---

### Post by Legendman3 on 2011-04-04
ooooooooooooooooo... Ok i get it. Thanks!

---

### Post by cottfcfan on 2011-04-05
Glad I found this thread.
Am having the same problems.

---

### Post by themisanthrope on 2011-04-05
Glad I found this thread too. Saved a lot of potentially wasted time attempting to fix what wasn't broke. Still, more user friendly messages from the Package Manager would have saved even hunting for this thread.

---

### Post by Yleeyas on 2011-04-05
Thanx for the heads-up technokoopa. So this will resolve itself when the dependencies catch up I guess :)

---

