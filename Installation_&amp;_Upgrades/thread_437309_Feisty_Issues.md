---
title: "Feisty Issues"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2007-05-08
Hi,

As many many people are experiencing a whole range of issues with the new Ubuntu release 'Feisty 7.04' I thought I would start a thread to list the issues here in the hope someone higher up the food chain will take notice.

This has to be the buggiest release of Ubuntu to date, personally I never had any issues with 6.10 Edgy and felt it was one of the most polished releases yet however Feisty has made me lose all faith in the product hence I am departing to my roots aka Debian 4.0.

Before I go I wanted to compile a list of issues I have found and I hope others will add to this list and keep this thread clean - so let me start.

Here are my system specs in full:

Dual P4 Prestonia Xeon's clocked at 3.5Ghz stable
Asus PC-DL Deluxe Motherboard
4GB Samsung DDR-400 Memory
1 x 160GB Hitachi Deskstar IDE Drive (main boot drive) / 1 X WD Raptor 75k Drive (linux only)
3 x WD Raptor 75k IDE Drives setup in RAID0+1
LG DVD-WRITER
LG CD-BURNER
Sound Blaster Audigy soundcard
nVidia 5950 Ultra 256MB (mildly overclocked)
2 x Dell 24" TFT Panels

I have my system running in dual desktop mode with Beryl + AIGLX installed on a Gnome desktop (as it should be) - all works fine on Ubuntu 6.10.  I had a tweaked install of 6.10 whereby my drives were setup correctly and running at their full potential, a solid Gnome desktop with the latest stable build of Beryl + AIGLX in all its 3D blingage - but the upgrade killed everything.

1. Upgrade from a customized/modified (only stable repositories used) Ubuntu 6.10 to 7.04 failed at around 75% when trying to install the new kernel image.

2. Performing a clean install to the WD Raptor drive (linux as the only system) resulted in grub loading up with the kernel images in the list however then being unable to find any of my drives (via the menu or command line)

3. Installing a clean build of 6.10 and then upgrading 7.04 resulted in a bootable system (6.10 as a stock image, no updates done)

4. sdparm does not work (neither does sdparm)

5. Random issues like 1 out of 5 times grub fails to find any drives in the system (full system check done, other linux distro's see my drives correctly)

6. Continueous errors in syslog stating:
```
3.876504] Buffer I/O error on device sda3, logical block 69898624
3.876514] attempt to access beyond end of device
```

7. Sound dying for no reason, have to scan for the soundcard to get it working again (have tried OSS, Alsa etc, had no issues in 6.10)

8. Poor disk performance

9. More load being presented on the CPU's (6.10 would result in a whisper quiet and relatively stress free OS)


These are my current issues, I am sure people have more, would appreciate it if folks could list their issues as per above.

Well good luck with Ubuntu, I may return after a few releases or when 7.04 has been sorted out finally ;)

Adios,

Fz

---

