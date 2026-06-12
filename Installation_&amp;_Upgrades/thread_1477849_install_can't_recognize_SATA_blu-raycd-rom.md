---
title: "install can't recognize SATA blu-ray/cd-rom"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by gilbert_u on 2010-05-09
I try to install 64-bit desktop and can get far enough for the kernel to load and to the point it tries to mount the installation CD.  Then it quits with a BusyBox ash shell complaining not being able to find any "medium".

I have two SATA harddrives, one each attached to /dev/sda and /dev/sdb and those seem fine.  But "cat /dev/sdc" (where the cdrom drive is) says "no medium found".

I also tried the alternate desktop CD and it also complaints not being to find the cd-rom during the installation process, and asks me if I have any module/driver I can load.

I have an HP Pavillion Elite desktop with a Blu-Ray/cd-rom player.  Is the drive too new to be compatible with Linux?  Is there a way to force installation to see it as a simple cd-rom drive?  If not, anyone knows of any place to get a driver module?  I searched hard in Google and couldn't find any so far.

Thanks!

---

### Post by gilbert_u on 2010-05-09
by the way, an old 9.04 32-bit CD seems to work and mounts the blu-ray drive as /dev/sr0 and /dev/scd0 (one is a link to the other).  So it is puzzling why this doesn't work with 10.04.

I guess I could potentially try to install 9.04, and then upgrade to 9.10, and then upgrade to 10.04 to avoid this issue, but it sounds like a pain...

---

### Post by davidmohammed on 2010-05-09
try examining your bios  - see if you can switch your cdrom drive from SATA to ide-emulation.  That should be enough to get your installation to work.

Once installed, you can reverse and then see if a later kernel will help.

---

### Post by gilbert_u on 2010-05-10
Thanks David but "IDE mode" for the SATA controller doesn't help (the only relevant thing I can change in BIOS)

turns out that the key was 32-bit.  the 10.04 i386 CD mounts the cd-rom fine, but not the amd64.

This is also the case with 9.04.

---

### Post by green slime on 2010-06-27
I too, have this problem. Most irritating.

---

### Post by nyteryder79 on 2010-10-28
Same HP Elite, same exact problem.  Very annoying.  I managed to install 10.10 x64 using a USB flash drive, but when Ubuntu boots to the desktop, the blu-ray drive isn't detected and won't even power on.  Yes!  That's right!  When booting Ubuntu 10.10 AMD64, the blu-ray drive looses all power.  Not to mention it won't shutdown properly and hangs on shutdown and when rebooting, the BIOS freezes up.  I have to force shutdown when the BIOS freezes, then force power-on.  Only then after a brief freeze with GRUB, does the PC boot to the Ubuntu logon screen.  I'm not sure who to blame here...  Bad BIOS from HP, or the supposed blu-ray support in the new Ubuntu 10.10.  Very annoying.

[Edit]
I disabled the port in BIOS that the blu-ray drive is installed to and I no longer have any issues.  I noticed dmesg error for ata3 that was the cause of my issue.  Turns out it's related to SATA_PMP or SATA Port Multiplier.  The only way to fix it is to recompile the kernel with sata_pmp=n option.  I'm not about to do that.  I'll just disable it until the next kernel update and boot into Windows if I need to burn or use the drive at all.  Hopefully by then I'll see a fix.  These days with flash drives I rarely used the blu-ray drive anyway.

---

