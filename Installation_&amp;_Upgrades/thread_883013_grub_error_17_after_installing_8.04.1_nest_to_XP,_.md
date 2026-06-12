---
title: "grub error 17 after installing 8.04.1 nest to XP, system with RAID 1"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by saul11 on 2008-08-07
**Error when botting:** I finally wanted to make my first Linux steps and wanted to install Ubuntu (8.04.1) next to windows XP. I first tried the standard version, but the installation seemed the stop somewhere (tried twice), so I tried the 64bit version, but that one didn't work either... Finally I tried the 64bit alternative and this one worked, but now when I boot I get the errormessage:

"GRUB loading, please wait
error 17"


**LiveCD:** Furthermore I cannot boot with the liveCD. It always throws me into the busyBox. (the 32bit liveCD as well as the 64bit)


**super grub disk:** as I couldn't boot my PC anymore I downloaded the super grub disk. With this I do get into windows... but when I try to boot Linux I get:
- with the option 'boot GNU/Linux' > 'error 17, cannot mount selected partition'
- with the option 'boot GNU/Linux directly' >
  ...
  * 'ata1 failed to recover some devices, retrying in 5 seconds' (een aantal keren)
  ...
  * 'ata7: SATA link down (SStatus 0 Scontrol 300)'
  * 'ata8: SATA link down (SStatus 0 Scontrol 300)'
and after a pauze:
'Done
check root = bootarg cat /proc/cmsline
or missing modules, devices: cat/proc/modules ls /dev
ALERT! /dev/sdc1 does not exist. Dropping to a shell!'

And then I get the busyBox v1.1.3
(iniramfs)

In which I -as a Linux noob- cannot do anything usefull...



So any help is greatly appreciated!

---

### Post by saul11 on 2008-08-25
No-one? :(

I'm still booting with the grub disk; and am thinking of trying to remove the boot managar and stick with windows unless there's a fix for me...

---

