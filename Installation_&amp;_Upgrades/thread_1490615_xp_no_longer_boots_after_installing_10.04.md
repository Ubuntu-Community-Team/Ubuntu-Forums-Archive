---
title: "xp no longer boots after installing 10.04"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by skatona on 2010-05-22
very new to linux ....  so hopefully I can explain this well.

I'm on a laptop. primary drive has 320gb XP installed. Ultrabay/secondary drive has 100gb lucid installed.

I installed lucid from booting with a flash memory stick to the secondary drive, while the XP drive was still in the primary location.

When booting the secondary drive with lucid, it comes up fine and seems to work great.

When trying to boot from the primary drive with XP on it, I get the following error and needless to say, the XP drive no longer boots.

error: no such device: xxxxx-xxx-xxxx-xxxx-xxxx (I left the numbers out here)
grub rescue>

I really need the primary drive with XP to boot again as it is my work drive.  Any ideas??

btw, if you ask me for info on my linux drive to show, please include instructions how to do so as like I said ... very new to linux.

Thanks - Steve

---

### Post by darkod on 2010-05-22
It seems you are hit by this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Because you can boot into ubuntu, you don't need the instructions in step 1.

If you want to investigate whether the UUID of the XP partition is wrong in grub.cfg (that's the long number), do steps 2 and 3.

If not really interested to investigate, just do step 4 and it should get you going.

---

### Post by skatona on 2010-05-22
THANK YOU !!

I am now able to get back into windows, albeit in a round about way.  I did steps 2 & 3 and when I tried to boot directly into windows it still gave me the no such device error.  But when I boot into the secondary drive (ubuntu) it now gives me a boot menu which gives me the option to boot the primary drive of windows and it works.  Strange way to get there, but it works.  I'll try to figure out how to do boot like normal later ...  thanks again.

Steve

---

### Post by bcbc on 2010-05-22
When you boot the primary it should boot windows directly. But you're getting a grub prompt which means you installed the grub bootloader to the primary drive MBR. So just replace this with the windows bootloader (or equivalent).

Boot ubuntu from the secondary. In the following example I'm assuming /dev/sda is the primary (you need to confirm this as maybe booting from the secondary makes the primary /dev/sdb)...
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This will install the lilo bootloader in a form that's equivalent to windows: it boots the partition marked active. Then after that you should boot directly into windows when you boot from the primary.

---

### Post by skatona on 2010-05-22
THANK YOU !

That was the finishing touch.  It worked and I am now able to boot directly from either drive.  Glad you guys and the forum are here.  Thanks again!

Steve

---

