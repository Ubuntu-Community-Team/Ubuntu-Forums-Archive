---
title: "dual boot ubuntu and windows 8 on Sony"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by rnazareno on 2013-03-21
i've problem like that but in a VAIO Ultrabook with Hybrid
I chat 4 o 5 hs with the tech service but they didnt help.

I disable the RST(the bios doesnt have UEFI to disable)
when it boots and I should choose the partition an error occurs and said i should install drivers
this occurs for W7, Kubuntu, Ubuntu and debian OS

if anyone can help me i would be very thankful

Roberto

p/s: sorry by my english

---

### Post by oldfred on 2013-03-21
Moved to your own thread. Boot issues are almost always unique.

Did you also remove the RAID meta-data from the drives?
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
      
 ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by rnazareno on 2013-03-26
I've read those links but no one was helpful. I'll try to snip some pictures of the process so you can tell me if i'm doing something wrong.

---

### Post by oldfred on 2013-03-26
Are you using the 64 bit versions that support secure boot? Windows 7 will not support secure boot, but may work with secure boot off.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

