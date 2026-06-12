---
title: "Seeking Help with Lubuntu install on a dell inspiron 3452"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by ramanterola on 2018-06-04
Hi!   Noob here

Can someone provide me with a step by step installation of Lubuntu on a inspiron 3452? Once I install Lubuntu, it goes into a GRUB2 install, and it finishes successfully.   When I take the USB stick out and reboot the computer, the computer cannot find a bootable device.   I have read as much as UEFI as I can, but I cannot figure this install.

Thank you in advance for your time and assistance.

R

---

### Post by oldfred on 2018-06-04
Lets see where you are at:
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Have you updated UEFI/BIOS from Dell?
Is drive set for AHCI, not RAID nor IDE, nor some Intel SRT or similar.

Even some Intel chips seem to need nomodeset. You could just try it as you boot. If UEFI, you may have to press escape to get grub menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ramanterola on 2018-06-09
Thank you for the reply Oldfred!  This machine has the eMMC and it takes patience.  At the end, I reset the BIOS to factory settings, and tried one more time .... and it works.   I cannot tell you what the difference is/was but it works.
I am happy to be using open source, I need to tweak it a little bit so it is a little bit easier to use.  Minor stuff, like the touchpad is hyper sensitive and it has taken my cursor away from the place where im typing a couple of times while typing this reply.  
Again thank you for your assistance.
R

---

