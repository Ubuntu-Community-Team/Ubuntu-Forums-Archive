---
title: "Fiesty on external usb"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by yeleek on 2007-04-21
Hi,

This morning i thought i'd try to install fiesty to an external usb.  Just to be safe removed power connection from internal sata disk.  Booted off CD with external usb connected and installed to the USB drive as if it were internal disk.  I got some strange errors, and presumed it hadn't worked.  Rebooted however and with no cd, and no power connection to internal hdd fiesty is up and running (writing this now via it).

What checks if any can i perform to make sure this installation is complete and valid?

Thanks

---

### Post by yeleek on 2007-04-21
Actually let me 'alter' my first statement.

The install is working, if you boot off the ubuntu cd.  And tell that first menu to boot from the first hard disk (then remove the cd).

If i remove the cd altogether and reboot getting grub error 18.

Any thoughts?  Or am i better scrapping this install and trying via alternative means?
[I]
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.[/I]

Thanks

---

### Post by yeleek on 2007-04-21
Anyone??  Please.

I think i have to start again with different sized partitions but am new to this so what should i setup?

Its a 40gb external disk, and the machine has 2gb of ram.  The whole disk can be for ubuntu...

But not sure what partitions or types to configure when doing a manual install.

Thanks

---

