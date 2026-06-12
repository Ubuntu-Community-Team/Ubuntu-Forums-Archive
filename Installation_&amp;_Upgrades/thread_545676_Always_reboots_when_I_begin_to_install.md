---
title: "Always reboots when I begin to install"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by zanzibuz on 2007-09-07
Hello,
I'm trying to install xubuntu onto an old computer.  It is a K6-III 450 with 384mb Ram, Asus P5A motherboard with a Via chipset and an AGP Voodoo3 video card.  This computer currently has an old install of Mandrake 10.1 on it.

I have tried to install xubuntu 6.04, 6.10, and 7.04, both desktop and alternative install cds for each version.  I've also tried ubuntu 7.04 desktop and alternative.  For every one, the install reboots my computer at the exact same spot.  The computer starts vmlinuz, then it starts initrd.gz, and a second later the computer reboots.  I see initrd.gz, periods start to cross the screen, then the bios screen loads.  I haven't ever been able to get beyond it.

I haven't been able to find any solutions to this.  I am completely out of ideas.  I know that the computer can handle linux since Mandrake is on it.

Any help is appreciated,
Garth

---

### Post by Pumalite on 2007-09-07
You might want to research your Voodoo Card.

---

### Post by banewman on 2007-09-07
From what I have read the k6 is a 586 comp and the kernels for the os's you are trying to install are 686 :- that's the trouble. If I'm right the kernel is too new for the comp. I'll read more and come back. :)

---

### Post by Pumalite on 2007-09-07
It is worrying that the common Voodoo card does not appear to be supported in Edgy. This mean that I can only convert 5 of the 16 computers I planned from Windows to Ubuntu. Only three of those with Voodoo cards seems to work with a vesa or vga adapter. None of those with Voodoo's on the motherboard want to work.

So does anyone know if there is a fix issued?

(from launchpad)

---

### Post by banewman on 2007-09-07
From my reading it seems the k6 is short of what is needed for the 686 kernel - it needs the 386 kernel.... looking in to that now.

---

### Post by zanzibuz on 2007-09-07
> **banewman said:**
> From my reading it seems the k6 is short of what is needed for the 686 kernel - it needs the 386 kernel.... looking in to that now.

You are correct.  It is a 586.  That's originally why I went with Mandrake.  Is there any way to tell the installer that I have a 586 processor?

---

### Post by banewman on 2007-09-07
Something that might work from my reading is at the "run or install" prompt from the live cd - press F6 and at the prompt that appears type :
  noapic nolapic - then hit enter. Fingers crossed. :)

---

### Post by zanzibuz on 2007-09-07
> **banewman said:**
> Something that might work from my reading is at the "run or install" prompt from the live cd - press F6 and at the prompt that appears type :
  noapic nolapic - then hit enter. Fingers crossed. :)

Same thing happens...  Starts the kernel, then back to the video bios...

---

### Post by banewman on 2007-09-07
That solves that then. You need a 386 kernel for your 400k6. I'm disappointed because I am about to set a 500k6 up as a file server and bittorrent downloader. I'll have to find out about loading a 386 kernel nowadays as I suspect they are being made redundant....:(

---

### Post by zanzibuz on 2007-09-07
> **banewman said:**
> That solves that then. You need a 386 kernel for your 400k6. I'm disappointed because I am about to set a 500k6 up as a file server and bittorrent downloader. I'll have to find out about loading a 386 kernel nowadays as I suspect they are being made redundant....:(

Correct me if I'm wrong, but shouldn't the 386 kernel be included in xubuntu-7.04-desktop-i386.iso?  Is there any way that the install process attempts to detect which processor you have, and for some reason it doesn't correctly detect mine?

---

### Post by banewman on 2007-09-07
I think you will find they are different images. [http://www.ubuntu.com/search/node/i386](http://www.ubuntu.com/search/node/i386)

---

### Post by Pumalite on 2007-09-07
He said he tried both in his first post.

---

### Post by banewman on 2007-09-08
Pumalite, try another read mate, the alternative is not 386. :)

---

### Post by K.Mandla on 2007-09-08
The stock installation kernels will work on i586 machines. I am using the default 7.04 kernel on a K6-2 450 right now.

There's some other issue at work here. I can't be sure, but a spontaneous reboot that early in the game is some kind of incompatibility elsewhere.

I would try another distro, just as a troubleshooting measure. Then, try pulling components until you can find the offending piece; if it were me, I'd try a different video card first.

---

### Post by zanzibuz on 2007-09-08
> **banewman said:**
> Pumalite, try another read mate, the alternative is not 386. :)

I did download and attempt to install the 386 version for everything I tried.


> **K.Mandla said:**
> The stock installation kernels will work on i586 machines. I am using the default 7.04 kernel on a K6-2 450 right now.

There's some other issue at work here. I can't be sure, but a spontaneous reboot that early in the game is some kind of incompatibility elsewhere.

I would try another distro, just as a troubleshooting measure. Then, try pulling components until you can find the offending piece; if it were me, I'd try a different video card first.

I have tried Mandriva Spring 2007 and Fedora Rawhide.  Both of them had the exact same incompatibility.  Then for kicks I tried DeliLinux... And it worked!  Unfortunately I found the install program to be horrible.  I got Gentoo 2005 Minimal to boot without any problems.  I'm Downloading Gentoo 2005 universal now to see if I can install it, too.

The only difference that I could find is that DeliLinux and Gentoo 2005 use a 2.4 kernel, while all of the newest versions are a 2.6 kernel.  Why that would make a difference, I dont know.

So, new question: Is there any way that I can install a current (or near current?) version of xubuntu with a 2.4 kernel, and then later on I could possibly upgrade to 2.6?

I'm going to go see if I have another video card around.  that early in the game I have to wonder, though, how it could affect the install process.  Shouldn't the text-based installer work at least with it?

Thanks for your help so far!

---

### Post by zanzibuz on 2007-09-08
I just put in an AGP Radeon 7000 AIW.  Still reboots during vmlinuz or initrd.gz...

---

### Post by zanzibuz on 2007-09-08
Okay, I've gotten Mandriva 2007 to install.  I literally tried every boot option I could find, and one eventually worked.  I used the boot option acpi=oldbios.  I tried the same option for xubuntu, but it didn't work.

So apparently I have an old bios that doesn't properly support acpi.  I wonder why the noacpi and nolapic options didn't help in xubuntu?

---

### Post by Pumalite on 2007-09-08
Is there any chance you can update your BIOS?.

---

