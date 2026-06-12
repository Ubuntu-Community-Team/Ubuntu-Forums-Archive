---
title: "Recovery disk from USB"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Clueless24 on 2009-12-12
I bought a new netbook but it has a very small hdd. It came installed with ubuntu, but I didnt know how to use it so I installed win xp from a USB drive (Netbooks dont come with cd rom drives)

SO now unfortunantly, the xp is taking up 3.5gigs of the 4 gig max hdd...I want to go back to ubuntu because it took up less space and I can LEARN to use it.

But my question is, my recovery disk is on CD- do I need to do anything special with my USB drive, like format it, make it bootable or anything? or when I put the linux recovery cd info onto the usb drive, and boot up from my netbook, will it automatically run and start the recovery process????

Its been driving me nuts for days and all I am getting is BS answers like "Oh well get a real laptop" gr8 thx that answer doesnt help...I wanted the netbook for a specific purpose so if you have something helpful to say please say it!!

---

### Post by gordintoronto on 2009-12-13
Did the manufacturer give you any info about the recovery CD?

You have access to another PC?  One option would be to download the Ubuntu Netbook Remix, and put that on a USB drive.  I think the Ubuntu web site has instructions on how to do that.

Lots of people know how to deal with an ISO, which is a CD image, but not so much with an actual CD....

---

### Post by Clueless24 on 2009-12-13
the little ubuntu booklet that came with everything tells you how to recover using an external CD drive but NOT a USB. :( and I cant just copy all the recovery files onto usb it will just say boot failed.

---

### Post by darkod on 2009-12-13
> **Clueless24 said:**
> the little ubuntu booklet that came with everything tells you how to recover using an external CD drive but NOT a USB. :( and I cant just copy all the recovery files onto usb it will just say boot failed.

You are right, if you just copy the files there will be no bootloader on the usb stick. One option is to download the Ubuntu Netbook Remix or Ubuntu Desktop 32bit version, but that would have hard time working on 4GB too.
Second option is to create a usb stick from your recovery cd but that will take some tweaking around to create the boot process. If you feel up to it I can basically give general instructions. That recovery cd version of ubuntu might have been stripped down to work better on 4GB.
Another option is to actually download Xubuntu 9.10 32bit, that is like light version of Ubuntu for older computers or with little hdd space like your own. The ubuntu website says that it needs only 1.5GB of hdd space to start.

---

### Post by Clueless24 on 2009-12-13
well I've been using a HP formatting utility that claims to make your USB bootable, all you do is format it with that util and then put your iso set up files in the "componants" directory but even when I did that,.....same thing, "boot failed"

---

### Post by Clueless24 on 2009-12-13
k i know this might sound like a dumb question but can I use WINTOFLASH to make a bootable restore usb drive? its the only application I have found so far that actually makes my usb drive bootable.

---

### Post by darkod on 2009-12-13
> **Clueless24 said:**
> k i know this might sound like a dumb question but can I use WINTOFLASH to make a bootable restore usb drive? its the only application I have found so far that actually makes my usb drive bootable.

I don't know, I haven't used it.
Unetbootin can create bootable usb stick from ubuntu/xubuntu ISO image.
Also, there is something called GRUB4DOS that allows to put grub bootloader on your usb stick, and then you can adjust it to boot your recovery files copied on the stick. That is the procedure I was talking about.

PS. One option is: create ISO from your recovery cd, and use unetbootin to make bootable stick with that ISO. Or as said before, use Xubuntu image if you want to.

---

### Post by Clueless24 on 2009-12-13
how do I turn my recovery files into an .iso? I downloaded that unetbootin thing but when I point it toward my D drive to read the recovery cd...obviously there is no ISO file in there and I dont know what file to point it to

---

### Post by darkod on 2009-12-13
> **Clueless24 said:**
> how do I turn my recovery files into an .iso? I downloaded that unetbootin thing but when I point it toward my D drive to read the recovery cd...obviously there is no ISO file in there and I dont know what file to point it to

You'll need another windows pc with cd-rom for that. Put the cd in, open the burning software that you're using on that pc, and find option that sounds like Create Image From Disc, or similar. That should create ISO image from the cd.

---

### Post by Clueless24 on 2009-12-15
nothing i tried was working (unetbootin or whatever its called, the usb creater from the restore cd)

so I gave in and finally bought an external cd drive. Should hopefully be here in the next week or sooner i hope.

---

