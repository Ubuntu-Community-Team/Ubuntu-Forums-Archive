---
title: "Grub Error 18: computer will not boot up."
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by BBX25Y on 2007-09-19
I installed Edubuntu 7.04 Desktop on my computer today, it has Windows XP Home on it.  The computer was set-up for dual boot menu at start-up during the install.

The computer will not boot up, says: GRUB loading, please wait...
Error 18, and then stops.

Thanks in advance for any help.

---

### Post by Jons_Collasius on 2007-09-19
i solved this problem by installing LILO rather than GRUB. use the alternate install cd.

---

### Post by BBX25Y on 2007-09-19
Thanks for the reply.

This was a download form the site, there is no other CD... anymore idea's, please.

Thank you.

---

### Post by Pumalite on 2007-09-19
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by BBX25Y on 2007-09-19
Thanks, understand now.

Is it possible to remove Edubuntu 7.04 from the hard drive, so I still can boot windows without having to format the hard drive and reinstall windows?

Thanks.

---

### Post by Pumalite on 2007-09-19
Erase Edubuntu with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Then fix XP's mbr. Plug in you installation CD>Hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by maybeway36 on 2007-09-19
There is a box on the download page that says:
> Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

And the FIXMBR thing can also be done from DOS if need be:
```
fdisk /mbr
```

---

