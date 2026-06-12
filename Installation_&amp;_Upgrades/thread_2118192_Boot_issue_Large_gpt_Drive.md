---
title: "Boot issue Large gpt Drive"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by eisioriginal on 2013-02-20
I repaired my system and went from the grub> menu to an information like

error: out of disk
error: could't read file.

press any key to continue...

here is what boot-repair produced

[http://paste.ubuntu.com/1691134/]("http://paste.ubuntu.com/1690947/")

can somebody guide me to the right setup for my problem

---

### Post by oldfred on 2013-02-20
Moved to your own thread.

Welcome to the forums.

You have a very large drive with the default install of just / & swap. Grub seems to have issues finding files and extremely large partitions where files are not close together.

I normally suggest only 25GB for / (root) even with a drive like yours. You then can add partition(s) for /home, data, backup or whatever other uses you might want.

You can quickly test if large partition size is an issue by using gparted to shrink / to less then 100GB. Test if it boots after that. Then you can either add partitions or reinstall.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by eisioriginal on 2013-02-20
Unfortunately this is not an option because there is already more than 1 TB Data present on this partition and it worked until i updated with apt-get upgrade. So i guess there was a configuration with grub that worked before.

---

### Post by oldfred on 2013-02-20
One of the advantages of Linux is that is does not need defragging, but it does that by writing the entire file randomly any where in partition. So files are not normally fragmented. But files can then be written anywhere.

```
=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1
 264.149469376 = 283.628333056  boot/grub/core.img                             1
   0.396192551 = 0.425408512    boot/vmlinuz-3.2.0-26-generic                  1
   0.396192551 = 0.425408512    vmlinuz                                        1
2114.318868637 = 2270.232598528 boot/initrd.img-3.2.0-26-generic               3
```

So it looks like on your update initrd was written nearer the end of the drive at 2270. Perhaps it worked ok as the original install had files close enough together to work.

There used to be a bug, but I thought they said they fixed it. Cannot find it offhand.
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

Since you still have lots of room on drive. I might try shrinking as much as you can, it may work. Or then move data to another partition and shrink some more. Unless you have saving large files like movies, I do not suggest one large partition as if you have errors fsck will take a long time.

---

