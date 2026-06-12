---
title: "Live cd blank screen"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by fishwebby on 2008-05-13
Hi,

I'm trying to run the 8.04 live CD on my laptop, but it doesn't display anything other than the splash screen, then goes blank.

I've tried all things suggested on these pages...

[http://www.cybertechhelp.com/forums/showthread.php?t=175033](http://www.cybertechhelp.com/forums/showthread.php?t=175033)
[http://ubuntuforums.org/showthread.php?t=580020](http://ubuntuforums.org/showthread.php?t=580020)
[https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

... from restarting X and editing conf files, but the most I managed to achieve was hearing the startup sound. The screen does flicker for a bit but then it seems to go to sleep.

My laptop specs are
Pentium 4 2.66GHz
504Mb RAM
Video Adapter: Intel 82845G/GL/GV Graphics Controller, 64Mb
1024x768 screen

I know there's Wubi now but I'd still rather see how Ubuntu runs on my machine before changing anything.

Anyone have any ideas? It does seem like a display problem, but I'm not sure.

Any help is greatly appreciated!

Cheers
Dave

---

### Post by housam on 2008-05-13
Did you got the live cd from ubuntu shipit or just downloaded and burnt it ? if so, please make the [[COLOR="Red"]_MD5Sum_[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") check and if ok burn the disc at slow speed as 2x - 4x .

---

### Post by fishwebby on 2008-05-15
Hi housam,

thanks for your reply. I tried what you suggested, even doing the integrity check on the CD when I booted from it, and the CD would seem to be ok. Alas it still doesn't load. I get the "Knight Rider-esque" progress bar, then the screen goes blank, and after a while the CD stops and the computer seems to go to sleep.

I'm thinking maybe it must be something to do with the video card?

Any ideas?

Many thanks
Dave

---

### Post by Pumalite on 2008-05-15
md5sum:
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
Is different than CD integrity check.

---

### Post by wpshooter on 2008-05-15
Have you tried booting in safe graphics mode ?

---

### Post by fishwebby on 2008-05-15
Hi

I did the CD integrity check in addition to the MD5sum just in case there was a problem after burning, but it was ok.

Just tried it in safe graphics mode and still the same I'm afraid.

I did hear the Ubuntu login sound though, but still nothing on screen.

---

### Post by housam on 2008-05-15
Either you try another Distros like 7.10  or the 8.04 alternate CD or you try yours on somebody else computer.

---

### Post by fishwebby on 2008-05-20
Hello

thanks for your reply - I gave up with Ubuntu 8.04 and now I've gone with Xubuntu 6.06 (the later versions wouldn't work either) and it's all installed and running nicely. All I need to do now is configure it to get it to recognise my network card, but that's another post! :-)

Cheers
Dave

---

