---
title: "non-networkable, cdrom-less brick of a laptop"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by drfloob on 2006-02-25
So ... I got a laptop at a garage sale today, Compaq Presario 1247, and I'd like to install the base ubuntu system (server) and add on gcc, java, and perl, to have a little portable development box / typewriter.  No X is necessary at this point, but maybe later ...

Here's the issue.  It has no networking capabilities aside from the builtin modem and the CardBus slot (for which I don't have any network cards), and the CDROM drive is busted ... hopefuly it's the drive and not something else.  There is a working floppy drive and single USB slot.  The bios is too old and will not let me boot from USB, nor can I find any bios updates.

The computer now runs WinTendo XP very slowly, but completely, so everything else seems to work just fine.

To be realistic, I've got a budget of about $20 to sink into this thing right now, but eventually I can replace some parts and dive into wireless.

How can I get ubuntu onto this system?

So far, I've come up with these possibilities:
1> Is there a way to network two Computers via modem / parallel / serial and do a network install that way?
2> I've got a 512 mb usb flash drive ... is there something of a "base install cd" I can copy over to the flash drive and use syslinux / floppy boot disk to install from that?

---

### Post by procras on 2006-02-25
> 1> Is there a way to network two Computers via modem / parallel / serial and do a network install that way?


PLIP lets you network two computers using a point to point interface with a special cable over the parallel port. But it is slow and can be tricky to get to work.

SLIP with serial cables is slower than plip but also works. You again need a special cable to connect the two boxes via their serial ports.

Easiest would be to put a network card into the PCMCIA slot on the side. Cheapest thing would be to borrow a card to put in the slot.

---

### Post by drfloob on 2006-02-25
Thanks procras: idea #1 shot down, but that's a good thing ... at least I wont be barking up the wrong tree.

Easy and cheap would work if I had any friends with PCMCIA cards, but everybody around here seems to have that stuff built in to their new-fangled nuclear-powered alienware gizmo's.  Go figure ...

I was given another idea, that being to get some ULTRA-minimal floppy-based linux distro installed (any good suggestions?), and borrowing a friends USB Haddrive, mount an iso as a loop device and Install ubuntu from that.  I'll work on both parts of that tonight, so if anyone has some helpful ideas or can explain why this could not possibly work, lemme know.

---

### Post by procras on 2006-03-01
Take the hardrive out and put it in another laptop with cdrom and/or network and install it there?

---

### Post by drfloob on 2006-03-01
yea, that is a good idea.  A tad impractical, however ... if I had an extra laptop I could take apart, I wouldn't be messing with this ancient 12 pound brick. =)

I did get ubuntu up and running yesterday.  I think I may create an article on the ubuntu wiki describing how I did it, since I searched for at least 12 hours over the course of last weekend and only found bits and pieces of what was really required to do an install like this ... and it really isn't all that complicated.

What I ended up doing was using tomsrtbt to A) partition the HD into a 700MB dummy partition and the rest as a main partition, B) attach a borrowed USB harddrive with the ubuntu iso on it, creating an exact copy of the iso to a 700MB partition (dd if=ubuntu.iso of=/dev/hdaX), and C) mounting the drive to copy vmlinuz and initrd.gz from the iso to the larger destination partition.  Then, with a grub boot floppy, I booted the system from the copied kernel and initrd on the main partition, feeding it the kernel parameters for a server install (taken from isolinux.cfg I think), then when it didn't find a CD drive and eventually asked for a device, I gave it /dev/hdaX (the harddrive copy of ubuntu ISO), and it sailed through the rest of the install.

just 2 or 3 floppy disks, a borrowed USB hard drive, and a computer (anywhere) with a network connection and a floppy drive.

Has nobody done something like this before?

---

### Post by Ptero-4 on 2006-03-01
You can take your external flash drive and put the iso in it. Then download a USB capable floppy based linux, boot off it and mount the iso as a loop device and install ubuntu off it.

---

### Post by drfloob on 2006-03-01
how???  Forgive my semi-noob-ness, but I don't get it.  Once in a linux environment, how do you initiate the installation from the mounted ISO?  I looked for that information, too ...

---

### Post by drfloob on 2006-03-02
really now, somebody has to know ... if it's even possible.

How do you start an install ... from either a mounted iso or cd ... without booting off of that media?

For example, let's say I have a form of linux running already ... from a floppy-based linux like [tomsrtbt]("http://www.toms.net/rb/") ... or maybe even easier, from ubuntu itself.

Is there an "install" script or startup program hiding on there somewhere that you can call from any *nix compliant OS?

---

### Post by drfloob on 2006-03-02
I wrote a wiki article this morning, in case someone else needs to do something similar.  [Installation/FromHardDriveWithFloppies]("https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies?action=show")

If you, Petero-4, or ANYONE for that matter, knows how to boot a mounted ubuntu iso from a linux environment such as tomsrtbt, that will save someone a big headache in the method I laid out.  Let me know or modify the wiki yourself =).

---

