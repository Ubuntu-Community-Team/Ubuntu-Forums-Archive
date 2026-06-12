---
title: "No video when attempting to boot"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by Steve215 on 2007-05-04
I've installed Ubuntu Feisty 7.04 64bit and I can't boot it up normally. When I select it in grub it says "Loading.. please wait" for a split second and then my monitor says "No Video" and turns off shortly after. I've got an X800 pro video card so I followed the tutorial located at [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) to get Ubuntu installed yet still can't get it to boot. The weird thing is if I enter the recovery console and then type "gdm" Ubuntu boots up fine. Anyone else experience this and know of a fix? Here's my specs:

AMD 3400+ (2.4GHZ)
1GB DDR Ram
ATI X800 Pro video card
250GB HDD with Windows XP
80GB IDE HDD with Ubuntu 7.04 installed with Grub setup to dual boot

---

### Post by taurus on 2007-05-04
You can try the alternate CD to install Feisty on your AMD64.

---

### Post by Steve215 on 2007-05-04
> **taurus said:**
> You can try the alternate CD to install Feisty on your AMD64.

Ahh yeah thats what I tried. I did the text install and then installed the fglrx drivers and get no video.  It's really weird how if I go into the recovery mode and load GDM that way it boots fine.

---

### Post by taurus on 2007-05-04
Have a look at this link, [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194).  Maybe it helps.

---

### Post by Steve215 on 2007-05-05
> **taurus said:**
> Have a look at this link, [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194).  Maybe it helps.

Unfortunately those were the instructions I followed with no success. :( After doing numerous google and forum searches it looks like this is a bug with all ATI X**** video cards and those instructions only work for some. Looks like I'll have to wait it out until another fix comes around. It's still really weird how I can get into the desktop if I type "gdm" at the command line.

---

### Post by LucienJ on 2007-05-05
Take a look at post [http://ubuntuforums.org/showthread.php?t=419351](http://ubuntuforums.org/showthread.php?t=419351).
It looks like the same problem and contains a fix...

Good luck

---

### Post by Steve215 on 2007-05-05
> **LucienJ said:**
> Take a look at post [http://ubuntuforums.org/showthread.php?t=419351](http://ubuntuforums.org/showthread.php?t=419351).
It looks like the same problem and contains a fix...

Good luck

Thank you for the link! Although the fix didn't worked someone mentioned in that thread that that removing the quiet and splash options in grub might work. I edited menu.lst and sure enough Linux boots fine with both options removed. I then determined it was the "splash" option in particular causing the problems. I can live without a splash before linux boots up. Anyhow, thanks again! :)

---

### Post by Gus_T_Reer on 2007-05-05
I have exactly the same problem using an x850xt card I came up with the same resolution - remove the splash option. However, on my system I have to remove the quiet option (on the kernel line) as well otherwise it won't boot. I can also boot using init 5 from the recover option unless I specify a vga=???? and then even the recover option doesn't work. It's all very strange.

I'd be interested to know if anyone with this problem can shutdown/logout/restart tidily because on my system the screen just goes off and that's it.

---

### Post by Steve215 on 2007-05-05
> **Gus_T_Reer said:**
> I have exactly the same problem using an x850xt card I came up with the same resolution - remove the splash option. However, on my system I have to remove the quiet option (on the kernel line) as well otherwise it won't boot. I can also boot using init 5 from the recover option unless I specify a vga=???? and then even the recover option doesn't work. It's all very strange.

I'd be interested to know if anyone with this problem can shutdown/logout/restart tidily because on my system the screen just goes off and that's it.

Check out [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666)

Apparently a lot of other people are experiencing this same bug. For me added "vga=792" now fixed it. I can now have "quiet" and "splash" on and everything works fine. Very strange how this bug seems to affect everyone differently.

---

