---
title: "Install Problems"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by MalcolmSP on 2007-07-31
I am working on a dual boot laptop--currently with Win XP and Fedora 7. I have been having all sorts of problems with this distro, so tried downloading Ubuntu. I have burned the ubuntu 7.04 CD successfully--check sums match on download and on burned copy. I have reset my CMOS to boot from the CD, but it keeps going to the GRUB loader for Fedora. Somewhere I have a copy of ubuntu 6--that worked as a liveCD--would I be better off going to that and upgrading via that route or what?? Open to suggestions.

---

### Post by Pumalite on 2007-07-31
Who owns the Grub? Fedora? You could erase Fedora, repartition ( and erase Fedora) with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), and then install Ubuntu. 256 MB RAM or less> Xubuntu Alternate CD. This would reinstate your Grub to the MBR and would recognize XP. If you want, between installations, you can fix XP's MBR with XP installation CD>Hit 'r' for Recovery>FIXMBR>FIXBOOT.

---

### Post by MalcolmSP on 2007-08-01
> **Pumalite said:**
> Who owns the Grub? Fedora? You could erase Fedora, repartition ( and erase Fedora) with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), and then install Ubuntu. 256 MB RAM or less> Xubuntu Alternate CD. This would reinstate your Grub to the MBR and would recognize XP. If you want, between installations, you can fix XP's MBR with XP installation CD>Hit 'r' for Recovery>FIXMBR>FIXBOOT.

GRUB is owned by Fedora. I am using an ACER TravelMate 4060 and have 512K. I cannot get my CMOS to pick up the ubuntu CD that I have--I have reset the boot sequence to CD then Harddrive--but it keeps going to the Harddrive. I don't see how doing an XP Recover would do anything to fix this issue. My XP is being recognized along with Fedora via GRUB.

---

### Post by Pumalite on 2007-08-01
No, it would not help you. I put it there in case you erased the partition and were left without anything and desperate. Your main problem is BIOS and the boot order. Did you have the problem of not being able to boot from CD before? Sometimes hitting F8 or F12 after POST would bring a different menu. You could try that. Or get an USB drive. Make sure you have a bootable CD. Check iso. Do md5sum. Burn at 4x, check CD for corruption before install, etc.

---

### Post by eggdeng on 2007-08-01
> I have burned the ubuntu 7.04 CD successfully
You burned the image file as ISO, right ?

---

### Post by MalcolmSP on 2007-08-01
I did the checksums and the file is correct. It is an ISO file. I have not had any problems before with booting from a CD--hey, I can try it with some other bootable CDs--new ideas always help. I also have a 1 and a 2 GB USB drive.

---

### Post by Pumalite on 2007-08-01
Double check BIOS, check connections. Did you do md5sum? Compared it to what? Use an USB drive if necessary. Clean the lens in your drive.

---

### Post by MalcolmSP on 2007-08-01
I have triple checked the bios. Can't check connections as I can't get access to them because it is a laptop--I am assuming that the drive operates correctly as the md5sum was correct for both the harddrive ISO copy and the one that was burned to the CD.Cleaned the CD Lens. Could it be that it would prefer to boot from a DVD? That would seem to be excessively weird.

---

### Post by eggdeng on 2007-08-01
Sorry to insist but I get the impression you burned the ISO file alright but not [COLOR="Red"]as ISO[/COLOR]. To do this, in Gnomebaker, choose Tools, burn CD image. In KDE, there's an option along the lines of burn ISO CD in k3b.

---

### Post by Pumalite on 2007-08-01
Ditto.

---

### Post by guilly on 2007-08-01
Do you have another computer near by ? just test the cd from taht computer if it doesn't boot off the cd then you know theres obviously somethign wrong with that cd or the way you burned it!!

---

### Post by MalcolmSP on 2007-08-01
oops. A mistake I Will never make again. Sorry to be so dumb!

---

