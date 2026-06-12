---
title: "Overwrite Redhat / Fix GRUB in MBR"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by xMore on 2006-09-20
Ok, here's my situation.

Some time ago I installed Redhat Enterprise on it's very own independent hard drive. Windows XP is on it's own drive.

When I initially installed Redhat, I set it up to install GRUB in the MBR on the XP hard drive.

Well, I no longer want Redhat on that hard drive, I want Ubuntu in place of it.

Here's the thing, I've lost my XP cd, so I can't try the recovery console with the fixmbr deal.

The question: When installing Ubuntu, will Ubuntu completely format the Redhat hard drive, AND will it overwrite the GRUB data in the MBR on the XP hard drive?

I'm really not to fond of trying to install it, and the MBR screw up, and I'm at a loss.

Thanks for the help, it's appreciated! ;)

---

### Post by confused57 on 2006-09-20
> **xMore said:**
> Ok, here's my situation.

Some time ago I installed Redhat Enterprise on it's very own independent hard drive. Windows XP is on it's own drive.

When I initially installed Redhat, I set it up to install GRUB in the MBR on the XP hard drive.

Well, I no longer want Redhat on that hard drive, I want Ubuntu in place of it.

Here's the thing, I've lost my XP cd, so I can't try the recovery console with the fixmbr deal.

The question: When installing Ubuntu, will Ubuntu completely format the Redhat hard drive, AND will it overwrite the GRUB data in the MBR on the XP hard drive?

I'm really not to fond of trying to install it, and the MBR screw up, and I'm at a loss.

Thanks for the help, it's appreciated! ;)
Here's a link for repairing the Windows mbr, if you don't have the Windows installation cd:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Which is basically downloading the Win98SE oem boot floppy:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
Then enter fdisk /mbr, as directed in the hermanzone link, to restore your mbr.


Ubuntu "should" overwrite the RedHat grub on the mbr...I'm not familiar with RedHat, so there's no guarantee that it will.

---

