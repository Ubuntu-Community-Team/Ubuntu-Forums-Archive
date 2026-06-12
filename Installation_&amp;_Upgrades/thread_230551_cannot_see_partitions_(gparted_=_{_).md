---
title: "cannot see partitions (gparted = :{ )"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by cd-r80 on 2006-08-06
Cannot install Ubuntu or Xubuntu. Install does not see partitions only one empty disk. DiskDrake sees everything ok. Old mandrake installs very well. but how can I install ubuntu and really that so the inst. prog sees partitions. Gparted sucks, at least for a while. Gparted live Cd has the same problem. So it is the Gparted the problem. Can I still install Xubuntu or Ubuntu????? I have Hda1 / windows. I had ubuntu 5.04 at same disk. Xubuntu inst. messed all..

---

### Post by bscbrit on 2006-08-06
How are the partitions formatted, in fact, how is the hard drive configured?

---

### Post by anindya_m on 2006-08-06
Can you please post the output of fdisk -l from a root terminal (this can be done after the live cd has booted). gparted can sometimes get confused if it sees certain partitioning arrangements, but fdisk will usually work. If you see your partitions this way you can use fdisk to create the partitions and then try running the installer again.

---

### Post by cd-r80 on 2006-08-06
I Have windows C: / hda1. then D and E. (dont remember hdas)
Linux Mandrake on hda7,swap,/home & usr/ at the end. 

Like:windows: hda1 / extended: /hdax /hdax Linux: hda7 swap hda8 hda9...

---

### Post by anindya_m on 2006-08-06
A quick question: do your linux partitions use LVM (Logical Volume Management)? AFAIK gparted cannot see LVM partitions. You can check by using fdisk -l /dev/hda while booted into Mandrake (if Mandrake can boot). I had a similar problem on a system which had Fedora installed. I remember in that case gparted wouldn't show *any* partitions. Finally I had to delete the linux partitions using fdisk and then it worked.

---

### Post by bscbrit on 2006-08-06
As Anindya_m suggested, the output of fdisk -l would be useful, as would the answer to his question regarding LVM.

---

### Post by cd-r80 on 2006-08-06
fdisk -l /dev/hda:
Disk /dev/hda: 255 heads, 63 sectors, 2481 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hda1   *         1       255   2048256    b  Win95 FAT32
/dev/hda2           256      2361  16916445    5  Extended
/dev/hda5           256       510   2048256    b  Win95 FAT32
/dev/hda6           511      1403   7172991    b  Win95 FAT32
/dev/hda7          1404      1719   2538207   83  Linux
/dev/hda8          1720      1787    546147   82  Linux swap
/dev/hda9          1788      2243   3662757   83  Linux
/dev/hda10         2244      2481   1911672   83  Linux

I cannot see anything about LVM? how to clean with fdisk without losing windows? Old lilo /mbr what to do with them? No more hds in use..

---

### Post by bscbrit on 2006-08-06
What is the contents of your /etc/fstab? please

---

### Post by cd-r80 on 2006-08-06
/dev/hda7 / reiserfs notail 1 1
none /dev/pts devpts mode=0620 0 0
none /dev/shm tmpfs defaults 0 0
/dev/hda9 /home reiserfs notail 1 2
/dev/scd0 /mnt/cdrom auto user,iocharset=iso8859-1,umask=0,exec,codepage=850,ro,noauto 0 0
/dev/fd0 /mnt/floppy auto user,iocharset=iso8859-1,umask=0,sync,exec,codepage=850,noauto 0 0
/dev/hda1 /mnt/win_c vfat iocharset=iso8859-1,umask=0,codepage=850 0 0
/dev/hda5 /mnt/win_d vfat iocharset=iso8859-1,umask=0,codepage=850 0 0
/dev/hda6 /mnt/win_e vfat iocharset=iso8859-1,umask=0,codepage=850 0 0
none /proc proc defaults 0 0
/dev/hda10 /usr reiserfs notail 1 2
/dev/hda8 swap swap defaults 0 0

---

### Post by bscbrit on 2006-08-06
I think that the problem is that the partitions are formatted as reiserFS.  Although ubuntu can use these partitions, I'm not so sure about gparted recognising them.
I'll go away and try and Google for some information.

---

### Post by cd-r80 on 2006-08-06
Hmm they were first XFS partitions, then Under Xubuntu I changed them as reisers, which I want to use... I rebooted and Xubuntu or  LIVE-Gparted-Cd cannot see the partitions anymore. Only Diskdrake sees them correct. XFS was regognised at first time by Xubuntu install. But why Gparted does not see even Fats now?.. hmm...I think Xubuntu and Ubuntus use gparted when installing? Strange but Xubuntu "Disk" program sees the partitions! Someone Fix Gparted? ! or what?

---

### Post by anindya_m on 2006-08-06
I have used gparted with reiserfs in Dapper. It usually works fine. But this conversion from XFS to Reiser you mention may be causing the trouble. Are you familiar with fdisk? Basically you can launch it as```
fdisk /dev/hda
```then press **p** to show the partitions. Note the partition numbers. To delete any partition press **d** and then the number. Finally press **w** to save changes and exit. If you do this then please be very careful so that you don't accidentally delete your windows drives.

---

### Post by cd-r80 on 2006-08-06
Even Live-CD-Gparted partitioning tool cannot see even windows parts. Diskdrake sees all ok, but Xubuntu, Ubuntu install uses Gparted, I think so.? So perhaps only Fix to Gparted helps?!

---

### Post by anindya_m on 2006-08-06
I agree there's a problem with gparted. What I was suggesting is that you delete the linux partitions using fdisk (or even DiskDrake from the Mandrake install CD) and then launch the ubuntu install, as a workaround. This time gparted will probably work.

---

### Post by bscbrit on 2006-08-06
Alternatively, as you know which partitions you want to use - from the contents of fstab - you can simply skip the gparted stage and select manual partition selection.  Simply tell it which partition you wish to use for what purpose, and reformat the ones that do not contain data that you need to keep.  Ubuntu will accept the partitions and use them as directed.  This assumes, of course, that they are not corrupted beyond recovery.

---

### Post by anindya_m on 2006-08-06
I agree. It is probably the easiest way. Anyway if there's a corruption in any partition then you'll get an error. In that case you'll have to recreate that particular partition.

---

### Post by cd-r80 on 2006-08-07
All Ok for now then. I deleted old partitions in Mandrake with fdisk. I downloaded Xubuntu-alternate inst. CD & installed & configured it ok in text inst.

---

### Post by bscbrit on 2006-08-07
Good news - enjoy your Ubuntu experience!

---

