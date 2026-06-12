---
title: "Live CD hangs on load"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Gelf on 2008-03-23
I've been working on this for the last couple of days, searching google and forums, and I'm stumped.

I'm trying to install Ubuntu 7.10 on my Thinkpad T61, and no matter what menu option I choose, after the Loading Linux Kernel screen disappears, I'm left with a black screen and a blinking gray cursor in the upper left corner.  I don't get the flash screen or a progress bar, and I most certainly don't get to a desktop environment.  I've tried the normal live CD in normal and safe graphics mode, and the alternate CD.  I checked the ISO md5sums before I burned the disks, and I've run the "Check CD for defects" menu option on both disks (on my desktop, not my laptop, because even that option causes the disks to hang).  I've let it sit for two hours, hoping that whatever was hanging would time out.  No luck.  I've also tried the boot parameters acpi = off noapic nolapic and various vga= options.

My laptop's specs are:
2GB RAM
Intel 8300 core 2 duo
nVIDIA Quadro NVS 140M

It's running Vista currently, I was planning on adjusting the partitions and dual booting.

I've read the thinkwiki guide and talk page, and I've looked at the Gentoo wiki's T61 install page.  I've also tried a Debian Etch install disk (I get a kernel panic when it tries to load), and a Knoppix 5.1.1 live DVD.  The Knoppix DVD fails with "'/cdrom/knoppix/modules/cloop/ko' Bad file number" as does the Knoppix CD image I put on my flash drive.

Any thoughts?

---

### Post by Pumalite on 2008-03-23
Clean the lens in your burner maybe?

---

### Post by Gelf on 2008-03-23
I don't think the CD burner is the problem, but your answer gave me a thought.

This is a brand new laptop, and trying to install Ubuntu is the first thing I've used its CD drive for.  Since I saw your post I've been testing the drive, and I'm getting errors both playing DVDs and copying data from CDs.  I think I'll be getting on the phone with Lenovo tech support tomorrow.

Thanks!

---

### Post by lemcott on 2008-03-24
had the same problem here.

when in the liveCD menu, hit F6 while the "install or run Ubuntu" (or something like that) option is highlighted. type in "noapic" without quotes
enter.

and let it run, thats what did it for me atleast.

---

