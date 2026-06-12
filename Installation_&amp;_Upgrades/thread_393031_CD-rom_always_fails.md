---
title: "CD-rom always fails"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by DDS_370 on 2007-03-25
I'm very new to Linux - and can't get it to install because the cd-rom is always corrupt.  

Trying to install 6.06 Xubuntu on an old Toshiba laptop (325CDS), and the CD-rom consistently fails.  I have burned the CDs on two other laptops, using ImgBurn and InfraRecorder.  I have run chksum on the downloaded file (works fine).  I have set the burn speed at 4X and burn with all other applications closed.  I've tried at least two separate cds.  

Regardless, whenever I run the "Check CD for Defects" function from the Xubuntu menu, it inevitably fails.  

What else can I do?  Thanks!

---

### Post by aecoss on 2007-03-25
Im having the SAME problem with Dapper Drake.....No matter which which image burning app I use...the error checking always fails.....Is this a widespread issue with Ubuntu 6.06? FYI Im trying to get it running on a 1600 Mhz AMD Sempron machine with XP Pro and no partitions (YET)...

---

### Post by angry_penguin on 2007-04-09
> **DDS_370 said:**
> I'm very new to Linux - and can't get it to install because the cd-rom is always corrupt.  

Trying to install 6.06 Xubuntu on an old Toshiba laptop (325CDS), and the CD-rom consistently fails.  

Sounds like a CD drive related problem to me.

I have a similar but different problem.  About 2/3 times I try my CD fails to boot but if I just press reset and retry I can eventually reboot (and even install).

Just a thought but maybe you should test the CD off the laptop.  If they test OK elsewhere then try getting a lens cleaning kit or do what I did and just keep retrying.

---

### Post by dptxp on 2007-04-09
It is also possible that your iso is corrupt. If you have not used torrent to download, use it, save the new iso exactly where your iso is, you do not have to download full iso, existing one will get corrected.

---

### Post by tl3000 on 2007-04-09
I am also facing this same problem with a Dell Dimension V400 desktop (PII-400MHz with 320MB ram, 9GB HD, NEC C3000A CDROM drive, built-in ATI 3D Rage Pro video, and an Ethernet PCI card).  Tried Ubuntu 6.10, 6.06, Xubuntu, and alernate install LiveCDs... Tried swapping CDROM drive and IDE cable... Tried using PIO drive instead of DMA... Tried setting CDROM from secondary IDE master to primary IDE slave... Tried various combinations of boot parameters (e.g., ide=nodma, fb=false, video=vga16:off, noapic, nolapic, acpi=off)...  Minimized the PC resources usage to bare-bone essentials and disabled unused BIOS functions (e.g., ACPI and audio)...  Tried verified ISO images with CDs burnt at 2X, 4X and 8X... still unable to boot/install from the LiveCDs.  Failure occurs randomly during accesses to the CDROM, read data gets corrupted, and the display screen is affected too.  I suspect that there are some memory conflicts with Ubuntu's handling of the CDROM IDE interface but don't know enough to know what and where.  Segmentation faults are reported on screen during the boot process startup.  Again, don't know the source or cause(s).  The CDROM drive works fine under DOS and Win 98.  Any suggestions?

---

### Post by dptxp on 2007-04-13
Check your iso with md5sum. Ensure that iso is OK.
More information here -
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

iso are best downloaded using BitTorrent.

Burn using Infra Recorder (in windows).
Use burn-image command (not bootable cd or data cd)

After you burn CD and run it, click on "Check CD for defects" before
clicking on Live/Install.

Then if all is OK, click on Live/Install and pray.

---

### Post by tl3000 on 2007-04-13
> **dptxp said:**
> Check your iso with md5sum. Ensure that iso is OK.
More information here -
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

iso are best downloaded using BitTorrent.

Burn using Infra Recorder (in windows).
Use burn-image command (not bootable cd or data cd)

After you burn CD and run it, click on "Check CD for defects" before
clicking on Live/Install.

Then if all is OK, click on Live/Install and pray.

For my situation, I've checked and verified the ISO checksums on all the different versions I tried using to ensure no data corruption occurred during downloads.  I also checked and verified the checksums for all the individual component files on each of the burnt CDs to ensure that no data corruption occurred during CD burning.  Not a problem with the discs...

My problem has evolved to a RAMDISK issue described in the following thread:

[http://ubuntuforums.org/showthread.php?t=407596](http://ubuntuforums.org/showthread.php?t=407596)

---

