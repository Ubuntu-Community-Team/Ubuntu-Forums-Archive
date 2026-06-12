---
title: "Trying to test LiveUSB on my new build and can't boot with any Linux-based OS"
date: 2012-12-18
forum: Installation &amp; Upgrades
---

### Post by ready4thebreak on 2012-12-18
I built a new desktop and I want to test out my hardware and see how Ubuntu is running out of the box with my hardware selection. Here's the quick rundown on the hardware I'm working with.

[LIST]
[*]AMD FX-4100 Black Edition
[*]Gigabyte 78LMT-S2P Motherboard
[*]8GB Crucial Vengenance RAM(single DIMM)
[*]XFX Radeon 6450 Core Edition
[*]No HDD at the moment
[/LIST]

I'll try to make this as clear as possible. I have multiple flash drives with different OSes setup so I can try LiveCD's and test hardware on the fly. I attempted to throw one of my trusty old Ubuntu-LiveUSB drives and when I tried to boot my system POSTs, then gives just a simple "Boot Error" message after selecting my boot device.

I thought, maybe this drive got corrupted, so I tried a few other drives I had laying around. The system gave the same results with an older Linux Mint build. I figured maybe the new hardware wasn't supported correctly on these older builds or maybe it was the configuration or something. Then, I grabbed two new images of Ubuntu(12.04 x64) and Mint(version 14 w/MATE x64). Overwrote both drives with Unetbootin and tried again. Bang. Same results.

For laughs, I threw a random LiveUSB install of Ubuntu Server 11.10 that never got upgraded in and to my surprise, it worked! I'd rather have a GUI and more "traditional" desktop setup here, so this proved a point, but not the one I was looking for. 

What am I doing wrong? Again, this is a prestine build, all hardware has been tested and is working(had to return a few parts after some tested bad originally). I smacked an HDD from another box I had laying around with Linux Mint on it and the system was in working order(minus some drivers and all, but the builds are EXTREMELY different, so I expected that). There has to be a simple fix for this...

Thanks in advance!

---

### Post by ready4thebreak on 2012-12-18
Also wanted to mention, I tried the instructions give at this [forum]("http://askubuntu.com/questions/129116/12-04-wont-boot-from-live-cd-or-usb") and it got me nowhere. My system doesn't seem to allow me to adjust the ACPI off.

---

### Post by dsv47 on 2012-12-18
I recommend that you try making a live USB distribution that runs entirely on RAM. Three such distributions are:
1. Gparted
2. Clonezilla - (There is an option in the Clonezilla boot menu to run it from RAM.)
3. Lightweight Portable Security
If you can boot a live USB distribution when it is running from RAM, but not reliably when it is not running from RAM, then you may have a hardware issue with *power to the USB port*.

---

### Post by C.S.Cameron on 2012-12-18
I have just noticed that my HP, EliteBook, is not booting from three different flash drives with three different types of install on them, (the old blinking cursor syndrome or just freezing).

These drives boot fine from my Acer Travelmate.

The HP is booting fine from USB3 external hard drives.

---

### Post by oldfred on 2012-12-18
Is this a new UEFI system? And are you booting in UEFI mode or BIOS mode.

You then may also have video issues. Have you tried nomodeset? I have nVidia and have to use nomodeset until I get the proprietary drivers installed, not sure about your AMD.

---

### Post by ready4thebreak on 2012-12-18
> **oldfred said:**
> Is this a new UEFI system? And are you booting in UEFI mode or BIOS mode.

You then may also have video issues. Have you tried nomodeset? I have nVidia and have to use nomodeset until I get the proprietary drivers installed, not sure about your AMD.

How would I know if it's a UEFI system exactly? I believe I remember seeing a setting for that in BIOS settings, but I could be wrong. I haven't tried nomodeset, because I have been able to even get to as much as a Splash Screen on the Linux distro. No GUI, I'm just getting this "Boot Error" right after POST.

---

### Post by oldfred on 2012-12-18
When you go into UEFI/BIOS does it show hard drive when you have one connected and does it show flash drive. Often new systems show flash drive as hard drive boot option not USB boot option.

With UEFI you should see two boot options from Ubuntu 12.10 64 bit, one UEFI and the other legacy/BIOS/UEFI. How you boot is how it installs.

Some settings in UEFI/BIOS may need to be set for system to work correctly. 

I know Intel motherboard have a BIOS that expects a boot flag on a primary partition on the boot hard drive. Boot flag is used by Windows (and lilo) but not by grub.

---

### Post by kurt18947 on 2012-12-19
I don't know if you're getting bit by this bug or not but here is something to consider.  I have a similar problem with a Gigabyte MoBo and AMD Athlon II processor. When I try to start, I get  "Boot error" and that's that.   I find that I must format a USB drive to FAT32 ***with windows** *then create the liveUSB.  Formatting with gparted then creating a live USB will boot fine on an older Gigabyte-AMD machine and on notebooks but not on this one newer Gigabyte-AMD build.  I think it's something to do with the modular BIOS.  It could also have something to do with UEFI, I have no experience with that.

---

