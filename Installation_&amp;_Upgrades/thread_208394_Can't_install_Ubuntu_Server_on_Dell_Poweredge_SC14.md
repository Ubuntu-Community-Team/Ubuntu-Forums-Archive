---
title: "Can't install Ubuntu Server on Dell Poweredge SC1425"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by dorqus on 2006-07-03
So I'm trying to install 6.06 Server on a Dell SC1425 with dual 80GB SATA drives.  I've installed Ubuntu plenty of other times, so it's not for lack of being unfamiliar with the installer.

If I just use non-raid filesystems (ext3, reiser, etc.) it works fine.
However, I'm trying to setup RAID-1 between both drives for /, /home, /usr, /var with no luck.   I partition the disks, then it seems to have initializing the RAID sets.  I've tried this with the BIOS in non-RAID (ATA) mode, and RAID mode, but neither one seems to matter.
File system layout is 2gb for / (primary), 512mb for /boot (primary), 2gb for swap (logical) on each drive (not raid), 8gb (logical) for /usr, 10gb (logical) for /home, and the rest (logical) for /var.

If I'm missing something obvious and you could point me to it, that would be great.  I know the hardware is OK, because I can install OpenBSD on it and use software RAID on it with no problems.

Thanks

---

### Post by lars_p_fink on 2006-09-21
Hi,

We're thinking of buying the same model.

Did you manage to successfully install the raid with ubuntu? If so, how did you do it?

Best regards,
Lars Persson Fink

---

