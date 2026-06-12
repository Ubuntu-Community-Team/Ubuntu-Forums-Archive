---
title: "Reboot with new 8.04 install and Error 17"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by GoliathWest on 2008-04-20
I installed 8.04 beta on a Dell laptop. Worked very well for 24hr and everything appeared OK until reboot. Now I am unable to get past the Grub screen as it returns Error 17.

I booted with a live CD and brought up a terminal- Here is my partition table:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris

I don't know why a Linux partition is not showing up here or how to get around the Grub Error.

Thanks in advance for any help on this one.

---

### Post by Pumalite on 2008-04-20
You failed to create a partition for root ('/')

---

### Post by Pumalite on 2008-04-20
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by GoliathWest on 2008-04-20
If you choose 'guided' vs manual at the partition step of the install process, do you have a choice to create a root partition?

---

### Post by Pumalite on 2008-04-20
If you use 'Guided', the installer does everything for you (it usually creates a '/' partition and a /swap one). But is risky. Manual is safer. Is good to backup everything before the installation of any new OS.

---

### Post by GoliathWest on 2008-04-20
Pumalite,
Thanks for all of your suggestions. Doesn't sound like I will be able to recover anything.

Could the root partition be located on the machine but not detected? I saw a web posting that said it is possible that initrd is missing the modules to access the partition(s).

---

### Post by Pumalite on 2008-04-20
sudo fdisk is pretty reliable. You could get Gparted Live CD, burn to disk and boot from it. And then take a screen shot. I'm sure it'll be the same.

---

