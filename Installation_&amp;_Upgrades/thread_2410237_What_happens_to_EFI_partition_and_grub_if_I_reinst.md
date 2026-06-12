---
title: "What happens to EFI partition and grub if I reinstall?"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by psklenar on 2019-01-12
Going to set up a dual boot.  Currently have Win10 boot from an SSD (with personal data on another).  I have 2 more SSD's to set up Linux on (one to boot from and one for personal data).

Based on multiple "guides" I've found, the recommendation seems to be to disconnect the Win10 drives and install Linux with it's own /efi and / on the boot drive and /home on the 2nd drive.  Then to plug the Win10 drives back in and refresh grub.  Thus the Win10 EFI partition won't be touched and will be distinct from the Linux one.

Okay.  Makes sense.  But ...

What if I decide I want to try a different distribution (say I start with Ubuntu but then decide to switch to Kubuntu)?  Do I need to disconnect the Win10 drives again?  Will the new install wipe out the first distribution's /efi & grub (I know my /home on the other drive will be fine)?  Will it mess with the Win10 EFI partition if I don't disconnect it?  Or will it be smart enough to re-use the EFI partition on the Linux drive?  Or ... ?

Thank you for any guidance!
pat----

---

### Post by oldfred on 2019-01-12
I do not have Windows, but do have multiple installs of Ubuntu on sdb & full installs to external flash drives.
And main working install is on sda.

Every test install of Ubuntu to sdb or flash drive, over writes my /EFI/ubuntu on sda's ESP.
I just tried 19.04 to see if grub was fixed. I changed install location (which has never worked), unmounted sda's ESP and mounted sdb's ESP, and during install it even said installing grub to sdb. But it overwrote my main working install's /EFI/ubuntu. It really is only /EFI/ubuntu/grub.cfg, which is a 3 line configfile to the full grub.cfg in the full install. So now I just edit that back. But I have full backup of ESP.

They have added the install of /EFI/Boot/bootx64.efi, but not sure exactly what file that is. We used to have to manually create that on external drives or as the fallback boot on internal drives. A few systems only boot the fallback entry.

       Ubuntu Installer uses wrong bootloader location for USB UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)
EFI doesn't show multiple installs of the same operating system 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712)
Debian has option to install grub to bootx64.efi
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662)
grub-efi-amd64  grub2/force_efi_extra_removable boolean true

For newer users often easier to disconnect a drive. Many new UEFI systems will let you turn off a drive in UEFI, so you do not have to open case to unplug it.
But UEFI can forget UEFI boot entries if a drive is unplugged. Many auto find Windows, but none auto find Ubuntu. So then you have to use efibootmgr to add new entry.
If knowledgeable on partitions, and willing to copy files from one ESP to another, the alternative is to just let it install to the Windows drive's ESP. You can then manually create boot entry or use Boot-Repair to reinstall grub as it will use the --force parameter (which the installer should be using).

I do like to have a small or test install of Ubuntu on every drive. And then an ESP on every drive configured to boot. 
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

---

### Post by psklenar on 2019-01-13
**oldfred**,

Thank you *very* much for a detailed and helpful response.  and a huge thank you for the link to the UEFI Tutorial!!  I'd missed that in my searches. <blush>

***pat----***

---

