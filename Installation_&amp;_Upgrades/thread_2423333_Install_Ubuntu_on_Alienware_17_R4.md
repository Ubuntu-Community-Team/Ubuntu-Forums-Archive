---
title: "Install Ubuntu on Alienware 17 R4"
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by nikkoz on 2019-07-21
[COLOR=#000000][FONT=Roboto]I installed Ubuntu 18.04 on Alienware 17 R4. After the installation, I got an offer to restart the system. I clicked restart and nothing happened. And after force reboot of the system, Ubuntu can't boot. What's the problem?
I used instruction: [/FONT][/COLOR][https://github.com/stormhart/dev-journal/wiki/Alienware-17-R4:-Dual-Boot-Windows-10---Ubuntu-16.04](https://github.com/stormhart/dev-journal/wiki/Alienware-17-R4:-Dual-Boot-Windows-10---Ubuntu-16.04)[COLOR=#000000][FONT=Roboto]
Characteristics: [/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Roboto]Intel Core i7 7700HQ 2800 MHz [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Roboto]16Gb[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Roboto]NVIDIA GeForce GTX 1070 [/FONT][/COLOR]
[*][COLOR=#000000][FONT=Roboto]256Gb SSD[/FONT][/COLOR]
[/LIST]

---

### Post by oldfred on 2019-07-21
Have you updated UEFI and SSD firmware?

You may need nomodeset. Some versions of Ubuntu now will install nVidia driver when you check include proprietary drivers.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Older Alienware threads, but some Dell threads may apply.
       
 Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)
Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

### Post by Dennis N on 2019-07-21
```
Characteristics:

    Intel Core i7 7700HQ 2800 MHz
    16Gb
    NVIDIA GeForce GTX 1070
    256Gb SSD

```
The instructions you refer to are for two separate SSDs, one with Windows. Is that what you have? (you indicate only a 256 gB SSD under "Characteristics"). And 16 gB is amount of RAM? 
The linked instructions, if followed, result in an msdos partition table (the preselected default). If you are using a UEFI computer, you want GPT instead of msdos. Then you will need different instructions, since there are no logical partitions with GPT, and UEFI requires an EFI system partition (not mentioned in those instructions).  

This may help:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

