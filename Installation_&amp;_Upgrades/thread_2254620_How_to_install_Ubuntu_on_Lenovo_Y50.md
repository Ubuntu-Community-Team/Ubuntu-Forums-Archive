---
title: "How to install Ubuntu on Lenovo Y50?"
date: 2014-11-28
forum: Installation &amp; Upgrades
---

### Post by kaustuv1993 on 2014-11-28
How does one install Ubuntu 14.04 on the Lenovo Y50? The confusion I have is because of the 8GB SSD, I've never had a hybrid HDD-SSD PC before and I am not sure how to install Ubuntu on such a system. It is vital for my work however. Any help would be appreciated
.

---

### Post by yancek on 2014-11-28
Is the link below the notebook you have?  The hardware page shows it has a 500GB drive and comes with windows 7 or windows 8.  Your post only mentions and 8GB SSD, do you not have an internal drive?  You don't mention any operating system on it, did you buy without any operating system?  A full install of Ubuntu uses about 6GBs.  Are you just planning to install to the SSD and not the hard drive?  Can you clarify your situation?

[http://support.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-y-series-laptops/y50-70-notebook-lenovo](http://support.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-y-series-laptops/y50-70-notebook-lenovo)

---

### Post by kaustuv1993 on 2014-11-28
It comes with W8.1 pre-loaded. And while a full install of Ubuntu would take up 6Gigs minimum I also want to partition in a way that I have at least a 100 GB workspace for my ubuntu OS. The HDD on my model is a 1 TB hybrid with an 8GB SSD.

[http://shop.lenovo.com/us/en/laptops/lenovo/y-series/y50/?sb=:000001C9:000120E6:](http://shop.lenovo.com/us/en/laptops/lenovo/y-series/y50/?sb=:000001C9:000120E6:)

---

### Post by oldfred on 2014-11-28
It used to be that the Intel SRT or the boot cache it creates caused huge issues. Now just some issue. :)

Also hybrid computers usually have dual video which also causes issues.

I believe the installer now works with the Intel SRT where before the RAID on the SSD confused it. It may still give issues on installing grub correctly as how grub is installed to RAID is different than a standard partitioned drive. I think you can just turn off the Intel SRT and it will install correctly and then turn it back on to have SRT work again. Many have posted about deleting the RAID meta-data on SSD, but that may not be required now.

Install is like others with UEFI & Windows 8.1. Turn off hibernation or fast boot, turn off secure boot, but also turn off Intel SRT and set to AHCI mode for drives.
Use Windows to shrink the NTFS partition to make room for Ubuntu and reboot immediately so it can run chkdsk and update for its new size.
Then only use Something Else to install Ubuntu. I prefer to partition in advance with gparted as it seems a bit easier, but you still have to use Something else to choose which partition is mounted where.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Not sure if any of these are similar to your model. But UEFI is typically very similar by brand. Options and which cpu brand are the major differences.

 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12

These have SSD:
  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)

---

### Post by kaustuv1993 on 2014-11-28
So essentially all I have to do is create a disk image of the computer, for safety's sake, and then resize my HDD partition. Then I restart and allow the computer to stabilist/use chkdsk to get used to the new partitioning. I then switch off hibernation and SRT and all of that and just install ubuntu as I normally would using the usb? Alongside windows of course...

---

### Post by oldfred on 2014-11-28
Some examples of using Something Else.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Then if sytem starts to boot but you get black screen that is video issue, and you may need boot parameters. And which parameter may depend on which video Intel or nVidia is used to boot with.

---

