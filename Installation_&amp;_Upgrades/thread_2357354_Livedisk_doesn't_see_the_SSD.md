---
title: "Livedisk doesn't see the SSD"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by Dennis_Beekman on 2017-04-01
[CENTER][URL="http://aldi.medion.com/md60250/nl/?refPage=aldi"]

[IMG]http://computerkiezen.nl/website/wp-content/uploads/2017/03/ALDI_MD60250_550x260_NL.jpg[/IMG]


http://aldi.medion.com/md60250/nl/?refPage=aldi[/URL]

[/CENTER]

This week i bought a new Medion MD60250 (E2228T) laptop as shown above.
Allthough it is a cheap Atom powered laptop it seems well build and works good enough under Windows 10.

I have however been totally unable to install Ubuntu 16.10 on it so far.
I had to do the following to get the standard livedisk to start and give me a desktop.

- Disabled "fast boot" and "secure boot" in my UEFI.
- Set the GFX mode to "1024x786x32" in the grub.cfg file of the USB drive. (otherwise the screen goes blank after 2 seconds of showing me the desktop).
- Set the "NOACPI" and "ACPI=off" flags in the grub.cfg file of the USB drive (otherwise the boot process fails on a ACPI call).

During the boot process the computer goes into hibernation twice and has be woken back up by pressing a button... it then continues to boot normally as expected.
It eventually shows me the desktop and all seems fine... however the laptops internal 64GB SSD (RAM ?) storage is not shown... only the USB storage.

The latest Debian and Arch Linux install images both find the drive with no problem just not Ubuntu 16.10 (or 17.04 beta) :-({|=
fdisk -l only shows the USB drive and a number of 64MiB ram disks with according to Google are normal.

I would hate to be thwarted at the last hurdle, so if anyone has any suggestions on how to find and mount the drive for installation I would be very greatfull ](*,)

---

### Post by oldfred on 2017-04-01
Obviously if Windows boots and other installs see drive, then UEFI correctly sees drive.

Is drive one of the new NVMe types?

Is drive shown in gparted or with a gparted live ISO?
What does parted show from other distributions?
sudo parted -l

       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570)

---

### Post by Dennis_Beekman on 2017-04-01
It is indeed a NVMe or similar type of storage system and it is working just fine in Arch Linux and Windows.

Parted -l
Model MMC 064G838 (sd/mmc)  
Disk /dev/mmcblk0 62,5GB 
Sector size (logical/physical): 512B/512B
Partition table: gpt

As far as I can tell it is being seen as a SD/MMC storage card with is odd, but it is a cheap laptop though so nothing would surprise me.
I will try again with a clean image of 17.04 wich should have the lasted packages... maybe i made a mistake not testing 17.04 further earlier.

Update:

I can confirm that 17.04b2 doesn't see the drive and parted doesn't list it either.... just the usb drive.

---

### Post by oldfred on 2017-04-01
If mounted at /dev/mmcblk0 that is the SD/MMC card which a lot of these small low cost Atom systems seem to use.

I do not know what drivers Debian & Arch may have that Ubuntu does not have. Since Ubuntu is based on Debian and often is somewhat more up to date.

And Ubuntu should have no issues seeing gpt drive. I have used gpt on internal drives & flash drives for years.

Some older Atom based systems were configured as Windows only by using 32 bit UEFI. But then Linux released a 32 bit UEFI. It is not in the standard Ubuntu distributions and you just have to add it. Perhaps Debian & Arch include the 32 bit automatically, now?
But with Ubuntu it would not boot at all if 32 bit.

---

### Post by Dennis_Beekman on 2017-04-01
I already tried a 32 bit UEFI, sadly this did nothing either.
I was going to test the system with Ubuntu before eventually putting Arch linux on... seems I will have to go straight to Arch on this machine :biggrin:

---

### Post by pvtillo on 2017-06-06
Hello, I have the same laptop as you. I tried to install Ubuntu on it, but I got the same problems.
However, I use Ubuntu Budgie, and Ubuntu Budgie sees the SD/MMC card, so it must be possible to install Ubuntu Budgie. I used version 17.10.
I did not install it yet, but I can choose the SD/MMC card. Maybe this is some help to you.

---

### Post by euneuber on 2017-07-03
just tried lubuntu 17.10-alpha1 on this notebook and it works in high resolution (still goes to sleep during booting). Touch screen does work. I did not install, but will try on a SDCARD or USB key.

---

