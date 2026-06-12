---
title: "install from floppy only"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Malegnis on 2007-06-11
is there a way to install (maybe an older version) of Ubuntu on a Compaq Presario 1200 using only floppy disks?

most other methods are out.. :-(

---

### Post by lemonwonder on 2007-06-11
What bout ordering the free live cd?

I am pretty sure a floppy only takes like 2mb stuff so my guess would be... **NO you cant**

---

### Post by Malegnis on 2007-06-12
well, it is possible, i can actually get "BasicLinux" to boot off of two floppies, but the problem is that i cant really get the cd to work, upon mounting i get the "no medium found" error, and i know theres is a Cd in there, and i have tried several CDs.  if there was a way for me to boot up from a floppy, get the HD read/write - able, the os is loaded in the ram, and then the floppies could carry over a compressed split file, where then it would be merged and then uncompressed and we would have a basic bootable OS on the hardrive, where i could then maybe use to install a more appropriate version of Ubuntu.  

i am going with the assumption that the dvd drive is not able to be booted (it did once but now it wont - thats one in like 150 boots) 

so maybe i could get some help in getting something that will mount up my usb port?  then perhaps i could simply install off of that.

o, and for a side note, i have no Ethernet only a built in modem. so net install is also out.

---

### Post by tgalati4 on 2007-06-12
"Prepare 500, formatted 1.4 MB floppy disks, labeled 1 through 500.  Insert the first disk when instructed."

Try Damn Small Linux.  There is a Floppy boot option with a network install.  At 50 MB, it's the smallest distro that I know of.

I loaded DSL on an old HP Omnibook with similar problems.  I took the harddisk out (it pulls out in a cradle), inserted it with a ribbon cable adapter ($6) and put it in an old P1 desktop machine.  Put DSL on it through normal CD install procedures.  Put the disk back in the Omnibook; result:  working DSL system.

There may be other distros that have floppy-network installs, but choose your distro carefully based on your hardware specs.

---

### Post by Malegnis on 2007-06-12
this was my original idea, to use dsl, copied over on floppies, but i was looking for either a way to utilize my usb (im currently using a grub boot disk to try and solve this problem) or look for an old distro of Linux (when floppies were the means of installing) to be able to maybe revive my cd drive, or to create a boot partition that will be able to boot a different CD.

---

### Post by lemonwonder on 2007-06-12
Wow, its a bit too technical for me :)

---

### Post by Malegnis on 2007-06-12
ok, another idea: perhaps i could use my laptops modem to dial out to my host machine (i could hook them both up to a pone line) and download or transfer the files i need that way?

now i need to find a way to run a ppp server for my house, this is difficult for me.

---

### Post by tgalati4 on 2007-06-12
You can also use floppy-based Smart boot manager (I don't have the link handy) and it will have an option to boot from CD for those old machines that don't have CD-boot as a BIOS option, or if the BIOS just doesn't work as it is supposed to.  That get's you back to a standard, CD-based installation process.

---

### Post by arvevans on 2007-06-12
Just maybe, the answers already given made some assumptions that were erroneous?
[LIST=1]
[*]Have you entered the CMOS configuration and checked to see if the computer is actually recognizing the CD-ROM drive?
[*]Have you entered the CMOS setup section and set the options so that the computer can boot from a CD?
[*]Does your computer actually recognize and boot from a Windows install CD?  If it won't boot from Windows, then it probably won't boot from any CD.
[*]When you made your Linux CD, did you insure that you wrote it using "ISO Image Copy" options?  It must be an ISO Image in order to be bootable.
[/LIST]

Once you have established that the computer can actually boot from a CD, then you are ready to try booting from a Linux CD.

[CENTER]===========  FLOPPY BASED  INSTALL ==========[/CENTER]

As to using floppies to boot a new linux...it is possible.  That is the way we all did it for many years.  You will need to find an old Linux distribution that includes the floppy utility tool called "rawrite" and that has the Linux files separated out as floppy sized disk images.  On that distribution, locate the boot image file that is the closest match to your hardware (usually the question is whether you use IDE or SCSI hard drives).  Use the "rawrite" tool to write the selected Linux boot image to a floppy disk.  You will also have to find the commands floppy image (there may be one or two of these) and also use "rawrite" to copy each of these to a floppy.  Then if all this has been done properly you can insert the boot diskette into your floppy drive and boot from it.  The system will then ask for each of the commands floppies.  After reading 2 or 3 floppies you will have a Linux kernel and small commands library running in system RAM.  At this point you can log into this abbreviated Linux and use "fdisk" to partition your hard drive for Linux.  After the hard drive is properly configured you can use the "install" or "setup" command to configure install options and to start actual installation from subsequent floppies to your hard drive.

OK.  If you read and followed all that, it should be obvious why we don't use floppies now to install Linux systems, and why most distributions do not even support floppy based installs.  The process is long, error prone, and requires a mountain of floppy disks (the typical Linux install is at least 700 MB of data, which would require 466 floppies). 

There are some guidelines to use when installing Linux on an old or discarded computer:
[LIST]
[*]If it won't run Windows, it probably won't run Linux
[*]Running Linux will not fix broken computers.
[*]Computers that run Windows slowly, will probably also run slowly on Linux.
[/LIST]

Hope this helps.

---

### Post by Malegnis on 2007-06-12
my computer can boot from the CD, it just wont, i used the smart boot manager, and it kept giving an error like there was no cd in the drive.  i found a Linux distribution called basicLinux, and i had a basic shell, but i was unsuccessful in mounting my CD (once again an error like there was no cd in the drive), i think this is due to a problem inside the cd drive.  so then i decided to move on to using the USB in the back, the kernel i have on the floppies doesn't have any tools for mounting it (that i know of) but once i get something basic on the HD perhaps i can use it to drop an ISO onto a partition, then boot it yada yada yada.  

but i do know that i have a working CD (its the ones you get when you request a CD, and my CD drive is recognized by the computer -i see the drive when it boots up- and linux sees it but i cant read from it, so im going to have to find a new way.

im off now to see if i can find a small distro

---

### Post by Shazaam on 2007-06-12
Specs? HD size, memory etc.
You can network with a serial null modem cable (no idea how) if you dont have ethernet.
Another way is to pick up a usb enclosure and install that way (from your main pc).
DSL works on old hardware, Puppy has higher requirements.
I have DSL installed (and working) on a Compaq LTE 5000.:D

---

### Post by Malegnis on 2007-06-12
compaq presario 1200 64 meg of ram, 533 mhz amd, and a 6 gig HD

---

### Post by pxwpxw on 2007-06-13
**Malegnis**

you might get some ideas from the debian guide, floppies or otherwise. 

Debian GNU/Linux Installation Guide

2.2. Installation Media

[http://www.debian.org/releases/stable/i386/ch02s02.html.en](http://www.debian.org/releases/stable/i386/ch02s02.html.en)

---

