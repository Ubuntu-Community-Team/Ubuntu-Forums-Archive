---
title: "Ubuntu 9.10 Grub 2 frustrations"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by skern03 on 2009-12-25
And yes, I've read countless posts, tried several fixes, including the excellent posting by drs305 on Grub 2 Basics, read through the tutorial on the Ubuntu Community and followed the steps to reinstall Grub 2.... Still can't get it working. Had to unplug (literally) my SATA drive just to boot into XP to post this. 

System: 
Primary drive: 40 GB IDE Western digital, XP only
Secondary drive: 250 GB SATA, Linux only. 20 GB /(root); 2 GB swap, rest /Home.
This system worked fine in all previous releases, up to and including 8.10, sucked in 9.04 (backed it out), but still booted.

After upgrading to 9.10, I cannot boot. I get "file not found" and one of two prompts: grub rescue> or sh:grub. I've tried the solutions posted in the above mentioned Grub 2 Basics, but cannot get Ubuntu to boot.

I have reinstalled five or six times, selecting the Advanced on the last tab, choosing the following:
(hd0) - the default
/dev/sdb - where linux lives
with no difference.
Note: I always reformat the root partition.

On two occasions, the install acted flaky: once, it said there was a problem with the disk after several installs with no failures. I ran disk check, and it performed flawlessly. The other time, the screen flashed on the orange/yellow boot graphic repeatedly, alternately displaying the text of the "real install."

Any other info you need to troubleshoot, please let me know and I'll post. I'm stumped. For now, I'm stuck with Windoze. :confused:

fdisk -l shows both sda1 AND sdb1 as bootable. Here's the output of fdisk -l:

```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dc00dbf

    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000569a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2490    20000893+  83  Linux
/dev/sdb2            2491        2739     2000092+  82  Linux swap / Solaris
/dev/sdb3            2740       30401   222195015   83  Linux

```

Thanks a million in advance for all your help and support over the years!

---

### Post by skern03 on 2009-12-25
So here's how I fixed it:
Burned the CD at 1/2 speed (24x)
Ran the live CD
Ran Terminal and mounted the linux partition
From drs305's grub 2 basics how-to [HTML]http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics+drs305[/HTML], ran these commands:
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
(in my system, sdX = sdb; sdXY = sdb1)

```
Rebooted and reinstalled.
This time, I did not format sdb1.
After reboot, the boot menu appeared!

Now if they fixed the hassles with ipv6 and ALSA, I'll be a happy camper....

---

