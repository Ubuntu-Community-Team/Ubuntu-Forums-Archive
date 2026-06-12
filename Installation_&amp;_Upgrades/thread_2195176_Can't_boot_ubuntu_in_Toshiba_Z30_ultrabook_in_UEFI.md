---
title: "Can't boot ubuntu in Toshiba Z30 ultrabook in UEFI mode."
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by robertozoco on 2013-12-22
Hi, i'm having some problems when I try to remove windows8 and install Ubuntu,

This are the step I follow.
 
Disable securebot and fast boot.,
Remove al partition of the SSD. There is only one ssd disc, so no RAID.
Install ubuntu 13.10 from a live CD, I checked and ubuntu creates the swap and UEFI partitions.  
 
Where I restart it, the error mesage is > Insert system disk in drive. 

So the grub does't start and in the bios I can only configure the order boot drives (ssd, usb or lan).

After, I follow the steps from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and I try to repair the loader, but doesn't work. 
 
The result is in> [http://paste.ubuntu.com/6619942/](http://paste.ubuntu.com/6619942/)

I try many other things and nothing works. Always the same message. Any idea?

---

### Post by oldfred on 2013-12-22
It looks like you installed Ubuntu with secure boot on, or have used Boot-Repair to reinstall grub & kernels with secure boot on. It should boot.

But with one install, you will not see grub menu and then may be into issues with video or needing other boot parameters.

From UEFI/BIOS can you hold shift key or with some UEFI hit escape key and get grub menu?

You can try recovery mode. Or try adding boot paramaters. With your Intel i915, nomodeset does not usually work and you need different parameters. See instructions on nomodeset on how to add to grub.
Basically at grub menu use e for edit, scroll to linux line and replace quiet splash with your boot parameters. See below what worked for another Toshiba.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed [COLOR=#ff0000]acpi_osi=Linux acpi_backlight=vendor[/COLOR]
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

