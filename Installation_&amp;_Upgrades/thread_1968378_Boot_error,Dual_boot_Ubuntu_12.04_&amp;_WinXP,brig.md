---
title: "Boot error,Dual boot Ubuntu 12.04 &amp; WinXP,brightness adjustment"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by harshthakar on 2012-04-29
Hi,
I am using a desktop PC with 2 hard disks,1 having Ubuntu 12.04 & the other Windows XP.
I have made a fresh installation of  Ubuntu 12.04(was using 11.04 earlier).
After fresh installation of  Ubuntu 12.04 the following error is displayed on starting the computer,

error no such devicea 32 digit alph numeric number is displayed)
grub rescue>

On manually chosing the hard disc having  Ubuntu 12.04 a proper menu is displayed having boot options for  Ubuntu 12.04 & Windows XP,previously this option was available on startup.

While using  Ubuntu 11.04 I was able to adjust brightness using Shift + +/- keys,in 12.04 this doesn't work.
In 12.04 no brightness option is available in System settings>personal>brightness & lock.
I have attached a screenshot of this window.

Please advice how should I fix this problems.

---

### Post by dino99 on 2012-04-29
- check in the bios that you are booting on the disk having grub installed on

- you can reinstall grub from a livecd (liveusb) on /dev/sda (supposing having ubuntu ) or /dev/sdb otherwise

sudo grub-install /dev/sda
sudo update-grub

---

### Post by harshthakar on 2012-04-29
Hi,
Found a solution to booting problem.All I had to do was,go to BIOS> boot settings when the computer starts,change boot setting to first boot hte hard disc having booting options and thats it.boot problem. solved.:smile:
Thanks dino99.
Still have to figure out how to adjust brightness.

---

