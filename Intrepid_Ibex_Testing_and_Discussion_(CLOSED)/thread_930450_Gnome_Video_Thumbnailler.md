---
title: "Gnome Video Thumbnailler"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-26
Im having problems with the synatx of gnome video thumbnailer. When I try:

gnome-video-thumbnailer -s 128 file:///mnt/vault/Film/Tests/IMAG0002.ASF 

I get no thumbnail - instead it present a help type output in terminal.

Im trying to retest this bug I reported:

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/263153](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/263153)

Anyone can try this out too by downloading the footage attached to the report.

---

### Post by marmuta on 2008-09-26
this should work:
gnome-video-thumbnailer -s 128 file:///mnt/vault/Film/Tests/IMAG0002.ASF IMAG0002_ASF_thumb.png

The thumbnail gets created but only the upper 20 lines or so seem right.

---

### Post by Nullack on 2008-09-26
Thanks mate

---

