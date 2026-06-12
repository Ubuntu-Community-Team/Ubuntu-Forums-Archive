---
title: "Install Gutsy Gibbon Tribe 2 on USB Thumb drive - The Easy Way"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by corey1981 on 2007-07-12
I was looking for a way to test out the Gutsy Gibbon Tribe 2 without killing my current Feisty Fawn release installed on my laptop.  I looked all over the internet about installing to a USB thumb drive, everything looked very hard and took LOTS of steps to complete.  So i figured i would try it the easy way.
I plugged the USB drive into my laptop, put the Gutsy Gibbon installation cd into the drive, and rebooted.  i did the install as normal, just selecting the usb drive instead of the hard drive,  everything worked perfectly (although slowly) and when the computer rebooted (and booted off of the usb thumb drive) i was booted into gutsy gibbon. the GRUB menu also shows the install on my hard drive. i did this using a 4gb usb thumb drive.  has anyone else had luck with this? is this a new feature in gutsy?

---

### Post by corey1981 on 2007-07-13
After removing the flash drive and trying to reboot, it would not load the grub config correctly, although with the usb flash drive connected i could boot fine into either OS.

To fix this, i did the below.

boot into the os installed on the flash drive
pull up a terminal
sudo grub
root (hd0,0)
setup (hd0)

now i can boot my machine to my old os, or the new (with the flash plugged in for the new on of course)

---

### Post by mistergq on 2007-10-26
I have a laptop that will be 3 years old in November.  In the summer of 2006, the wireless failed.  I just  added a PCMCIA wifi card no big deal.  In the fall last year, the hard drive controller failed.  Got a new laptop to replace.  Bum though because the laptop was 2 years old when it failed.  After Fiesty came out, I started playing with the idea of creating a flash drive install.  Actually made a thumb drive of a live cd.  Then I picked up a 4 gig thumb drive and installed Kubuntu Fiesty on it, worked perfectly.  Wife is very happy now because she can post on forums while watching her reality shows.

Tonight, I just installed  Kubuntu Gutsy for her on the thumb drive.  I had to do a fresh install because there was not enough room to do an upgrade.

I can't wait for an 8 gig or 10 gig reasonably priced thumb drive.  Then I will be able to do a partition for root, partition for home, and a partition for swap the way I want to do it.  I will probably be able to do upgrades in the future.

Personally, I am just happy that my soon to be 3 year old laptop continues to be used.  If we can get one more year out of the laptop, I will be happy.  If we can get more, that will be awesome. And btw: this is a solution that Microsoft cannot offer! :p

Oh, and she uses it for work stuff too, when she is home that is.  She runs open office from the laptop, saves her documents, uses a thumbdrive or emails it to herself.

---

### Post by MQMike on 2007-12-06
Question for the experts - - -

Cory1981,  Yes, I did this, also – put 7.10 on a 4 GB flash drive.  No problems, just had to configure GRUB a bit to account for the USB drive-shifting that takes place, as you also know.

But I join you here in posing a question to the Ubuntu experts, 

Why does this work so easily?  I am under the impression that installing previous versions was not so straightforward.  I did not experiment with 7.04 or with 6.06, but I suspect it would not be difficult to find the cut-off point where this will not work as Cory1981 & I have done it.

Obviously, this is a function of several things:
>  The BIOS capability to boot from USB
>  The USB drivers
>  Maybe how the OS kernel is setup (drivers, etc?)
>  Maybe the bootloader (?)

---

### Post by schmildo on 2007-12-06
What the hell?
I thought about installing gutsy like that but I figured it was too simple, linux would never let me do it without 2 days of f*&king around on the internet following half-arsed guides... So I didn't bother... aand I spent 2 days of f*$king arouond on the internet trying to get it going.

I played with it for 3 days and linux did it to me again, the gui crashed, i was forced to do a hard reset and now my usb stick isn't bootable.

I was in the middle of finding the 4 different guides i combined to get this going again, when I saw this. 

I have a 4 gig USB stick, so I'll give it a go right now.

---

### Post by MQMike on 2007-12-06
I kinda, sorta wrote up my experience at a hardware place I hang out,
[http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=12;t=6250;&#top](http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=12;t=6250;&#top)
and I referenced a How-To I wrote at Kubuntu on installing GRUB etc to UFD (Puppy, Super Grub, GRUB, GParted, all sorts of stuff to USB flash drive).

Cory1981 raises a good point though:  Why does this work, and I hope we can attract some of the Linux kernel/dev experts to shed some light on why this works on automatic pilot.

I'm with you guys on the How-To's:  in the past,  they have been anything but straightforward; some are downright unreadable.  And now, with 7.10, it seems, one can simply run the K/Ubuntu installer, pointing it at the UFD.  And, of course, deal a bit configuring GRUB afterwards, but that's not a big deal.

There is, however, the usual issue with USB flash drives (UFDs):  The wear out from re-write cycles.  Puppy is specifically engineered to avoid this, and so is a good candidate for UFD use.  Knoppix is an example of an OS that is not particularly suited to UFD.  In the worst case, the UFD will wear out.  At the same time, one can justify putting K/Ubuntu on UFD as an emergency or back-up device, or limited/special purpose portable OS device.

Whatever, huh?  It's neat and fun to mess with this, and you learn a lot doing it.

So then, why does it fly so easily . . . Hmmm ... ?

---

### Post by MQMike on 2007-12-07
To be clear here . . .

Just so we are all together here, there are two general situations where one installs Kubuntu to a flash drive:
1   Using a Kubuntu install CD, do a full installation of Kubuntu to the flash drive as one would to any drive.
Or, another case:
2   Copy just the Live CD contents to a flash drive, make it bootable, and so then you have a "Live Kubuntu USB flash drive" (just like a Live Kubuntu CD).  This requires a 1 GB flash drive.  An extension of this case is when you make the USB Live flash drive persistent by including a data partition on the flash drive where you can save your user data and settings.  There are many How-To's on making a Live USB K/Ubuntu flash drive.  I like this one:
by IntutiveNipple:   [http://ubuntuforums.org/showthread.php?t=476302](http://ubuntuforums.org/showthread.php?t=476302)

What I have done is simply an example of case 1:  
a full installation of Kubuntu to a flash drive; mine is not a Live USB flash drive installation and was not intended to be.  Issues here, mainly, are that under case 1, we have to be concerned about wearing out the flash drive with so many re-writes that the OS does while running in normal mode.  The same applies in case 2 where a persistent partition is used, and the concern would apply only to the partition used as the persistent data partition.  And that, too, is a separate subject.

---

