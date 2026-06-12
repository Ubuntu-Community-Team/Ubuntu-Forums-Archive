---
title: "Dual Boot Vista and Ubuntu 7.10"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by scott1978 on 2008-04-01
Hi,

I just wanted to say hi as I have just joined this forum and installed Ubuntu for the 1st time on my spare hard drive.

This is also the read for the post, basically when the PC loads it seems that grub come on and starts up Ubuntu, as I have Vista installed on 1 hard drive and Ubuntu 7.10 on another I cant load windows.  Basically I want to have the machine come on and the I get a choice of loading vista from 1st HD or Ubuntu from the 2nd HD.  All my kids book marks and PC knowledge is based on windows so it much be the default operating system and Ubuntu is just for me - can anyone give me a step my step guide to doing this please?

Thanks

---

### Post by Pumalite on 2008-04-01
Welcome. It's very simple. Install Ubuntu, go 'Manual', point to your second hard drive and make 3 partitions:
10 GB for '/'
1 GB for /swap (I assume this is a Desktop)
The rest for /home
Then press 'Forward'
This will install Grub to your Vista MBR and you'll have dual boot.
I hope you have 2 SATA or 2 IDE
Mix of SATA and IDE, means is better to have both OS in the SATA and use the IDE for storage.

---

### Post by scott1978 on 2008-04-01
Hi,

Thanks for the reply - does that mean that I will have to reinstall Ubuntu as that is what I am using now and it seems that the live CD has created the 3 partitions on the IDE hard drive already.

The drive with Vista is a SATA drive.

Cheers

---

### Post by Pumalite on 2008-04-01
You are better off allocating space for Ubuntu with the Vista partitioner, then installing Ubuntu in the new space in the SATA and keeping the IDE for a /home for Ubuntu if you want.

---

### Post by Pumalite on 2008-04-01
Here is a guide:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

