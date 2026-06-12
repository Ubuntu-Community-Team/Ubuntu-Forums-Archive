---
title: "Dual Boot Xp-Ubuntu 7.04... Error 21"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by trsix on 2007-05-25
Hi, Im new to Ubuntu and I am having an issue with the Grub boot loader... (I think)

**About my system:**
[INDENT]HPXW 8000
Dual 2.66Ghz Xeon Processors
3GB Ram
2 x 36GB scsi drives
1 x 60GB IDE drive
Windows XP installed on 1 Scsi HDD
Attempting to install Ubuntu on a partition on the 60GB drive
(other information available upon request)[/INDENT]

**Process which got me to where I am currently having the issue.**
[INDENT]1. Put the Ubuntu 7.04 CD into the drive
2. Booted my computer to the Ubuntu LiveCD environment
3. Doubleclicked on Install Icon.
4. Followed the on-screen prompts
5. Re-booted after successful install (no errors came up)
6. After reboot, "Grub Error 21"  (Im not left with a grub prompt, just that error, all I can do is reboot and get the same error message)[/INDENT]

**I am attempting to do one of two things.**
[INDENT]1. Get Ubuntu and Windows XP dualbooting (most preferable)
2. Get Windows XP booting again[/INDENT]

**I will post my fdisk here:**
[INDENT]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 36.4 GB, 36420075520 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4426    35551813+   7  HPFS/NTFS

Disk /dev/sdb: 36.4 GB, 36420075520 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4426    35551813+   7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdc2            3825        5685    14948482+   f  W95 Ext'd (LBA)
/dev/sdc3            5686        7297    12948390   83  Linux
/dev/sdc5            3825        5608    14329948+   7  HPFS/NTFS
/dev/sdc6            5609        5685      618471   82  Linux swap / Solaris[/INDENT]

**I am anxious to get this working again so please let me know if there is anything you think I should post or try and I will be happy to try it out**

---

### Post by Ub1476 on 2007-05-25
Um, if I remember correct, error 21 means that grub can't detect anything to boot from, or something like that. I've seen at forums that you need to insert the xp cd, then choose repair, and write two commands in correct order. I don't remember the link, but it took me two minutes to find it, searching for something similar to "error 21" in Google. Although I find it odd that you get that error when you just installed Ubuntu. Anyways, take a search at Google, and here's a guide for dual-booting XP and Ubuntu (XP installed first), if you should have happened to miss something.:p It's for Edgy, but that shouldn't matter. Good Luck:)

[Link to guide]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu")

---

### Post by mikewhatever on 2007-05-25
Grub very often gets confused when there are numerous hard disks present. You can try getting the Super Grub Disk to boot into Ubuntu and diagnose, or mount Ubuntu's partition and post your grub menu from /boot/grub/menu.lst and the device map from /boot/grub/device.map
[SUPER GRUB DISK]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by trsix on 2007-05-26
Thanks for the information, I will see what I can find... I'll post the outcome.

Trsix

---

### Post by trsix on 2007-05-26
Ok, things are a "little" better.

Ive managed to use the SGD to get my system to boot back to XP.

I still have Ubuntu installed on my secondary harddrive but what I am thinking is that I will use my second 36GB scsi drive to install Ubuntu on and then hopefully things will go smoother.

Thanks very much for the SGD option, that really helped me out alot.

I will keep updating on my progress and post anything that might be helpfull to others.

(NOTE: I used the SGD Floppy boot disk to restore my MBR to allow me to boot to windows.  I still have not figured out why grub comes up with the Error 21 and then just stalls there.  Anyone with experience should post regarding this issue   :)

Thanks, and off to work i go :)

---

### Post by confused57 on 2007-05-26
Yes, the SGD is a great tool...what you might want to try is to install grub to the mbr of the drive with Ubuntu, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
it would be something like this:
```
sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit
```

Then set your bios to boot first to the drive with Ubuntu, if you get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hdx,y) to (hd0,y), then press "b" to boot...this change is temporary, if it works.

If you still get the error 21, then you might need to check in your bios & see if the Ubuntu drive is identified & setup correctly.

---

### Post by trsix on 2007-06-01
Ive got things working now.

basically what i did was decide that both Ubuntu and Windows required their own scsi drive for the main OS.

I moved ubuntu to my other scsi drive and did a re-install of grub.

Everything is working perfectly now.

Thanks for the help  regarding this issue.


..six

---

