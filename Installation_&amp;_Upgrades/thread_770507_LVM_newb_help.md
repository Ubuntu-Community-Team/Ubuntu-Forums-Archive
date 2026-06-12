---
title: "LVM newb help"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by CyberCowboy on 2008-04-27
I've been using Linux for about 10 years and ubuntu for about 3, however this is my first time with LVM.

Ok with Hardy I decided to add LVM to my main machine.  My understanding 
is that I need a seperate /boot partition since natively a system can't 
read a LVM here's my setup
I am doing this from the 64 bit alt install CD with a clean install.

SDA
40 GB NTFS (with XP on it for legacy problems going away soon)
70 GB free space for future lvm growth

SDB
 part 1: 256 MB /boot partition
part 2: 156 GB partion in LVM mode
       Part 2 a: 6 gb swap
       part 2 b: 50 GB / partition
       part 2 c:  100 GB /home

My problem is I've never had a /boot seperate before and my system 
doesn't seem to be booting.  What all partitions need a boot flag?  I 
presume the /boot and the NTFS, but does the LVM as well?

thanks for the help in advance

---

### Post by wcorey on 2008-04-27
[QUOTE=My problem is I've never had a /boot seperate before and my system 
doesn't seem to be booting.  What all partitions need a boot flag?  I 
presume the /boot and the NTFS, but does the LVM as well?

thanks for the help in advance[/QUOTE]

I am having issues with LVM as well but not yours. Clearly the /boot native partition needs to be marked as bootable. I do not believe you can have multiple bootable partitions defined.  I installed Friday from the 64bit alternate ISO just as you did. I selected the second option install with LVM but not the encrypted LVM. The preinstall portion wiped out the Vista partition as it was both hard drives so I guess it had no alternative. I wedged it the first time and it did not let me continue because it said I did not have a root or boot (I forgot now) partition. In any event I did have both. I reinstalled Vista and re installed Ubuntu 8.04. My first drive had the following paritions, /root, /boot, and swap and my second drive I specified as one partition LVM eligible. I did a finish and the rest of the install went fine. However DF only showed the /root partition as usable space not the second entire drive/partition which did show on the pvscan. I did an lvextend to add that space from the 2nd PV and it deallocated the free space from the second drive and showed the LV as having 465+GB. That should be goodness except the DF command still only showed 230GB as usable and something around 100MB as being in use so clearly it does not see the space in the second PV as being part of the DF available space. An issue I have is which is correct, the DF or the LVDisplay as far as how much space is really available to me. I would be curious with what you see when you get to that point.

Walt

---

### Post by spvo on 2008-04-30
CyberCowboy, I had the same problem the other day when I installed hardy.  Turns out it was a simple mistake.  I created the separate boot partition, but did not tell the ubuntu installer that the mount point for it was to be /boot.  Instead it put the boot files into the LVM partition.  Which, for me, resulted in errors.  You might want to check your boot partition and ensure the files were actually written there.

---

### Post by wcorey on 2008-04-30
> **spvo said:**
> CyberCowboy, I had the same problem the other day when I installed hardy.  Turns out it was a simple mistake.  I created the separate boot partition, but did not tell the ubuntu installer that the mount point for it was to be /boot.  Instead it put the boot files into the LVM partition.  Which, for me, resulted in errors.  You might want to check your boot partition and ensure the files were actually written there.


Has anyone installed 8.04 with LVM that spanned multiple hard drives? 

Thanks,
Walt

---

### Post by CyberCowboy on 2008-04-30
THanks for the help everyone, I figured out my problem, simple PEBKAC (Problem exists between keyboard and chair) I switched from ATA and AHCI which changed the boot order in the BIOS, as soon as I fixed it I was up and running.

Wcorey, I am spanning 2 hard drives at the moment, did you have questions?

---

### Post by wcorey on 2008-05-01
Yes, I am having trouble doing the same on a xps 720 with two 250GB drives and firmware raid 0. There are two issues here, one is what I will explain below and the second is Ubuntu, unlike Windows, Fedora, OpenSuse does not honor the firmware raid 0. In order to get the installed system to boot I have to disable firmware raid on both drives. That shouldn't be required as not only Windows honors it but so do other distros. OK, on to the other problem.

Here is a pvscan and lvdisplay:

walt@cor720:~$ sudo lvm pvscan
  PV /dev/sda5   VG cor720   lvm2 [232.59 GB / 0    free]
  PV /dev/sdb1   VG cor720   lvm2 [232.83 GB / 0    free]
  Total: 2 [465.42 GB] / in use: 2 [465.42 GB] / in no VG: 0 [0   ]
walt@cor720:~$ sudo lvm lvdisplay
  --- Logical volume ---
  LV Name                /dev/cor720/root
  VG Name                cor720
  LV UUID                g2Jod5-ZqxW-U5Ju-TS7B-QJG5-yIUP-v68cJJ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                456.56 GB
  Current LE             116880
  Segments               2
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/cor720/swap_1
  VG Name                cor720
  LV UUID                uMXrIl-dDqS-VLrz-VzuL-u2T3-4Ybf-PqMggF
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                8.86 GB
  Current LE             2267
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1

That looks pretty good, right? Says I have two 250GB physical volumes and one logical volume (well 2 counting swap) and that the 465GB LV has two segments, presumably the 2 PV's. HOWEVER
walt@cor720:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x561ee893

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30394   243890797+   5  Extended
/dev/sda5              32       30394   243890766   8e  Linux LVM

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a92d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+  8e  Linux LVM


walt@cor720:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/cor720-root
                     232754316 178490704  42533488  81% /

You can see from the df that it shows only the first drive (232GB). The available is counting mounted nfs drives. I do not understand why when lvm is happy I have 465+GB from the two drives, well presumably from the two drives, the disk system shows only the first. Now the fstab the install created follows, if that is any hint.
proc            /proc           proc    defaults        0       0
# /dev/mapper/cor720-root
UUID=1484d5c4-baa1-4520-a443-de92282cb1f9 /               ext3    relatime,errors=remount-ro 0       1

Further down it has the mount for the swap LV.Notice though the UUID of the /dev/mapper/cor720-root and the uuid from the lvdisplay. They differ. I tried specifying that UUID and got 222GB.

Can you, or anyone else decipher this please?

Thanks,
Walt

---

