---
title: "Error 13 and 7 on separate disk install"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by njaneardude on 2007-12-01
<NOOB ALERT>

I've searched the threads but can't seem to come up with an all around solution.

Here is my situation.  XP on IDE HD0, added a new disk, slave, both on master select.
Installed Ubuntu GG on HD1 and GRUB on HD1.  

Rebooted, went straight to XP, okay, at least I know my XP isn't hozed.

Went into BIOS changed boot order to DISK #2

GRUB loaded, XP/2000 OS available, yeah, tried it, got Error 13

But wait, tried Ububtu and got an Error 17, apparently all classics in the dual boot arena?

Changed BIOS back to DISK 0 and alas, back in XP world.

Puhleez point me in the right direction :  )

:lolflag:

---

### Post by meierfra on 2007-12-01
Ubuntu sometimes gets confused  with two hard drives. Probably you just have to edit  the file menu.lst.

I can give you detailed instructions but I need a little bit of information.
Boot from the Ubuntu Live CD, open a terminal (Applications->Accessories->Terminal)
Type

```
sudo fdisk -l
```

(l is a lowercase L)

and post the output.

---

### Post by njaneardude on 2007-12-02
Thanks for the reply!  You know, the disk I installed Ubunto on was formatted NTFS, could that have caused a problem?  It's on the 40GB drive.

Cheers,:popcorn:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e5820df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02370236

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4682    37608133+  83  Linux
/dev/sdb2            4683        4866     1477980    5  Extended
/dev/sdb5            4683        4866     1477948+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by meierfra on 2007-12-02
The instructions in the following post should work for you,too:
[http://ubuntuforums.org/showthread.php?t=627776#12]("http://ubuntuforums.org/showthread.php?t=627776#12")

---

### Post by njaneardude on 2007-12-02
Thanks, but all is well.  I realized, het "Man up" and injstall GRUB on HD0 like it wants to!
I'm in Ubuntu now and XP comes up fine!  Thank you!

Now to install Skype and import my Thunderbird settings :  ):guitar:

---

