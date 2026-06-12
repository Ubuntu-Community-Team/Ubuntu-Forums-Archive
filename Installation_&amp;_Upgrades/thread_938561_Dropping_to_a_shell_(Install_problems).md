---
title: "Dropping to a shell (Install problems)"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by McFuzzie on 2008-10-05
Hey,

I am new here and to this forum and I am having issues with the installation of Ubuntu. I get this message:

Starting up...
Loading, please wait...
usplash: Setting mode 1600x1200 failed
usplash: Using mode 1280x1024
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/7f374ef3-be4b-4535-81b4-755d55e9a98b does not exist. Dr
opping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

Can you please help me.

---

### Post by lemming465 on 2008-10-11
I infer from your description that you installed linux, but now it won't boot?  From your error messages, either the disk with the root file system isn't accessible, or something reformatted it or damaged it.  Is /boot on a different partition than root?  Because it appears to be getting a kernel and an initial ramdisk.  Are there any other operating systems installed?  How many disks are there? How many partitions?

---

### Post by TurkVU on 2008-10-17
I'm having a similar issue. Have a SATA drive with 2 partitions on it, on the first I installed Vista. When I tried to install Ubuntu it wouldn't recognize the free space, so I had to go into the BIOS and change the access type to LBA for the drive. This fixed it enough for the install CD to complete the install...however...

Now when I try to boot into ubuntu I get a similar error message to the one above (only with a different file name).

Any ideas?

---

### Post by lemming465 on 2008-10-17
the UUID is different on every PC, partition, and mke2fs, so yours would be different, yes.

Boot a live CD and include the output of ```
sudo fdisk -l;
```

---

### Post by TurkVU on 2008-10-17
Looks like I got it working. I used the info in this thread:

[http://ubuntuforums.org/showthread.php?p=4809508#post4809508](http://ubuntuforums.org/showthread.php?p=4809508#post4809508)

And updated my boot parameters with what is in post #61.

---

