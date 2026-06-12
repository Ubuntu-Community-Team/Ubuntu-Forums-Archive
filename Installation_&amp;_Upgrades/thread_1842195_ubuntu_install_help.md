---
title: "ubuntu install help"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by dsbig on 2011-09-10
alright so I spent friday night trying to install ubuntu on my computer
intel i7 3.9
8gb memory
3 drives
I have 3 drives, 1tb for backup, 1tb for game and software and 1 250gb for windows.

the 250gb is partitioned, one part for windows and windows recovery, and I used windows to partition 80gb for ubuntu.

I ran the 64bit ubuntu live cd, it go to the part where it says preparing to install, I click forward and it just hung there, nothing happend. tried different times. 

I switch over to the text installer version, and it went to show the drives, but first said it detected that I was running raid, but Im not running raid, I have the bios configured as achi. and after that it was showing the other drive and the 250gb drive but not the partitions. so after that I disconnected the other drives and restart the setup up. it ran installed and then rebooted and went to start, read error.......I had to use my windows cd to recover the boot back into windows.

I also retried the live cd and got the same read error at boot. 

I also tried partition one of the other drives and got the same error.

I made sure that / is entered for mounting.

I even tried partitioning one of the other drives and still had to same problem.

in the frustration windows delete the partition on the drive that held my game and software. but I was able to do a full recovery of the partition.

I want to put it on the 250gb drive with windows, but only way it looks like it will work is if I do a full format first. and then  reinstall both systems.

I tried using wubi, but not matter what I do it keeps saying it cant find the *iso file on reboot. and it the *iso is there.

anyway to fix the problem without the format?

---

### Post by Rubi1200 on 2011-09-11
Hi and welcome to the forums :-)

The fact that you are not on RAID does not mean that the drive was not once part of a RAID array and there is a chance old metadata is still there.

Boot with a LiveCD and run the following command in a terminal:

```
sudo dmraid -E -r /dev/sdx
```

(where x is replaced by the actual drive e.g. sda, sdb, sdc, etc.)

If this tells you there is metadata, then remove it and try the installation again.

---

### Post by dsbig on 2011-09-11
that did help some, but installer is only showing the drive and not the partitions.

---

### Post by Rubi1200 on 2011-09-11
Next step is to post the results of the [Boot info script]("http://bootinfoscript.sourceforge.net/")

---

### Post by dsbig on 2011-09-12
well I gave up and went ahead and told ubuntu to delete the drive with windows on it

I noticed that gparted and fdisk was complaining  that the drive was GTP instead of mbr, and I think maybe thats what was causing the pain. anyway I went and use Parted to erase the GTP and wrote the msdos and then went and uses gparted to partition the drive and then install windows and installed ubuntu. 

now I have ubuntu and windows running on the 250gb drive. but for some reason even though I told ubuntu to install grub to the 250gb drive , it went and install grub to one of the other drives, now I have to start that drive in order to start both systems.

on another note it took me a while to figure out why my network wasnt working right. turned out to be the realtek driver problem and I read on a different thread  on how to replace the driver with a different one, so now thats working...

---

