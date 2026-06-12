---
title: "Installing grub in a partition not in the MBR"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by pardon? on 2009-11-15
hi,
My hard disk is organised as:
```
/dev/sda1               1       16379   131556348    7  HPFS/NTFS
/dev/sda2   *       16380       18246    14996677+  83  Linux
/dev/sda3           18247       30401    97635037+   5  Etendue
/dev/sda5           18247       18495     2000061   82  Linux swap / Solaris
/dev/sda6           18496       30401    95634913+  83  Linux
```
sda1 is my Vista partition, sda3 is my Ubuntu 9.10 / partition and sda6 my /home partition. 
Note that I've moved the boot flag from sda1 to sda2. I've installed 9.10 using the installer from the LiveCD and all works well but I wonder: if I have to re-install Grub2 for a reason how can I do it?
My question is: how can I, **using the cli**, install Grub2 in the sda2 partition instead of the MBR. Which command can I use. 
Using:
```
$ sudo grub-install --root-directory=/... /dev/sda
```
will install grub2 in the MBR if I'm not mistaken. And when I do:
```
$ sudo grub-install --root-directory=/... /dev/sda2
```
It reports an error.

---

### Post by louieb on 2009-11-15
GRUB2 gripes about being install in the boot sector of a partition. I had to use the --force option.  Complained but did it anyway.  
[IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

---

### Post by pardon? on 2009-11-15
Thanks louieb.
If I understand you you use grub-setup instead of grub-install. It's not exactly clear for me which command to use. Thanks for the link too. I'll read it carefully.

---

### Post by oldfred on 2009-11-15
Ubuntu does not use the boot flag. That is a windows (and maybe some other systems) thing. You can move it back to the windows partition without problem.

I installed grub2 to the partition when I installed alpha. At that time it did not complain, but now on every update I get the warning message about blocklists. System works fine, I currently chainboot from an old grub only partition to grub2 in the Karmic partition.

---

### Post by pardon? on 2009-11-15
> **oldfred said:**
> Ubuntu does not use the boot flag. That is a windows (and maybe some other systems) thing.

Yes but if i don't move the boot flag to the Ubuntu partition then when I reboot, the BIOS starts Vista instead of Ubuntu. That's why I've done it.

---

### Post by louieb on 2009-11-15
Your right - think i did use grub-setup. That was just after the beta came out. - All I known I'm chainloading Karmic from GRUB legacy in my Jaunty install. 

About the boot flag - thats kinda weird - did not know that some BIOS look for the boot flag.  :DI'll have to put that in my odds and end bag.

---

