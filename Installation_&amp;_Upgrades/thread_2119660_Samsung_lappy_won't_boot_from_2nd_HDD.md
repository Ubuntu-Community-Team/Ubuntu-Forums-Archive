---
title: "Samsung lappy won't boot from 2nd HDD"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2013-02-24
I have a Samsung Series 3 laptop (model NP300-V5A) that won't boot from a second HDD where I have installed Ubuntu 12.04.2 (x86).

I replaced the primary HDD with a Samsung 830 series SSD and moved the original Windows 7 Home Premium install there.  More recently, I bought an optical bay HDD caddy and reinstalled the original HDD as a second drive.  I installed Ubuntu 12.04, and its bootloader, to the second HDD.  So it should be able to boot.

I have "SATA CD" and "USB CD" in the boot order ahead of the Samsung SSD, so why won't the system boot off the second HDD?  

The system will boot off e.g. a bootable USB stick, which is how I installed Ubuntu 12.04 to the secondary HDD in the first place.

I've avoided installing the Ubuntu bootloader to the SSD because I'm concerned it would interfere with the rapid resume/sleep functions of the Windows 7 install, which are really quite nice (this thing wakes and sleeps QUICKLY.).  But it's starting to look like that may be my only option to dual-boot.

---

### Post by darkod on 2013-02-24
I have seen other threads where the optical device bay disk is not bootable. I guess it might be by design.

Have you tried with usb cd option as first, or the optical device option? It might still consider it as the optical device.

---

### Post by Objekt on 2013-02-24
Yes, in fact I've put every available device ahead of the SSD in boot order - still no dice.

I ended up reformatting the second HDD, and reinstalling Ubuntu 12.04.2, this time with a "traditional" dual-boot, i.e. GRUB on the primary drive (SSD).  I am happy to report that it does NOT interfere with the rapid sleep/wake functionality of Windows 7!  To get the GRUB menu to come up, I have to do a complete shutdown, then power up (i.e. cold boot).  That is, in a way, better than having to choose an OS every time I bring the system out of sleep or do a warm-boot.

Now to test whether Ubuntu can properly use the sleep/resume features.

---

