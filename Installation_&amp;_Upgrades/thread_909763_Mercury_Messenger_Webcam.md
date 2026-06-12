---
title: "Mercury Messenger Webcam"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Pen3356 on 2008-09-03
My webcam is not working on Mercury.  I tried to do a lot of things that I read on other threads but I did not know where to copy and paste certain things.

This is what the Global Settings show me:

Copy libjmutil.so: Failed

How do I fix that? HELP PLEASE

---

### Post by Sef on 2008-09-03
What version of Ubuntu are you using?

---

### Post by Pen3356 on 2008-09-03
It is 8.04

---

### Post by Sef on 2008-09-04
I found the same question and an answer [here]("http://ubuntuforums.org/showthread.php?p=5644072").  The answer is in Spanish, but mostly it's command line.

I translated it via my knowledge of Spanish and babelfish.

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

