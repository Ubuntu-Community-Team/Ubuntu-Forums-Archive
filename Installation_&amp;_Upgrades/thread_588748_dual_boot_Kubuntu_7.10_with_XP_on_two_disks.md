---
title: "dual boot Kubuntu 7.10 with XP on two disks"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by yair999 on 2007-10-23
Hi,

I have XP installed on a master disk and I have a 2nd NTFS slave disk for XP use.

I'd like to reduce the NTFS partition on the 2nd disk and free some space for Kubuntu installation.

Questions:

1. Can I ask the Kubuntu installation to reduce the NTFS partition on the 2nd disk and create whatever partitions it needs on the freed space SAFELY?

2. For a dual boot: If I set the bios to boot fron the 2nd slave disk, where should I ask the GRUB to be installed? On the 2nd slave disk's MBR or on a new partition created on that 2nd slave disk (which one)?

3. Do I need to edit the menu.lst file at all?

Thank you in advance,

Yair

---

### Post by Pumalite on 2007-10-23
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Degrag the drive several times. Resize the partition you want to shrink. I would let the boot order in the BIOS as it is. Install Ubuntu and let Grub install itself where it installs by default. If you have any problem with menu.lst, come back; we can fix it easily.

---

### Post by yair999 on 2007-10-24
> **Pumalite said:**
> ...I would let the boot order in the BIOS as it is. Install Ubuntu and let Grub install itself where it installs by default. If you have any problem with menu.lst, come back; we can fix it easily.

Thank you but I'd rather not let my master XP disk being touched by the installation and I understand it can be done. So my questions are still:

1. I can boot the slave via BIOS. Can I then ask the installation to be done on the slave?
2. If so, where exectly do I ask GRUB to be installed on the slave disk considering the first slave partition is NTFS for the the XP' use (XP installed on the master)?
3. Do I have to edit the menu.lst?

Thank you,

Yair

---

### Post by Pumalite on 2007-10-24
You better leave the drive you are going to install on in the computer alone. Do all I told you, then install; Grub will get installed to that drive. Later menu.lst will need to be modified, but you can be sure all your other stuff will be untouched.

---

### Post by yair999 on 2007-10-24
ok, it worked and I changed menu.lst as per this thread: [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
So now the dual boot works too.

Thank you.

---

### Post by Pumalite on 2007-10-24
Your welcome.

---

