---
title: "Can't install Ubuntu"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by Sami_Mattila on 2017-06-14
&#8220;Unable to install GRUB in /dev/sda&#8221; still plagues Ubuntu and it's derivatives preventing installation on UEFI hardware.
I would think somebody caress about this?
Disabling UEFI on  BIOS did nothing and I tried on 2 different Ubuntu flavors. Eventually I had to manually partition the hard drive to be able to setup Ubuntu.
Why can't Ubuntu setup add the needed FAT partition automatically (if needed) and why does GRUB installar ALWAYS crash during the setup?
The option to continue without GRUB setup never works.

Disappointing.

---

### Post by NoWayWin8 on 2017-06-14
Is this a dual-boot machine with Windows on it? If so, dev/sda is the WinRE partition and the EFI partition is located at dev/sdb.

---

### Post by slickymaster on 2017-06-14
*Thread moved to **Installation & Upgrades**.*

---

### Post by sccman on 2017-06-15
The first thing I would check (on another Ubuntu, Windows, or other OS computer) is how much space is available on the drive you want to install Ubuntu to.

---

