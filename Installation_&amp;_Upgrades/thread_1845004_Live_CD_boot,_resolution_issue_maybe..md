---
title: "Live CD boot, resolution issue maybe."
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by Lues on 2011-09-16
Hi, I want to install Ubuntu on my laptop, and remove the windows 7 installation I currently use. I had Ubuntu installed with XP in a dual boot situation 2 years ago but after I upgraded to 7 I removed it. Anyway, the problem I am having is that when I boot up the CD the screen gets messed up and splits into three zones. See images. If anyone can tell me what the heck is going on in these photos and how to fix it I would really appreciate it. I have used two different CD's burned from two different drives and both times the same result.

[IMG]http://http://imageshack.us/photo/my-images/571/0916010256.jpg/[/IMG][[IMG]http://img571.imageshack.us/img571/7544/0916010256.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/571/0916010256.jpg/")
[[IMG]http://img507.imageshack.us/img507/2008/0916010258.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/507/0916010258.jpg/")



[IMG]http://http://imageshack.us/photo/my-images/571/0916010256.jpg/[/IMG]

---

### Post by mörgæs on 2011-09-16
Hi, welcome to the fora :-)
Please give a complete hardware description.

---

### Post by Lues on 2011-09-16
Ok, here is the hardware. Please let me know if anything else is needed.

HP Pavilion dv6700 Notebook PC 
dv6915nr is the actual model number
3.00 GB RAM
NVIDIA GeForce 7150M / nForce 630M
AMD Turion 64 X2 TL-60 2.00 GHz

also found this thread while researching, but I'm not sure I understand it. [http://ubuntuforums.org/showthread.php?t=1689643](http://ubuntuforums.org/showthread.php?t=1689643)
in my case I can't seem to progress farther than the choose your language and boot live or install screen.

---

### Post by mörgæs on 2011-09-16
Yes, that thread seems to have the solution. 

When you get stuck at the messed-up screen, try pushing Alt+Ctrl+F1. Now you should have a text window where you can log in again.

After doing this, try executing the four commands beginning with sudo.

---

### Post by Lues on 2011-09-16
I tried typing in the commands just like that post says and nothing happened. As for the second part of the post, about pressing e at the grub menu. Doesn't ubuntu already need to be installed for that to work? If not could someone elaborate on how I can reach the grub menu?

---

### Post by Lues on 2011-09-16
I was able to solve this issue by first pressing shift while the CD was booting. It gave me access to a screen that had Boot Live, Install, Memory Test, and a few other options. By selecting the boot live option and pressing F6 I enabled (or disabled, made an x next to) nomodset. Then booted up the live CD, once the CD booted and I was in the Ubuntu test mode, I clicked the Install icon on the desktop and everything is working fine now. Thanks.

---

