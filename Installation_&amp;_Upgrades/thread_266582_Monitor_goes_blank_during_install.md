---
title: "Monitor goes blank during install"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by ryboto on 2006-09-27
I've downloaded the latest 64bit version of ubuntu, and attempted an install.  All I get to see is the screen with the ububtu logo, and a list of drivers/things scrolling with "ok" across from them. I'm assuming everything loads, and thats when my monitor goes blank.  A few seconds later I hear a sound, that I'm assuming is like a startup sound, so I know somethings happening in the background, I just can't see it!  I'm a second time noob, it's been a while since I played with linux, and this being the distro for "humans" i just assumed I might have an easier time learning it all again.  So, keep that in mind if you have any suggestions for me! thanks!

---

### Post by wpshooter on 2006-09-27
Does you computer have any other O/S or anything on it you need to keep or are you trying to install **JUST** Ubuntu on the computer ???

---

### Post by ryboto on 2006-09-27
the drive wasn't blank, but, I was just going to have the ubuntu installer erase the disk.

---

### Post by wpshooter on 2006-09-27
Then do this.

Download the KILLDISK program from this site and WIPE the drive clean.
[http://www.killdisk.com/](http://www.killdisk.com/)

Then attempt to install from the DESKTOP CD but first make sure that you run the verification test on the Ubuntu CD from the initial boot screen menu.

If it passes that test, then proceed with the install once you get to the desktop.  If it will still not install after that then download, burn and attempt to install from the ALTERNATE CD.

Good luck.

---

### Post by ryboto on 2006-09-27
thanks for the reply.  I'll attempt using killdisk asap.  I am curious though, why would having data on the disk prevent the install from ocurring??  i've already had the install check the cd, i did that after the first attempt.

---

### Post by wpshooter on 2006-09-27
I can not tell you exactly why but my past experience is that these installs work MUCH better on a completely clean drive, i.e. no data, programs or partition info.  I think they still need to do a bit of work on some of their formatting and installation procedures.

Good luck.

---

### Post by ryboto on 2006-09-28
So, I downloaded the alternate disc and tried it.  The system installed without a hitch.  When I restarted after the install, instead of logging in the blasted monitor went blank.  I typed my username, hit tab, then password, hit enter, and low and behold, I hear the welcome sound, and see that my hard drives are being accessed.  So, it works, I just have no display.

---

### Post by ryboto on 2006-09-29
can anyone shed any light here?? I think it must be a display driver issue, but I have no idea what to do to fix it.

---

### Post by wpshooter on 2006-09-29
When you are using the AlTERNATE CD, when it gets to the prompt where it ask you about your choices for avaiable screen resolultions, are you possibly putting in a resolution higher than either your video card or your monitor can handle ???  If I use the ALTERNATE CD, I alway eliminate all of the choices on the prompt other than the one that I want to use, which is usually 1024 x 768.

Good luck.

---

### Post by ryboto on 2006-09-29
my monitor uses a resolution of 1680x1050, and I was surprised to see it as a resolution I could choose, but it was there, and that was the only resolution I selected.  Still, monitor goes blank.

---

### Post by wpshooter on 2006-09-29
> **ryboto said:**
> my monitor uses a resolution of 1680x1050, and I was surprised to see it as a resolution I could choose, but it was there, and that was the only resolution I selected.  Still, monitor goes blank.

Try choosing something lower, 1024 x 768 and see if that does not work.  If it does, then me things you probably have a BUG to report.

Good luck.

---

### Post by ryboto on 2006-10-01
using the desktop install disk, I've specified it to use 800x600, and 1024x768, and for both of them, the monitor goes blank.

---

