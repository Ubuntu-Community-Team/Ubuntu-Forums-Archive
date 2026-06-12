---
title: "Installation problem"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by billybob1982 on 2008-08-02
Hi forum! I want to install two OS on my hard disk, Windows XP and Ubuntu. After installing Windows, when I try to install Ubuntu on the same disk(different partition), I get up to the point where it installs the grub bootloader then it says that it Could not install Grub lootloader on the disk and that it is a fatal error. I'm running an AMD 64 Athlon X2 processor on an Asus A8N-E mobo, one GB ram. Has anyone seen this problem before? What can I do to resolve the issue? The live CD runs fine, just a problem installing the bootloader. Thanks in advance!

---

### Post by redraiderbum on 2008-08-02
Try to install the lilo boot loader if you have the option.  You could try putting linux on the first partition and windows on the second or vice versa (whichever you haven't tried).

---

### Post by billybob1982 on 2008-08-08
This doesn't work because when you try to install Ubuntu 8.04, the Grub bootloader tries to install automatically. So then it reaches an error because it can't, and nothing gets installed. Help, please!

---

### Post by falcon61102 on 2008-08-08
As you go through the settings to install Ubuntu, one of the last screens you should get is a type of summary and it has an Advnaced button on it.  Click that button and it should allow you to choose where you wish to install the GRUB.  It may be that it cannot install the GRUB to the default location but if you specify a new one, say your Ubuntu partition, it may work.

If that doen't work, I'd check the integrity of the CD, could be a problem with that.

---

### Post by billybob1982 on 2008-08-09
For some odd reason it installed fine this time. The installation was a 32-bit Kubuntu 8.04. I clicked the advanced tab on the last step before formatting, but I kept the default settings(hd0). It said that it was successfully installed, needed to reboot to use the operating system. And so I did. The problem now is that after I rebooted, the bootloader that appeared was the normal one for Windows XP Professional and the Recovery console. Now I'm pretty sure that the Kubuntu installation is there, I just cant get to it. I have two hdd's. One is one my primary IDE channel and is used basically just for storage. The other hdd is SATA. The SATA is the boot device. First on the disk physically is my Windows XP installation(30GB), next comes the Kubuntu(20GB), then swap(1GB), and the rest is storage, all on a 250GB drive. I'm thinking that GRUB is written in the wrong place. Is it supposed to overwrite the Windows XP bootloader? If so, how do I do that? Please help!!!!!!!!!

---

### Post by falcon61102 on 2008-08-09
If the GRUB is not one the boot device, then it's not going to load at startup and from the sounds of it, this is what's happening.  The install put the GRUB on the first drive in your computer so even if your SATA is your boot drive, if it's not considered the first HD, then it wasn't installed there. First you need to find out which HD is considered the first drive.  You can run:
```
sudo fdisk -l
```
-l being a lower case L

That will list all your drives and partitions.  Then you can find out where exactly the GRUB was installed by using:
```
sudo grub
find /boot/grub/stage1
```

If you can post the results from both of those commands along with any errors, if you receive any, we can help figure this out.

---

### Post by billybob1982 on 2008-08-09
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab42ab42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6226       18890   101731612+   7  HPFS/NTFS
/dev/sda2               2        6225    49994280    f  W95 Ext'd (LBA)
/dev/sda5               2        6225    49994248+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x003a0039

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sdb2            3917       30400   212732730    f  W95 Ext'd (LBA)
/dev/sdb5            3917        6396    19920568+  83  Linux
/dev/sdb6            6397        6527     1052226   82  Linux swap / Solaris
/dev/sdb7            6528       30400   191759841    7  HPFS/NTFS



That was returned from fdisk -l.

---

### Post by billybob1982 on 2008-08-09
(hd1,4)

that was returned from the other command

no errors

---

### Post by falcon61102 on 2008-08-09
If you stage1 is on hd1,4 that means you need to install the GRUB to HD1 instead of hd0 where it is now.  To do this, go back to the terminal and run:
```
sudo grub
root (hd1,4)
setup (hd1)
quit
```

When you run the setup command, you will know it succeeded if you don't receieve a "Fail" at the end of any of the lines that print out.  Try that and then restart.

---

### Post by billybob1982 on 2008-08-09
That did it. THANKS!!!!!!!!!:)

---

### Post by falcon61102 on 2008-08-09
No problem, glad it worked.

---

