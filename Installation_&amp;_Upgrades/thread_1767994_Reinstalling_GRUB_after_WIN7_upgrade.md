---
title: "Reinstalling GRUB after WIN7 upgrade"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by bfromcolo on 2011-05-26
I have read about 100 posts on this topic and just seem to be confusing myself.  I had a dual boot system running XP and 10.10, the system has 3 physical drives.  I upgraded XP to WIN7 and predictably the boot loader has been over written by Windows.  I have attached the details for my configuration.  I am booted up on the 10.10 Live CD now.  Can someone tell me the right commands to properly re-install GRUB?  

Thanks

sda is the Linux install
sdb is the WIN7 install and boot drive
sdc is supplemental storage


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by lmarmisa on 2011-05-26
You need to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Open a terminal and type these two commands:

```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Reboot the system normally and type this command:
```

sudo update-grub

```

---

### Post by bfromcolo on 2011-05-26
I guess this is part of my confusion, wouldn't the commands provided install GRUB on sda and I want it installed on sdb?

---

### Post by lmarmisa on 2011-05-26
I recommend to configure your BIOS in order to boot from sda and to install the GRUB loader in the MBR of the hard drive where Ubuntu was installed (/dev/sda).

---

### Post by bfromcolo on 2011-05-26
OK I guess that was simpler than it looked.  All's working fine again.

Thanks

---

