---
title: "Cannot dual boot?"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by brokkenwilliam on 2010-07-05
Hi all,

When I recieved this computer, I immediately install ubuntu on it and got everything set up. However, I soon realized that I needed Windows (and not just the virtual machine) for other needs. I installed Windows XP and now the computer will only boot windows and I cannot figure out how to boot ubuntu. I did not have grub installed on my ubuntu side. However, I think i just need to boot into ubuntu once so that I can set up my dual boot.

I know that what I did was really stupid :frown: so please no flaming.

Oh btw my computer is a sager 2096 HL90 if that makes a difference.

---

### Post by oldfred on 2010-07-05
You just need to reinstall grub or grub2 depending on which version you have. Do not mix as that makes it worse.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by brokkenwilliam on 2010-07-05
Ok great got grub installed.

Now I boot and I get the grub command line. How do I work this to dual boot Windows Xp and Ubuntu 10.04?

---

### Post by brokkenwilliam on 2010-07-05
UPDATE:

So i figured out how to boot into ubuntu. Then, i went into terminal and did "sudo update-grub". However, the computer still boots with a command line. Help????

---

### Post by libssd on 2010-07-05
**See**: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

**Tip**: If your machine can boot from a USB flash drive, get an 8gb drive, and do experimental installs there. Much less exciting.

---

### Post by oldfred on 2010-07-05
I do not understand why after the install of grub and the sudo update it is not working. perhaps reinstalling after you manually boot into your system.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

To get grub to remember where to reinstall:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

