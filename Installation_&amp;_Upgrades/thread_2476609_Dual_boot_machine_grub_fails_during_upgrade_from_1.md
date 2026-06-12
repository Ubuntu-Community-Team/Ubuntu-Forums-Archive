---
title: "Dual boot machine: grub fails during upgrade from 18.04 to 20.04"
date: 2022-06-30
forum: Installation &amp; Upgrades
---

### Post by dtset2 on 2022-06-30
The upgrade process successfully created the Focal Foss desktop. But after prompted to reboot, grub produced an error. (Tried a cold boot: same issue. Tried advanced reboot: same issue when top choice chosen, i.e. 5.4.0-121-generic .) Here's the error in grub:

```
[    2.641286]  sd 6:0:0:0: [sdb] No Caching mode page found
[    2.641294]  sd 6:0:0:0: [sdb] Assuming drive cache: write through
Gave up wainting for root file system device.  Common problems:
 - Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough?)
   - Missing modules (cat  /proc/modules; ls /dev)
ALERT!  /dev/sda6 does not exist. Dropping to a shell!

BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu6.4) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

The last word in parentheses is a command prompt. 

This is an HP Z220 dual boot windows desktop with Win 10 (upgraded from win7, which borked grub back in Nov 2020). 

I started using Ubuntu dual boots back in 2010, and am still a noob. (Maybe I should run Linux in a mini-PC.) 

What's the next step? Mess with BusyBox, whatever that is? Edit the grub file? (If so, how do I locate it and how do I edit it?) Re attempt this with a fresh install via USB? (Not a problem - I backed up all my data.) Try a recovery Linux installation in grub? Something else? I fix grub issues every few years and invariably have no memory of my previous adventure.

---

### Post by grahammechanical on 2022-06-30
When you select Advanced Options for Ubuntu what Linux kernels do you see? My Ubuntu 20.04 is on Linux 5.13. I am guessing that the 5.4 kernel is left over from Ubuntu 18.04. If Grub cannot find the Linux kernel and then we get dropped to a Grub prompt. Ending up with BusyBox is another matter entirely. It indicates that the partition is corrupted.

[https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

[https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

Regards

---

