---
title: "Deeply Weird install running 2 days +"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by GordSellar on 2005-09-26
Um, I have been trying to install various versions of Ubuntu on my old Thinkpad... I think it's an i-series, from late 2001, maybe i-1100 or so... (I don't know the exact model, tho I could find out... but since it's "installing " right now, ie. occasionally reading from the CDRom, I don't want to lift it and look under right now. 

Anyway, here's the weird thing. Every time I try to install, I need to boot up with the Windows CD -- the Ubuntu disc won't boot it unless I boot up with Windows, first, and format the C drive. So I do it, I swap in the Ubuntu CD, and reboot. 

And sometimes it started to install, and others times it didn't. But now, the farthest I've come so far, it's been "installing" for about 24 hours or more. By "installing" I mean it kind of sits for an hour, then the CD spins a little and it advances a little, and then it sits for an hour more. The stage it's stuck at right now is at 78% -- no, wait, 80% -- of "Scanning CD-ROM". Now, it's the Nth time I've done this, and the first time I've gotten anywhere, really. I'd be tempted to say it's the burn except my other computer's DVD-Rom drive reads it fine, and finds all files intact... and this is also my Nth copy of the disc image to a disc. And it can't be the CD-drive because Windows installs fine on that same CD-ROM drive. 

It's still sitting there, stuck at 80%, and I wonder what I should do. Is it possible Ubuntu just hates my laptop? Is it possible I could install something simpler and then expand it from a command line or something? What can I do? Because frankly, I'm starting to wonder if it will ever be possible for me to install Ubuntu on this laptop at all! Which, you know, is weird, considering that I read somewhere here that IBM hardware usually works okay with it. 

Thanks for any advice you can offer, guys.

---

### Post by mlomker on 2005-09-26
> format the C drive. So I do it, I swap in the Ubuntu CD, and reboot. 

Have you checked the boot order in the BIOS?  If hard disk comes before CD then it could do that.

> 
reads it fine, and finds all files intact... and this is also my Nth copy of the disc image to a disc. And it can't be the CD-drive because Windows installs fine on that same CD-ROM drive. 


Tried booting the Ubuntu disc on another box?  Tried booting a Knoppix or Ubuntu liveCD disc on your laptop?  I've always found Knoppix to be a good hardware test.

> 
know, is weird, considering that I read somewhere here that IBM hardware usually works okay with it. 


I wouldn't say that.  It would seem that many of the older IBM machines will only run old versions of linux (2.4 kernel) or else the keyboard and/or USB ports won't work.  I'm not sure about your specific model.  I'd recommend searching on Google for **model# linux** and see what other people have installed on it.

---

### Post by GordSellar on 2005-09-26
Ah, okay, thanks very much! 

I will try as you have suggested. But I guess if it needs 2.4 or older, I'll have to go with something else other than Ubuntu? (Ubuntu doesn't come with 2.2 or older, does it?)

---

### Post by GordSellar on 2005-09-27
By the way: I haven't got a spare PC to boot with this disc, but then again, I've had the same problem with three discs burned from different downloads; and the burner is working fine these days. So I don't think it's a disc problem. 

I checked the boot order and it's CD, HD, Network, Floppy. 

The laptop keeps haltingly scanning the CD. I'll try a Knoppix disc, but I think the PC itself is fine since I've repeatedly installed Windows XP on it lately with no problem at all. 

Hmmm. If I install just the basic system (ie. type "server" at the boot menu when it boots with the CD) can I install the rest manually afterward?

Wait, it seems even that isn't working. Man! This is a strange one. I'll get on the Knoppix thing ASAP.

---

### Post by mlomker on 2005-09-27
> Hmmm. If I install just the basic system (ie. type "server" at the boot menu when it boots with the CD) can I install the rest manually afterward?


Yes, you can do that.

> 
Wait, it seems even that isn't working. Man! This is a strange one. I'll get on the Knoppix thing ASAP.

That'd be a good test.  Ubuntu requires a 2.6 kernel, so you'd have to run something else if that turns out to be the problem.

---

