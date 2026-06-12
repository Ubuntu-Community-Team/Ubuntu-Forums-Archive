---
title: "Potential Installer Bug"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Jcw87 on 2008-01-07
I wanted to install Ubuntu Server to a USB flash drive so I can try it out without changing anything on my HD. Installation went fine, till the point where GRUB was installed. It asked me if I wanted to install GRUB on the first hard drive, and I told it no. I told it to install GRUB to /dev/sdc1 (My hard drives were at /dev/sda and /dev/sdb, and the USB drive was at /dev/sdc). After the install finished, I restarted my computer to find that my BIOS didn't support booting to USB drives and that the boot sector on the first hard drive had GRUB in it. WTF? My Windows XP partition was rendered unusable untill I ran recovery console and used "fixmbr" and "fixboot"

Why did Ubuntu install GRUB to the first hard drive when I specifically said not to? It's a bug IMO.

To make things worse, it would appear that my BIOS fails at starting GRUB from a floppy or the erroneous GRUB on the hard drive (GRUB Hard Disk Error every time). It starts GRUB from the install CD just fine though. My BIOS version is actually greater than the most recent available on the ASUS site (mine is P4G8X rev 1007 beta 002, and the most recent is P4G8X rev 1006), so it can't be "upgraded"

---

