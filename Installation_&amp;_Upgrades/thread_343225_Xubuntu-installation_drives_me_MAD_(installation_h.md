---
title: "Xubuntu-installation drives me MAD (installation hangs up)"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by egon123 on 2007-01-21
This is the story of my tryings to install xubunut on my desktop-PC.
People, who don't want to know the whole story, but like to help me, may start reading at "*The Problem now is...*"


First I downloaded *xubuntu-6.10-desktop-i386.iso*, the checksum was ok, and i burned it on an old CD-RW to install it on my laptop. everything worked great (even if i don't like the havy-weight installation with the live-system) and i really got in favour with xubuntu.

Now I wanted it also on my desktop-PC to take the place of my fast, but not so userfriendly VectorLinux... and here the desaster began:

First time the installation seemed to run normally, but after reboot, I just got *"Error 17"* from GRUB. When i started the installed system with a boot-cd, i got many many errors (modules.dep not found). The Xfce-Desktop loaded even normally but nothing worked with hardware. btw, the error 17 of grub won't vanish after
re-installing grub.
I decided to re-install Xubuntu... but without success:

**The Problem now is...**
that I never saw the "installation"-Link again. 
=> When I put the CD in my HP-CDRW-Drive (secondary Master) it will hangup between 4% and 20% of "loading kernel" and say "error reading boot cd".
=> on the other drive (noname-DVD, secondary slave) after finding usb-ports (ergo always at the same point) it will say:

[FONT="Courier New"]cdrom_decode_status: error=0x51 driveReady Seek Complete Error[/FONT]

together with other /dev/hdd (this is the drive)-errors this repeats forever, sometimes some "reset ATAPI" or something in between.

The same happens, when I try to check integrity of the CD. Although on my laptop, I can easyly check integrity and install Xubuntu. 

**What I already tried:**
[LIST]
[*] re-downloaded image *xubuntu-6.10-desktop-i386.iso* (although the checksum was ok)
[*] re-burned image on different CDs with different CD-writers
[*] ide=nodma noapic nolapic acpi=off debian-installer/probe/usb=false (even if i don't know what the apic-stuff means)
[/LIST]

I have also an Ubunutu (not Xubuntu)-CD 6.10 (don't know which image exactly, got it by a friend), on which the live-CD-environment starts just fine.

Anyone any idea?


Egon

---

### Post by Pobega on 2007-01-21
If you have an Ubuntu 6.10 CD, install with that. Once you get the installation done remove the ubuntu-desktop metapackage for the xubuntu-desktop metapackage, and you'll basically be set. You may also need to remove Gnome in place of Xfce, but it shouldn't be too hard. Especially if you use [this page](http://www.psychocats.net/ubuntu/purexfce) to switch from Ubuntu to Xubuntu.

---

### Post by egon123 on 2007-01-21
thank you, i will try this workaround.
but although it seems very strange to me... I had never problems installing any other linux-distribution.
what I forgot to say: the ubunut-CD works only on the DVD-drive, on my HP the installation hangs with the same problem as with xubuntu ("cannot read boot CD" while "loading kernel")


Egon

---

