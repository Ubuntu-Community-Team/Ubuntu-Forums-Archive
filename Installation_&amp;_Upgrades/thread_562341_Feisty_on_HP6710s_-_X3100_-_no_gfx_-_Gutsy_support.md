---
title: "Feisty on HP6710s - X3100 - no gfx - Gutsy support?"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by czato on 2007-09-28
I installed 7.04 on my new lap (as second boot with Vista). 

Now of course my gfx does not work.
I found a link with solution, but it involves custom kernel, don't know how to do this:

wiki.ubuntu.com/LaptopTestingTeam/HP6710b

now, I am not sure whether I should wait for Gutsy (will it support X3100 and Santa Rosa?), or try to build custom kernel (difficult for me, newbie)? What do you think?

I found another solution - sudo aptitude install xserver-xorg-video-intel,
 but I don't have this driver on my installation...

Help appreciated - I would like to get away from Vista ASAP...

---

### Post by Pumalite on 2007-09-28
What graphics do you exactly have?

---

### Post by czato on 2007-09-28
My system spec:

CPU     Intel Core 2 Duo T5470 (1.6 GHz, 2MB cache, 800 MHz FSB) Intel Centrino Duo
GFX	Intel GMA X3100

---

### Post by Pumalite on 2007-09-28
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+b](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+b)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129130](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129130)

[http://lwn.net/Articles/244582/](http://lwn.net/Articles/244582/)

[http://www.phoronix.com/forums/showthread.php?p=12122](http://www.phoronix.com/forums/showthread.php?p=12122)

[http://www.phoronix.com/forums/showthread.php?p=11908](http://www.phoronix.com/forums/showthread.php?p=11908)

[http://ubuntuforums.org/archive/index.php/f-135-p-117.html](http://ubuntuforums.org/archive/index.php/f-135-p-117.html)

[http://ubuntuforums.org/forumdisplay.php?f=135&page=261&order=desc](http://ubuntuforums.org/forumdisplay.php?f=135&page=261&order=desc)

---

