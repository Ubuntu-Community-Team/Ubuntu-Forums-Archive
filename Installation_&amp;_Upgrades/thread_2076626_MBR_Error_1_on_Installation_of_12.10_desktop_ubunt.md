---
title: "MBR Error 1 on Installation of 12.10 desktop ubuntu 64 bit."
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by azngigolo64 on 2012-10-26
Hi,

I hope someone can help with this.  I recently had a virus on my old computer hard drive and I decided to wipe everything out with Acronis using a DoD triple overwrite. I downloaded the ubuntu 12.10 desktop version 64 bit and tried to install it using both a bootable cd and a usb drive.  After I turn on the computer and it goes through the bios, I get the "MBR error 1, press any key to boot from floppy"

I tried to use a windows installation cd but I cannot get past this mbr error. It will not boot from CD or USB.  Any thoughts? Thanks!

Eddie

---

### Post by dannyboy79 on 2012-10-26
did you set your BIOS to boot from either a CD or a USB key?

---

### Post by azngigolo64 on 2012-10-26
Yes, it is set to boot from cd and usb.

The annoying thing is when I put in the Acronis boot cd, it loads from the CD but when I put in the windows 7 installation/recovery cd or the ubuntu cd and usb, it goes straight to MBR error 1...:confused:

---

### Post by dannyboy79 on 2012-10-26
Well, when you used Acronis to wipe the drive you wiped out the MBR. Whats very strange to me is that your computer is unable to boot to a CD. I was going to suggest you download and make a bootable CD or USB of Gparted Live so that you can wipe the drive and create a ms-dos partition table. Can you do anything like that with this Acronis disc you have?

and you're 100% positive that the BIOS is set to boot to cd-rom first? Also is this a really really new computer with UEFI instead of a BIOS?

---

