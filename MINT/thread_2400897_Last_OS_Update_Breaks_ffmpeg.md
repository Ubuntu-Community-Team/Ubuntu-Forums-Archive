---
title: "Last OS Update Breaks ffmpeg"
date: 2018-09-11
forum: MINT
---

### Post by stephen67 on 2018-09-11
I am using 18.0 and apply all updates.

I have been using ffmpeg for many years to convert file formats. I am now getting errors that have me confused. Here is the command line:

ffmpeg -i 101.Cat.avi  -c:v libx264 -c:a copy 101.Cat.mp4

I now get many errors:

libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error:  GLXBadContext
  Request Major code 155 (GLX)
  Request Minor code 6 ()
  Error Serial #55
  Current Serial #54

I Google the errors and everything seems to focus on bugs in Android Studio which I don't use.

So I am at a loss for how to fix this.

Any and all help appreciated.

---

### Post by ajgreeny on 2018-09-11
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by davidrobbe on 2018-11-29
Same issue here , did you found a way to fix it ?  It says below the thread has been moved but I can't fin it

---

