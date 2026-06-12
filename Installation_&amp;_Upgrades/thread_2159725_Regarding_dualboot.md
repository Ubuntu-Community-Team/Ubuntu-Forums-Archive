---
title: "Regarding dualboot"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by silv3rm00n on 2013-07-04
Hi

On a fresh hard disk, can I first install ubuntu on primary partition and then install windows on a logical partition?
How should I go about it. Installing windows would erase the boot record.

regards
silver

---

### Post by JRV on 2013-07-04
You need to install Windows first.
Then installing Ubuntu will overwrite the Master Boot Record and point it to grub.
Grub is the boot loader, It will give you the option to choose operating systems.

If you are using Windows 8 there might be problems with UEFI.

Search the forum to learn of any other possible problems.
My Windows experience ended with XP.

---

### Post by grahammechanical on 2013-07-04
See this recent post on what would happen if Windows is installed after Ubuntu.

[http://ubuntuforums.org/showthread.php?t=2159718](http://ubuntuforums.org/showthread.php?t=2159718)

To be fair, Ubuntu does the same thing to a Windows install but at least Grub is willing to put a Windows install into its boot menu. Microsoft makes no attempt to recognise any other installation except Microsoft OS.

Regards.

---

### Post by silv3rm00n on 2013-07-08
> **grahammechanical said:**
> See this recent post on what would happen if Windows is installed after Ubuntu.

[http://ubuntuforums.org/showthread.php?t=2159718](http://ubuntuforums.org/showthread.php?t=2159718)

To be fair, Ubuntu does the same thing to a Windows install but at least Grub is willing to put a Windows install into its boot menu. Microsoft makes no attempt to recognise any other installation except Microsoft OS.

Regards.

Most probably grub would get overwritten, however it should be possible to restore grub later on.

---

### Post by oldfred on 2013-07-09
Windows has to boot from a primary partition formatted NTFS with the boot flag or active partition in Windows. So if you attempt to install to a logical partition you still need another Windows Boot partition that is primary.

---

