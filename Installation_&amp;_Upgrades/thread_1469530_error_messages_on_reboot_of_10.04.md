---
title: "error messages on reboot of 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by DOS Chuck on 2010-05-02
I have been having this problem since upgrading from 9.10 to 10.04. I originally installed 9.10 using wubi (I've never been able to get any variant to install any other way) on a logical partition (105GB) of a 750GB Seagate SATA drive (WinXP-64 is one the primary partition).

The original install of 9.10 got trashed during the upgrade to 10.04 (memtest hung up for about an hour) and now I can't get 9.10 to reinstall. So, again using wubi, I installed 10.04. The installation went smoothly. After installing NVidia proprietory drivers (183, I believe) and rebooting, everything worked fine. Installed NTFS-3G config, set read and write atributes for my 3 HD's, rebooted, everything fine.

After installing a couple of other apps (nothing that should have effected the system, I reboot and get this message after the grub menu:

"Gave up waiting for root device. Possible causes:
-Boot args (cat /proc/cmdline)
 -check rootdelay
 -check root
-missing modules (cat /prov/modules; ls/dev)
Alert! /dev/sdb5 does not exist. Dropping to shell.

BusyBox v1.13.3........etc.
(initramfs)"

If I reboot, sometimes it boots just fine. Half the time I get the above message. Using the recovery kernel, I can boot in the safegrafix mode and MAYBE reboot normally. I never know if it's going to work.

Any ideas? And, yes, I've searched for similar threads and haven't found anything yet.

Thanks in advance.

---

