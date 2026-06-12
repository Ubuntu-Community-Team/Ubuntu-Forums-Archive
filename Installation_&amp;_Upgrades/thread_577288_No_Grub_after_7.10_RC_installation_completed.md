---
title: "No Grub after 7.10 RC installation completed"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by ups on 2007-10-16
Hi,

I have an Acer Aspire 4520 laptop (AMD Athlon 64 X2), and installed Ubuntu 7.10 RC on the 160 GB hard disk which has Windows XP on the first 20GB partition.

The installation from the LiveCD went successfully (no error messages), but when I rebooted there were no changes to the MBR - the system just went into Windows XP as usual. There was no sign of Grub during boot.

During installation, only thing I noticed weird was that my Parallel hard drive was named sdaX. On the Advanced options during installation, it showed bootloader would be installed on hd0.

(There are threads/bugs saying IDE drives are being recognized as SCSI, but it seems that's just the way it is being named nowadays).

Anyone has any clues as to what may be wrong?

Thanks!

---

### Post by logos34 on 2007-10-16
Ubuntu since 7.04 Feisty uses the libata driver, which recognizes ide drives as scsi.

Reinstall Grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If grub still doesn't appear, check this:

[http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect](http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect)

---

### Post by ups on 2007-10-16
I'll try re-installing grub once I reach home.

Haven't checked for the MBR write-protect possibility, so will keep that in mind too. Thanks for pointing out!

---

### Post by ups on 2007-10-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/135149](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/135149) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Turns out the installation hadn't completed successfully afterall. It was due to [bug 135149]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/135149"). I've added my comment to the bug.

The quick solution is to click on the "Continue" button on the migration assistant window if it fails to mount the source partition (from where some application's migration is being done).

---

