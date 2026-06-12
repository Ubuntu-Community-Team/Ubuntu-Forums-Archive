---
title: "New Xubuntu over old SUSE, with some hurdles to hop"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Foster Grant on 2008-03-26
Houston, we have a problem. At least, I do.

I've recently been handed a computer set up to dual-boot SUSE 10.1 and Windows XP and asked to install Xubuntu 7.10 in place of the SUSE installation. It only has half a gig of RAM and SUSE runs v-e-r-y s-l-o-w-l-y on it.

Needless to say, it's somewhat more difficult than it sounds. :)

The SUSE partition is set up to load from GRUB without a login/password screen (single-user setup). However, I can't figure out what the root password is for the SUSE partition, and nobody else knows it. Logically, without the root password I can't do anything inside the SUSE system (apparently it was abandoned by the original owner due  to the system's inablity to see the computer's sound card and Ethernet card — this system is not a ringing endorsement of 

Of course, I figured the easiest way to do it would be to pop in a Xubuntu LiveCD and then boot/install from that. Eh ... not so much. I can tell the computer BIOS to load from the CD-ROM drive (and I have), but when SUSE's version of GRUB loads, it bypasses BIOS directives and gives me a choice of SUSE, Windows, floppy disk or recovery partition (which I believe to be the Windows XP recovery partition, so it would not be helpful under the circumstances). This computer will not load from the CD drive at all.

I tried to backdoor into a Xubuntu installation via Wubi 7.10, but hangs up early and it won't load from the CD. Then when I boot into Windows, it says "Ubuntu is already installed" and gives me the uninstall option. I have a feeling it sees the SUSE partition, but I can't be sure. I can guarantee that there's no Wubi-Ubuntu installation on this C;\ partition — I've checked.

Fragging the entire hard drive and starting over is *not* an option (end user's choice, and the end user happens to be my mother, who's retired and has somewhat hesitantly agreed to give Ubuntu a try). Mom got this computer second-hand from one of her friends after friend's son went off to college with a fancy new laptop. I need to make this look easy, *without making it look like Data Armageddon*, so I can make another Ubuntu convert.

Any ideas other than loading the computer into a [trebuchet](http://en.wikipedia.org/wiki/Trebuchet) and launching it are requested and welcome. :)

[IMG]http://i176.photobucket.com/albums/w186/Foster_Grant/forum%20stuff/popcorn.gif[/IMG]

---

### Post by PmDematagoda on 2008-03-26
Actually, it's kind of hard to believe that the Live CD is not booted unless:-
1) The Live CD is corrupted.

2) The CD-ROM is broken.

This is because when you instruct the BIOS to boot from a CD, it will boot from the CD if it is bootable regardless of the MBR being occupied by GRUB.

At what speed did you burn the Live CD? Did you also check the md5 sum of the ISO?

---

### Post by Foster Grant on 2008-03-26
> **PmDematagoda said:**
> Actually, it's kind of hard to believe that the Live CD is not booted unless:-
1) The Live CD is corrupted.

2) The CD-ROM is broken.

This is because when you instruct the BIOS to boot from a CD, it will boot from the CD if it is bootable regardless of the MBR being occupied by GRUB.

At what speed did you burn the Live CD? Did you also check the md5 sum of the ISO?

CD is not corrupted — I just booted it on this computer to verify it. All Xubuntu LiveCD functions are as expected.

---

