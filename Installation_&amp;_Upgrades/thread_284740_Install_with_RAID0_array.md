---
title: "Install with RAID0 array"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by cboyd on 2006-10-26
I'm trying to install Ubuntu on a Dell XPS that has an Intel ICH8R SATA RAID controller on it.  Dell created a RAID0 array at the factory using two 320 GB drives and installed Win XP on it.  After I got it, I shrunk the windows partition down and rebooted with the Ubuntu 6.06 live CD.  During the partitioning part of the installation, it sees two hard drives, not one like I would expect.  Why is Ubuntu not seeing the RAID array as one drive?  Do I need to load special drivers at the install so it can see the two drives as one?  I also tried installing Ubuntu 6.10 Release Candidate using the alternate CD since it said something about LVM and RAID partitions, but that didn't seem to help.  Any assistance would be greatly appreciated.

---

### Post by daou on 2006-10-26
Installing Ubuntu on RAID isn't a simple task.
For directions, look here:

[w.ubuntu-in.org/wiki/SATA_RAID_Howto]("w.ubuntu-in.org/wiki/SATA_RAID_Howto")

---

### Post by cboyd on 2006-10-28
I tried using the guide you included in your post but it still didn't work.  I configured my array, installed the dmraid package in Synaptic, and started gParted.  The guide you referenced in your post says that once you start gParted there should be an entry similar to "dev/mapper/nvidia_gahhaaab", depending on your chipset, in the drop-down at the top right.  I don't have anything close to that in the drop-down.  All I have is two entries:

/dev/sda
/dev/sdb

This tells me that it's not seeing the RAID array correctly, but seeing the two individual hard disks.  Do you have any idea on why I'm not seeing the one array?

---

### Post by daou on 2006-10-28
To check if dmraid recognized your RAID array correctly, type the following into terminal:

> ls /dev/mapper

If the folder is empty, dmraid hasn't recognized your RAID. For example, with NVIDIA RAID drivers there should be something like "nvidia_bhddfjde".

---

### Post by cboyd on 2006-10-28
Here is the output:

```

ubuntu@ubuntu:~$ ls /dev/mapper/
control  isw_dgifbgibad_LINUX  isw_dgifbgibad_WINDOWS  isw_dgifbgibad_WINDOWS1

```

Also, I added another post that doesn't show up in this thread for some reason.  Basically what it said was that dmraid does recognize the arrays:

```
ubuntu@ubuntu:~$ sudo dmraid -s
*** Group superset isw_dgifbgibad
--> Active Subset
name   : isw_dgifbgibad_WINDOWS
size   : 125829120
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
--> Active Subset
name   : isw_dgifbgibad_LINUX
size   : 499304448
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
ubuntu@ubuntu:~$ sudo dmraid -tay
isw_dgifbgibad_WINDOWS: 0 125829120 mirror core 2 65536 nosync 2 /dev/sda 0 /dev/sdb 0
isw_dgifbgibad_LINUX: 0 499304448 mirror core 2 2048 nosync 2 /dev/sda 125833216 /dev/sdb 125833216
isw_dgifbgibad_WINDOWS1: 0 125804952 linear /dev/mapper/isw_dgifbgibad_WINDOWS 63

```

As you can see, the arrays are there and dmraid recognizes them.  Just not gParted.  It still only shows the two separate drives.  However, I went ahead and started the install process from within the Live cd, and when it got to the point where it asks you to partition the drives, it DID show the two arrays isw_dgifbgibad_WINDOWS and isw_dgifbgibad_LINUX (see Screenshot-install1.png).  I selected the option to let Ubuntu format the drives to the default, but when the installer went to mount the array to install the system, it failed (see Screenshot-install2.png).  I'm going to try to manually partition each drive that is part of the array exactly the same (I'm using RAID1 now) and see if the installer will work then.  I'm starting to run out of ideas.  Any more help you could give would be appreciated.

---

### Post by cboyd on 2006-10-30
I found a GREAT how-to that has helped me a lot ([https://help.ubuntu.com/community/FakeRaidHowto)](https://help.ubuntu.com/community/FakeRaidHowto)).  I am almost there!  However, now I am stuck trying to configure Grub.  I followed the instructions in the how-to, but when configuring Grub I get an error.  From the Grub console:

```

device (hd0) /dev/mapper/isw_dcbdeabhjb_ARRAY3

root (hd0,2)

setup (hd0)

Error 17: Cannot mount selected partition

```

Here is the output from fdisk:

```

Disk /dev/mapper/isw_dcbdeabhjb_ARRAY: 320.0 GB, 320070483968 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                           Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dcbdeabhjb_ARRAY1               1        7833    62918541    7  HPFS/NTFS
/dev/mapper/isw_dcbdeabhjb_ARRAY2            7834        8332     4008217+  82  Linux swap / Solaris
/dev/mapper/isw_dcbdeabhjb_ARRAY3   *        8333       38913   245641882+  83  Linux

```

I'm so close, but I've hit a wall!  I don't know where to go from here.  I don't understand why I'm getting this error.  Can someone please help?

---

### Post by daou on 2006-10-30
I have that link as well, but I never successfully installed Ubuntu on RAID with it. In fact, I got the same error with GRUB. That's why I gave the other FakeRAID howto, but I haven't had the chance to try it yet myself.

I'm afraid I don't know how to help you any further with the problem.

---

### Post by cboyd on 2006-10-30
OK, thanks for your help daou.  I appreciate your efforts.  Anyone else out there got any ideas?  Also, I wanted to make a correction to my last post.  In the Grub console section of my post, this line:

```

device (hd0) device (hd0) /dev/mapper/isw_dcbdeabhjb_ARRAY3

```

should have read:

```

device (hd0) device (hd0) /dev/mapper/isw_dcbdeabhjb_ARRAY

```

Anyone else that could give me a hand with this problem would be greatly appreciated!

---

### Post by cboyd on 2006-10-30
Sorry!  Copy/paste error in last post.  The correct line should read:

```

device (hd0) /dev/mapper/isw_dcbdeabhjb_ARRAY

```

---

### Post by daou on 2006-10-30
I suspect it has something to do with GRUB not recognizing the RAID array. I have no problem reading from or writing to my RAID array from Ubuntu.

---

