---
title: "Windows dissappeared after Ubuntu installation."
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by hakelm on 2011-09-20
Yesterday I installed Ubuntu 11.04 on an Asus Eee PC 1215P with disappointing results. 
The intention was to get a dual boot Ubuntu/Windows 7 system.
Since I got the message "(initramfs) Unable to find a medium containing a live file system" (yes, I have checked the MD5-sum)
I selected to install ubuntu-11.04-alternate-i386 instead of ubuntu-11.04-desktop-i386.
After this I cannot boot the Windows 7 other than the Windows Recovery Environment which cannot find any Windows or any disks at all on the system.
Below you can find output from fdisk -l for this machine (A) and for a similar machine, an Asus Eeepc 1001 that sports the kind of installation I tried to accomplish (B).
Interestingly we find in A new partition sda1 that I don't think was there from the beginning and that the sda1 and sda2 file systems are designated SFS.
Ubuntu has no trouble reading the files on sda2.
I have all data backed up but I have invested a lot of time installing many programs on the Windows system so any advice on how to recover will be highly appreciated.
Thanks in advance
Håkan



A:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24f732d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048   209717247   104857600   42  SFS
/dev/sda3       209719294   488396799   139338753    5  Extended
/dev/sda5       209719296   285888511    38084608   83  Linux
/dev/sda6       484491264   488396799     1952768   82  Linux swap

B:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfcb46e7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10444    83891398+   7  HPFS/NTFS
/dev/sda2           10445       18558    65175674+   f  W95 Ext'd (LBA)
/dev/sda3           18559       19451     7173022+  1c  Hidden W95 FAT32 (LBA)
/dev/sda4           19452       19457       48195   ef  EFI (FAT-12/16/32)
/dev/sda5           10445       14269    30724281   83  Linux
/dev/sda6   *       14270       18376    32989446   83  Linux
/dev/sda7           18377       18558     1461883+  82  Linux swap / Solaris

---

### Post by Quackers on 2011-09-20
Windows being designated as SFS is not good. SFS means that Windows@ partitions have been changed from basic discs to dynamic discs. This is usually caused by an attempt to create more than 4 primary partitions, which is the maximum for a mbr partitioned disc.
There have been successful conversions, I believe, back to simple volumes (basic discs) but the road may be long and often the advice has been to re-install Windows.
However, have a look at this thread and in particular post #6

[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

You may also need to restore the Windows bootloader to the MBR of the hard drive (over-writing grub) to get Windows booting again. Grub can be re-installed later if necessary, if the Ubuntu installation survives.

---

### Post by YesWeCan on 2011-09-20
If you are really lucky, restoring the standard MBR boot code will get you into Windows again:
Boot live CD
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

fdisk reports the wrong label for type 42H partitions: it should report LDM (Logical Disk Manager) not SFS (Secure File System).

Do you recall if you shrank the Windows partition sda2 when you installed Ubuntu?

---

### Post by hakelm on 2011-09-20
You are probably right. It must have happened when I freed up space for Ubuntu.
The funny part is that windows can't see the partitions it created.
Thanks
Håkan

---

### Post by Quackers on 2011-09-20
That's likely because Windows' bootloader is not there any more - grub is.
You could try to get Windows booting again by repairing the bootloader with a Windows repair or installation disc.

---

### Post by YesWeCan on 2011-09-20
> **hakelm said:**
> You are probably right. It must have happened when I freed up space for Ubuntu.
The funny part is that windows can't see the partitions it created.
Thanks
Håkan
I am really interested to know how you freed up the space? What tool did you use? Did the Windows partition consume the whole disk before?

Have you tried reinstalling the standard MBR code using lilo?

---

### Post by hakelm on 2011-09-20
I used the windows disk manager and shrank the second partition. My first attempt resulted in something that Ubuntu considered "unusable". The second, in which I removed the second partition (d:), was more successful but probably resulted in the dynamic disks. I remember some kind of warning.
I was stupid enough to use the windows recovery tool to restore the MBR and now I can't boot anything. Have to reinstall to Ubuntu to try your trick.
H
d: is disk d

---

### Post by Quackers on 2011-09-20
If you've used the Windows recovery tool you may have re-installed Windows to the whole disc - over-writing everything!
It should boot though.

---

### Post by hakelm on 2011-09-20
I just run Bootrec.exe /FixMbr. What intrigues me is that I can start Windows Recovery Environment but that it can't find any disk or OS. Initially on boot I get Windows error recovery screen with two options: recovery and start Windows normally. The second results in a blue screen and reboot.
H

---

### Post by Quackers on 2011-09-20
Is this from the Windows recovery partition or from a recovery dvd or from a repair disc?

---

### Post by YesWeCan on 2011-09-20
> **hakelm said:**
> I used the windows disk manager and shrank the second partition. My first attempt resulted in something that Ubuntu considered "unusable". The second, in which I removed the second partition (d:), was more successful but probably resulted in the dynamic disks. I remember some kind of warning.
I was stupid enough to use the windows recovery tool to restore the MBR and now I can't boot anything. Have to reinstall to Ubuntu to try your trick.
H
d: is disk d
So you originally had both a C: drive and D: drive. You used Windows to shrink the D: drive and then tried to install Ubuntu but it reported "unusable"?
Then you deleted D: - presumably using Windows and you think at this point the drive was converted to LDM (dynamic disk) format?
Then you installed Ubuntu.

I am just trying to determine whether the Ubuntu installer did something naughty here. If my understanding of LDM is right, it should not have allowed you to install on a LDM drive.

The LDM format puts special metadata on the disk, at the end of the disk if I understand it right. If this gets corrupted then I presume the dynamic partitions will be unrecognizable.

---

### Post by hakelm on 2011-09-20
It must be from the recovery partition.
H

---

### Post by hakelm on 2011-09-20
I am sorry I am getting a bit out of sync. 
Yes I had C: and D:, first I shrank D: leaving som 30 GB for Ubuntu which was considered unusable. Then I removed D: and installed Ubuntu and told it to put Grub on the first partition. I have no idea if or when the LDMs where created.
H

---

### Post by Quackers on 2011-09-20
I haven't seen many recovery partitions with the command prompt option before (which is necessary to run bootrec.exe /fixmbr)
Did you start it from the grub menu or with a special key press during boot?

---

### Post by hakelm on 2011-09-20
According to fdisk sda2 is the boot partition.

---

### Post by hakelm on 2011-09-20
On boot I get something that translated from Swedish is Windows start handler. There I have two options, one is  Windows 7 the other is Ubuntu (from WUBI) (doesn't work).
If I select Windows 7 I get two selections:
  Start Startrepair (recommended)
  Start Windows normally.
The recommended option results in "System Recovery options"
H

---

### Post by hakelm on 2011-09-20
Grub disappeared after fixmbr.

---

