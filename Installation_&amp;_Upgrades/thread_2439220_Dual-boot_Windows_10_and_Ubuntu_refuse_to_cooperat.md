---
title: "Dual-boot Windows 10 and Ubuntu refuse to cooperate"
date: 2020-03-24
forum: Installation &amp; Upgrades
---

### Post by perihelion00 on 2020-03-24
I recently bought a HP Spectre x360 and wanted to set up Ubuntu dual-boot. It has not gone well.

I did the usual; turn off secure boot, turned off fast boot, partition close to 100GB for Ubuntu environment. Ubuntu 18.04 iso in USB; installation goes well.

At boot however, grub does not appear. And if I manually navigate to boot menu and select Ubuntu, it will continue to take me to Windows.

I tried boot-repair - unsuccessfully, I suppose. Her complaint is listed in the paste URL below.
[https://paste.ubuntu.com/p/Y2YjkY6GcM/](https://paste.ubuntu.com/p/Y2YjkY6GcM/)

I've tried more than a few workaround; deleting partiion and reinstalling, erasing Windows OS and make Ubuntu the default. All had ended tragically for different reasons.

---

### Post by yancek on 2020-03-24
Ubuntu has had a site up explaining dual booting with windows 10 for several years, see the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you look at line 45 of the boot  repair output, you will see there is a vfat partition.  That would be the EFI partition and it should have both windows and ubuntu boot files in separate directories/folders.  If you go down further to line 275, you will see and EFI entry for Ubuntu (Boot0001).  This is the entry which needs to be set first in the BIOS to boot Ubuntu.  I don't see a grub.cfg file in boot repair except the one on the install usb. 

I'm not sure what options you have with your HP Spectre.  I have an HP notebook and to access the BIOS firmware, I need to hit the Esc key on boot and will then see  several options.  Using the F9 key will allow you to make a one time change to the boot order, select the hard drive (probably boot windows), select windows or Ubuntu.  To make a change permanent, it would be necessary to use the F10 key and go to System Configuration and then UEFI boot options.  Do you see these same options on your machine?

I'm not sure why your grub.cfg file isn't showing.  It might be because you are using an NVME dirve. You might try mounting partition 6 and 7 to see if there is actually a /boot/grub directory with a grub.cfg file.

---

### Post by perihelion00 on 2020-03-24
> **yancek said:**
> I'm not sure what options you have with your HP Spectre.  I have an HP notebook and to access the BIOS firmware, I need to hit the Esc key on boot and will then see  several options.  Using the F9 key will allow you to make a one time change to the boot order, select the hard drive (probably boot windows), select windows or Ubuntu.  To make a change permanent, it would be necessary to use the F10 key and go to System Configuration and then UEFI boot options.  Do you see these same options on your machine?

The paste url is actually a tad outdated - I have already changed boot order in both the BIOS settings and from the cmd such that Ubuntu ranks higher; still took me to Windows.

> **yancek said:**
> [COLOR=#000000]Ubuntu has had a site up explaining dual booting with windows 10 for several years, see the link below.[/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Cool, thanks for the link. Let me try to scrap what I can from it.

---

### Post by oldfred on 2020-03-24
Many with HP have had to update UEFI and if SSD, the firmware for the SSD.

Grub uses efibootmgr to set boot order, but many with HP have said efibootmgr does not work, but after UEFI update resetting boot order in UEFI does work. It also may be BCD setting in Windows as it can do a sync between UEFI & BCD.

HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)

---

### Post by perihelion00 on 2020-03-25
> **oldfred said:**
> Many with HP have had to update UEFI and if SSD, the firmware for the SSD.

Grub uses efibootmgr to set boot order, but many with HP have said efibootmgr does not work, but after UEFI update resetting boot order in UEFI does work. It also may be BCD setting in Windows as it can do a sync between UEFI & BCD.

HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)

Updating the BIOS/UEFI to F.20 did the trick. Restarted to live USB Linux and ran boot-repair - successfully installed the grub.

Thanks for the help!

---

