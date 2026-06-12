---
title: "can't install Ubuntu, can't install winxp"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by twede on 2006-07-15
I am absolutely niew hier and I don't know much about Linux. Today I've tried to install Ubuntu and it seems that I have really messed up my hard disk. Now winxp is dead and I can't install neither of the two... 

The idea was to create a double-boot with winxp. I've downloaded the CD, checked the checksum, booted into Ubuntu: everything fine except the sound (no sound), but I've decided to install anyway. Right away I can't partion -I get a message saying that NTFS can't be edited. So I download the Ubuntu System Rescue and try with qtparted, still can't partition.

Defrag a few times, chkdsk, and then IT SEEMS that the partitions are created but instead I end up with a useless big partition where I can't install anything at all. Windows won't install and the Ubuntu setup can't read my hard disk. Since I get all sorts of messages about bad blocks (when trying to install an old copy of win98 ), i try Chkdsk, that doesn't start and fdisk that gives a fatal error.

Please help....

---

### Post by gerbman on 2006-07-15
> **twede said:**
> I am absolutely niew hier and I don't know much about Linux. Today I've tried to install Ubuntu and it seems that I have really messed up my hard disk. Now winxp is dead and I can't install neither of the two... 

The idea was to create a double-boot with winxp. I've downloaded the CD, checked the checksum, booted into Ubuntu: everything fine except the sound (no sound), but I've decided to install anyway. Right away I can't partion -I get a message saying that NTFS can't be edited. So I download the Ubuntu System Rescue and try with qtparted, still can't partition.

Defrag a few times, chkdsk, and then IT SEEMS that the partitions are created but instead I end up with a useless big partition where I can't install anything at all. Windows won't install and the Ubuntu setup can't read my hard disk. Since I get all sorts of messages about bad blocks (when trying to install an old copy of win98 ), i try Chkdsk, that doesn't start and fdisk that gives a fatal error.

Please help....At this point it might be best to wipe the entire drive and start over. I would recommend installing Windows 2000 or XP by itself, making sure to leave 5-10GB of free space for the Ubuntu installation. Next, install Ubuntu. Read the following pages for info on dual-boot systems and partition setup:

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

I'm afraid I don't have any suggestions if you don't want to wipe the drive. :-k

---

### Post by twede on 2006-07-15
Hi Gerbman, thanks for your answer

At this stage I don't have any problem with wiping the whole drive, but I can't...  with the windows setup I can do absolutely nothing, it doesn't let me delete the partition or install anything. It says that it can't access the partition.
All I get is a window saying that windows is being shut down in order to prevent damage (!)

---

### Post by gerbman on 2006-07-15
> **twede said:**
> with the windows setup I can do absolutely nothing, it doesn't let me delete the partition or install anything. It says that it can't access the partition.
All I get is a window saying that windows is being shut down in order to prevent damage (!)Oh...and this happens after booting into the setup CD for Windows? If that's the case, then I'm really stumped.

---

### Post by twede on 2006-07-15
:(    I guess I need a new hard disk....

---

### Post by mbrang00 on 2006-07-23
That would be my guess...this may sound silly, but make sure the power and data cables are secure on the disk and on the MOBO.

---

### Post by tseliot on 2006-07-23
You can also check the RAM (I had a similar problem). Try leaving only 1 stick of memory per time

---

### Post by Sef on 2006-07-23
This is an excellent tutorial on [How to Dual Boot.]("http://users.bigpond.net.au/hermanzone/")

---

