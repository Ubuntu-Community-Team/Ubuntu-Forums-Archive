---
title: "Boot from floppy, install from CD"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by Nepherim on 2007-03-21
I have an old machine I'm trying to install Edgy desktop onto. The machine has working floppy and CD drives. I can boot from floppy but there are no BIOS settings to boot from CD. 

I have created a floppy based on these [instructions]("http://ubuntuforums.org/showthread.php?t=246486"), using SMB 3.7.1 and the Edgy .bin. When I select the CD from the pulldown and press Enter (to select the option), I get an error **"Disk error! 0xAA"**. I set the CD to Active (F4), no error, but still not bootable from the CD.

My CD appears to have burned correctly. It works and is readable from another PC. I know the CD drive works because I previously booted from floppy, and installed Smoothwall.

I searched the forums for a while, and read various FAQs, but none which seem to be able to help me move ahead. Suggestions appreciated.

 ~ ~ Dave

Machine details:
[LIST=1]
[*]AST Bravo MS-T Pro 6200; 
[*]200MHz Pentium Pro; 
[*]CD signature on boot-up is CDR_S18
[*]96Mb
[*]currently has Smoothwall installed on it (no need to keep this)
[/LIST]

---

### Post by wpshooter on 2007-03-21
If that is 96mb of MEMORY/RAM, then I believe you can probably forget about getting Edgy to run on that machine.  Probably need at least 256mb or preferrably 512mb memory to run Edgy decently.

You might want to try Xubuntu or Damn Small Linux (DSL).

Good luck.

---

### Post by Nepherim on 2007-03-21
> **wpshooter said:**
> If that is 96mb of MEMORY/RAM, then I believe you can probably forget about getting Edgy to run on that machine.  Probably need at least 256mb or preferrably 512mb memory to run Edgy decently.

You might want to try Xubuntu or Damn Small Linux (DSL).

Good luck.
Good to know that. Given that I'm likely to hit this same problem later, here's an update.

I can access the Smoothwall command line. So it occurs to me that I could mount the CD drive, and initiate the Ubuntu/Linux install direct. How do I do that?

---

### Post by Nepherim on 2007-04-19
Okay, since Ubuntu is going to be a little large for my machine, I'll go with Xubuntu. The question is the same though. How to boot from floppy, and then initiate the CD install. Or, if I'm in the Smoothwall command line, is it possible to mount the CD and initiate the Xubuntu install?

---

### Post by confused57 on 2007-04-19
> **Nepherim said:**
> Okay, since Ubuntu is going to be a little large for my machine, I'll go with Xubuntu. The question is the same though. How to boot from floppy, and then initiate the CD install. Or, if I'm in the Smoothwall command line, is it possible to mount the CD and initiate the Xubuntu install?

When you boot from the SBM floppy, have you tried pressing "enter" a couple of more times when you get the Disk Error?

---

### Post by Nepherim on 2007-04-19
> **confused57 said:**
> When you boot from the SBM floppy, have you tried pressing "enter" a couple of more times when you get the Disk Error?
Pressing Enter the first time clears the error message. Pressing a second time simply goes through the cycle of displaying the error message again.

---

### Post by Nepherim on 2007-04-23
Anyone have any experience/suggestions for this?

---

### Post by Nepherim on 2007-04-28
Okay, my last attempt: How to boot from floppy, and then initiate the CD install. Or, if I'm in the Smoothwall command line, is it possible to mount the CD and initiate the Xubuntu install?

---

### Post by baldmancan on 2007-05-02
I too cannot install.....
I am new to linux.
I want to install it on a similiar capacity machine.
This machine has no capability to change the boot order from Bios.
So, I need to boot from floppy, and then initiate the CD install. (xubuntu)
I have read many postings about creating a floppy using SBM and rawrite to do this.
I have both on a floppy, I  have the cd in the cd drive and when I reboot. nothing happens.
any help with this install, would be appreciated.

---

### Post by pinoytechie on 2007-05-02
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#CDROM_related_subjects")

---

### Post by ocheyes on 2007-12-18
I too have the same problem. SBM does not work when the computer's BIOS is not configured to recognize the cdrom as a bootable device. I need scripts to get the cdrom recognized once I have started the box with the floppy disk and then access the cdrom to install the distro from the cdrom. So far nothing works. I can start the computer from the hard drive (using a previously installed version of DSL) but, again, can't go to the cdrom to install Xubuntu...And I have a 500Mhz computer with 128 MB of RAM and a 20 Gb hard drive. This old box configuration is a lot more advanced than the one's from the other people posting here but still can't install Xubuntu.

---

