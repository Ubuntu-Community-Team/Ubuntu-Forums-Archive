---
title: "Install Ubuntu to Microdrive without touching XP install"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by kseise on 2007-08-25
I want to install Ubuntu onto a microdrive that I can slap into a work provided laptop.  I love Ubuntu and the suite of GNU software available.  I use it exclusively at home and frequently prefer it over the software I am forced to use for work.

My requirements are this:
Full install onto microdrive (up to 8 gigs) using PCMCIA adapter
Bootable into Ubuntu when microdrive is present
No trace of Linux when microdrive is removed.

Anybody ever try this?  I saw WinGrub which has to be installed on the Windows partition.  I can not modify the MBR or in any way modify the XP setup.  I will be able to mount the NTFS partition to write to a folder on the drive.  

The primary use would be to use the laptop as a thin client on my home network while leaving it untouched and using it on my corporate network.

Can anybody help me?

---

### Post by kseise on 2007-08-27
Let me make this clearer.  I want to use the BIOS boot device selector to boot to XP on the hard drive, or boot to Ubuntu on the microdrive (removable device).

I know I can choose to boot to either one with the BIOS options, but can I install everything to JUST the microdrive when doing the Ubuntu install?

---

### Post by kseise on 2008-04-08
Just to wrap this up, and because I enjoy talking to myself.  I gave up on the microdrive but did manage to install on an external USB drive, not a flash drive, but a USB HDD.  

I removed the hard drive from the laptop, booted from the live CD, plugged in the USB drive and did a fresh install of Ubuntu to the only drive on the system.

On reboot, I edited the GRUB menu.lst file to boot from /dev/sda instead of /dev/hda.  

Now I can use the BIOS to toggle between the two and when the USB drive is not attached, there is no trace of it on the Windows side.

---

