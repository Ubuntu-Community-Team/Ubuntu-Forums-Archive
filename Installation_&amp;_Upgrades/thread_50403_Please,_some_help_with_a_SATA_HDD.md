---
title: "Please, some help with a SATA HDD"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by gloomygod on 2005-07-20
hi all. I'm trying to install ubuntu in a SATA hdd.
The installation begins with no issue, but when the time of install the bootloader comes, i got a error like: /sbin/lilo failed with code 1.


I got a SATA drive, configured like:

40 Gb NTFS with XP PRO
40 Gb ReiserFS mounted as /
640 Gb Linux Swap mounted as Swap

The installation copies all the files into the /, but i have no way to install the bootloader on that disk.

I'm trying the lilo, with the default option (/dev/sda) and give the /sbin/lilo failed with code 1.  The GRUB also fails at that point.

If i try to install the lilo to a floppy, when trying to boot from the floppy, the lilo instead of load as normal, says: Invalid geom, or somth like that.

The mobo is a GA-K8NF9 and the chipset and the SATA controller is the NVIDIA Nforce 4.

one thing more: I have tried with the following distros, and all of them give me the same error on the bootloader: Ubuntu (AMD64) Kubuntu(AMD64) Debian Sarge(AMD64)

I'm searching on google, and seems people does not have too many problems with SATA devices, so i'm a little lost.

thanks in advance.

See u

---

### Post by mingus on 2005-07-20
*640 Gb Linux Swap mounted as Swap*

This is a typo, right?  The drive is 80GB total?

There should not be an issue using SATA, the problem is elsewhere.

Try installing grub to floppy.  I would install it with the HowTo in the wiki, which will give you both the Ubuntu menu for normal boot plus the grub shell.  That way you can use explicit grub commands for debugging, rather than just an installation script (grub-install).

One possible issue is that since you installed Ubuntu in one partition, the boot files  may not be inside the 1024 limit.  My understanding is that both grub and lilo now have commands to get around this; in grub I think it is --force-lba when used with the "install" command, you would need to check this.  Oh, before doing that, make sure the device in the BIOS is set to use LBA.  Alternatively, using a separate boot partition inside the limit also works.  And finally, if all else fails, and you've insured the 1024 limit is not an issue, install grub to the /boot or / partition, and then chain-load boot from Windows ntldr.

---

