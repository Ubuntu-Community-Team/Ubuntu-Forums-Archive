---
title: "Lucid 10.04 Live CD Issues with HP"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by rmccarri on 2010-06-10
Hi everyone,
I've pooled through the hundreds of posts regarding issues with the Lucid Lynx live CD installation, but have not been able to get any of the fixes to work.  I'm at my wits end here.  Yesterday, my computer froze and when I brought it back up after a hard reset it was borked.  It would freeze at after the login screen (it seems like this is a plymouth issue and if I ever get it Ubuntu installed again, I'll remove this package).

I've tried the many suggestions for boot options.  The best that I've been able to get so far is with "irqpoll xforcevesa nomodeset acpi=off noapic"

These options get me past the "setting sensor limit [ok]" step, but it freezes at the Ubuntu wallpaper.

I have an HP DC7800 with an nVidia video card.  I've disconnected my second monitor as I've heard that can cause issues.  I've been using Ubuntu since 7.10 and exclusively since 8.04 and never have I had such a frustrating time installing the OS.  I've also tried the alternative text based installer and it freezes at the partitioning step (at 33% every time).  Any suggestions of additional magic boot options or anything else that I could try?

Thanks,
Rob

---

### Post by dino99 on 2010-06-10
maybe try with an other cd

boot without "splash"

at last, boot in recovery mode

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

sudo update-pciids && update-usbids
sudo rm -f /etc/X11/xorg.conf

[http://www.google.fr/search?as_q=DC7800+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=DC7800+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by rmccarri on 2010-06-10
Thanks for the suggestions.  Unfortunately, I had already made the decision to start fresh as this has been continually upgraded for several releases and I thought it might be a good time to get a fresh install with a LTS release (and I even **shutter** installed Windows XP to test and see if there was a major hardware issue and it installed without a hitch).

I've tried booting to the live CD with splash turned off and I've redownloaded the iso file, checked the MD5 sums and verified the burn process (and tried a couple of different brands of CD-Rs to make sure it wasn't a bad batch of disks).  Also, I swapped out the DVD drive from another computer to make sure that wasn't causing the issues (I'm getting some I/O error on device sr0 in the boot, but got the same errors on my laptop and was able to boot into the live CD just fine).
Rob

---

### Post by rmccarri on 2010-06-11
Well, I finally figured this out.  I could install Windows, and run Puppy Linux and some other Live CDs without a problem.  As it turned out, one of my ram chips was bad and all of the 32 bit OSes were running fine, but the 64 bit Ubuntu installs were going bad because they could see the bad chip.  I just put on of the good ones in and it's running fine.

---

