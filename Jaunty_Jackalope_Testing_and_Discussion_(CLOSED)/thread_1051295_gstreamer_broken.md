---
title: "gstreamer broken?"
date: 2009-01-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-26
Is it just me, or is gstreamer segfaulting and sigseving on fresh Jaunty installs?

---

### Post by gwenn on 2009-01-26
+1

---

### Post by Gina on 2009-01-26
Working fine for me in AMD64 - playing a .wma file ATM.

---

### Post by Nullack on 2009-01-28
Details are needed for any sensible investigation

---

### Post by Starks on 2009-01-28
I'd gladly give more info if I knew how to use gdb.

---

### Post by Starks on 2009-01-28
Just did a trace. libavcodec52-unstripped is the culprit. libavcodec52 is needed instead.

---

### Post by bruce89 on 2009-01-28
> **Starks said:**
> Just did a trace. libavcodec52-unstripped is the culprit. libavcodec52 is needed instead.

Please [file a bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+filebug").

---

### Post by Starks on 2009-01-28
Aye.

[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/322570](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/322570)

---

### Post by bruce89 on 2009-01-28
> **Starks said:**
> Aye.

[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/322570](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/322570)

Thanks, I feel lazy now.

---

### Post by gwenn on 2009-02-01
Thanks for the codec Starks.Totem gets me crazy,but now I have a brand new fresh install of jaunty 100% functionall.

---

