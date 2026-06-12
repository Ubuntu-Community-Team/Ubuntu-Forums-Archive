---
title: "Karmic Koala trouble"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2009-10-13
Ok, still Beta, I know, but it is weird no one else has these problems as far as I read:

upon installing Nvidia driver 185, I can't start gdm, it goes to cdm as root and the screen flickers real fast, allowing me to write only when its bright, but not dark (???), but again, it flickers real fast, so I can't log in and start x. 

second problem:

If I do not install the driver, and instead I perform system update in Synaptic (or it does it automatically in recovery in Grub), and after a long and hard download and installing, it then fails to load: I can't start ubuntu. It loads after Grub but then a black screen. when I press the power button I see the ubuntu logo and then it turns itself off.

---

### Post by lovinglinux on 2009-10-13
You shouldn't be using a beta release on a production environment, specially if you are not familiar with Linux.

There is a [bug related with the nvidia driver](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442), that started to show up after recent updates.

See [this thread](http://ubuntuforums.org/showthread.php?p=8087079#post8087079) for a solution.

BTW, you shouldn't be posting about Karmic on this forum. There is a [proper forum for issues regarding Karmic](http://ubuntuforums.org/forumdisplay.php?f=359).

---

### Post by TheNessus on 2009-10-13
ah, great. I installed the driver from cmd as is suggested, it works now. Thanks :)

didn't know about the karmic forum, sorry. 

And learning the hard way is the good way, IMHO.

---

### Post by lovinglinux on 2009-10-13
> **TheNessus said:**
> And learning the hard way is the good way, IMHO.

If you have nothing to loose, then yes.

---

### Post by lovinglinux on 2009-10-14
This bug has been fixed with the latest updates! =D>

---

