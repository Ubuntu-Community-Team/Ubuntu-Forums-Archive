---
title: "Gutsy Installer can't detect NTFS WinXP partition"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by slink on 2007-10-29
Hi, 


I can detect my XP partition with the LiveCD:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc97dc97

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5943    47737116    7  HPFS/NTFS
/dev/hda2            5944        9779    30812670   83  Linux
/dev/hda3            9780        9964     1486012+   5  Extended
/dev/hda4            9873        9964      738958+  82  Linux swap / Solaris
/dev/hda5            9780        9872      746959+  82  Linux swap / Solaris



ubuntu@ubuntu:~$ sudo cat /etc/fstab 
unionfs   /    unionfs rw           0 0
tmpfs     /tmp tmpfs   nosuid,nodev 0 0
/dev/hda4 swap swap    defaults     0 0
/dev/hda5 swap swap    defaults     0 0
```

I can mount it:

[XP.jpg]("http://bp2.blogger.com/_80ytoCMo2uc/RyXx6XkGJLI/AAAAAAAACvI/b-pjlDQ479c/s1600-h/xp.jpg")


But at Install time I got this message when manual installing:

[guided.jpg]("http://bp3.blogger.com/_80ytoCMo2uc/RyX2AnkGJMI/AAAAAAAACvQ/gOCWPfn9bEM/s1600-h/1guided.jpg")

```
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 IDE1 master (hda)

The following partitions are going to be formatted:
 partition #1 of IDE1 master (hda) as ext3
 partition #5 of IDE1 master (hda) as swap
```


If I try manual partitioning:

[manual.jpg]("http://bp0.blogger.com/_80ytoCMo2uc/RyX2F3kGJNI/AAAAAAAACvY/eT8d9Evdk5o/s1600-h/5manual.jpg")


So I understand that the LiveCD recognizes the partitions but the Installer does not. What should I do ?

---

### Post by caricc on 2007-10-29
Just some more info is needed. Is this an update of ubuntu or are you installing for the first time? If it's an update, then use the update manager to load. If it's a first time then in windows you will need to get all of the files to the front of the drive. Disk defrag will work but have patience. It will take some time. I use DIRMS from the ubcd. It has an option that will move files to the front of the drive. 
Once that is completed then you can use the livecd to load ubuntu. Just choose the option in the disk space to use the largest available unused space. (hence the need to move ALL files to the front of the drive). If you want a dual boot. If you only want ubuntu then tell it to use the whole drive. 
with a dual boot to be able to see windows you will need to get the ntfs3g files.  You can do a search here on the board to get the install instructions. 

enjoy.

---

