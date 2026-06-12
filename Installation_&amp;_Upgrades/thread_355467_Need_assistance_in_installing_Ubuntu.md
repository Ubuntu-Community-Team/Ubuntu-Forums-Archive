---
title: "Need assistance in installing Ubuntu"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2007-02-07
I am thinking of installing Ubuntu Dapper Drake 6.06 on the computer. It currently has the following partitioning:
40 GB - WinXP
20 GB - Win2000
5 GB - FAT32
~15 GB - unpartitioned
The choice of OS is made with BootMagick - a menu with the available OS's is shown...
My idea: install Ubuntu in the unpartitioned drive and make it install GRUB there! Later somehow the BootMagick must be configured to add an entry for Ubuntu - so that it can also load its Grub :)
Is my idea good?

---

### Post by tommcd on 2007-02-07
I think it would be best to let ubuntu install grub to the master boot record. It is easy to scroll up and down with the arrow keys to select the OS to boot with in grub.
Looks like these 2 guys had problems with boot magic and linux:
[http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html](http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html)
[http://www.techspot.com/vb/topic48230.html](http://www.techspot.com/vb/topic48230.html)
Plus, if you want to learn linux, you should learn grub. It is not very difficult:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Herman's page is everything you would ever want to know about grub.
EDIT: Grub will allow booting winXP and 2000 just fine.

---

### Post by Zdravko on 2007-02-07
But will GRUB detect the other 2 already installed OS?

---

### Post by reiki on 2007-02-07
Grub should detect them just fine. I know I just did a Feisty install (next version of Ubuntu under development) into some free space on a hard drive and when it came time for grub to be installed it found the Win XP installation with no problem. You'll want to learn a little bit about how grub works, but if you just go ahead and install, and let grub be installed on the MBR, worst case scenario is you'll still be able to boot to Ubuntu and you can come in here or go on IRC (using XChat) and we'll help you get your grub menu straightened out.

OR... if you get REALLY stuck and can't find help fast enough, you put in your XP CD and repair the MBR from there. You won't be able to boot Ubuntu if you do that, but at least you'd be back on familiar ground. From where we can then help you reinstall Grub properly. 

Again... not hard... just not what you're used to. No worries. It works.

---

