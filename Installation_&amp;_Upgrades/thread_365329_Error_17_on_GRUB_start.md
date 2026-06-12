---
title: "Error 17 on GRUB start"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Prestwick on 2007-02-19
Hello there, trying to install Ubuntu 6.10 on a:

Athlon 64 X2 4600+
1GB Corsair XMS Ram
DFI Lan Party UT RDX200-CF Motherboard
ATI Radeon x800 GTO2 (modded to an x850)
19" Hanns-G HW191D Widescreen LCD monitor
250GB Hitachi Deathstar HDD (main drive where Windows XP resides)
80gb Maxtor HDD in an external USB caddy. (External drive)

I am trying to install Ubuntu on the80gb Maxtor HDD USB drive. Ubuntu installed grub on the main Hitachi drive.

 It ran fine through GRUB first time and I went to try and fix some display issues with my Widescreen monitor and my ATI card. However, I accidentally cancelled an ubuntu update and restarted Ubuntu.

GRUB would not load on boot, citing "Error 17" so I reinstalled Ubuntu and tried again, only to see the same error message.

I have no clue what is going on here and I am running off of my Ubuntu install CD. Can anyone help me fix this?

---

### Post by logos34 on 2007-02-19
> However, I accidentally cancelled an ubuntu update and restarted Ubuntu.

Ouch.  Sounds like it may have been in the middle of installing the kernel update to grub.

Try starting from the 6.10 livecd and on the start screen select "boot from first hard disk." See if that gets you the grub menu.  Probably won't.

Otherwise go back into the livecd to reinstall grub.
> **sudo grub **
**root (hd1,x)**  (*replace x with your ubuntu / partition #)
**setup (hd0) **  
**quit**

This assumes your maxtor drive is (hd1) and the hitachi (hd0)

Now restart the system.

If that doesn't work, download [SuperGrub]("http://supergrub.forjamari.linex.org/") CD.

---

### Post by Prestwick on 2007-02-20
Thanks! That solved the problem :)

---

