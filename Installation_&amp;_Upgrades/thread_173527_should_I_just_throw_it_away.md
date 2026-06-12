---
title: "should I just throw it away?"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by damianubuntu on 2006-05-10
Hi,
I've tried almost everything I can think of to try and get my last machine over to ubuntu, but the install always fails.  I get a variety of errors at different times incuding (but not limited to!):

debootstrap error, exited with code 1 (sometimes code 15 or 11)
various installation aborted for an unknown reason errors
failed to read from CD

Things I have tried so far:
reburn DVD with new ISO, md5 checked
reburn CD at 1x speed md5 checked after burn
different CDrom
different hdd
different ribbon cables, slave and master and IDE arrangements
different make of CD/DVD
linux:aspci=off and other options from F1 menu at install
unplug everything from the motherboard that I dare.

The only one I haven't yet been able to try is a network install, I have two problems with this:
1) I can't find a menu to let me specify a non CD install (despite womething I read in th forum here once, suggesting a http or second hard drive install was a possibility, though maybe that was for hoary)

2)I can't get my network card recognised, in fact (and is this perhpas part of the problem?) ubuntu claims that I have a firewire device (which I'm sure I don't though I don't really know what one is exceept for what I could get from wikipedia) and suggest that although unlikely, this could be my primary ethernet interface.  It doesn't find the same network card that Ubuntu found on a different machine automatically.

I've tried other distros, and all debian derivatives fail, though I did manage to get Mandrakee succesfully installed, but then I thought I'd rather have it all on Ubuntu and formatted the hdd :( 

Does anyone have any suggestions? PLease? or do I just give up on it as a freaked out motherboard?

---

### Post by Omnios on 2006-05-10
Did you try the older release of Debian with an older kernal I managed to get my old P2-350 running even though I could not get even the older Ubuntu releases to run on it. Think I used to  old stable with a net install.

---

### Post by damianubuntu on 2006-05-10
No, I haven't....
spec is AMD K6-2 450 with 128mb ram and whichever hdd is currently in (!) at least 3 gb.
I guess its worth a go, is there an iso I can download, or what's the score?

Cheers for teh reply

---

### Post by Omnios on 2006-05-10
This is the debian web site.
[http://www.debian.org/]("http://www.debian.org/")

 This is the download page
[http://www.debian.org/CD/]("http://www.debian.org/CD/")
You need either the first and possibly the second cd counting on what you want, think the first cd has gnome and the 2nd has some KDE stuff and extras. If you can get the network working on boot you might want to try a net install.

 As for what version you need im not shure if they have a AMD version or not. Also there is a 3.0 and 3.1 version. I think I used the 3.0 anyways you can alsways try to upgrade 3.0 if possible as well as having an older kernal.

---

### Post by Omnios on 2006-05-10
Another thing there are few things that could be holding you back from installing Ubuntu one of which is the vidio card and a few other parts and pieces that are no longer covered under the new Kernal. I know that older Mercury cards no longer work with the newer kernals so you might wnat to look into that also

---

### Post by damianubuntu on 2006-05-10
This page at Debian seems to only offer deb 3.1 r2.

Is that ok do you think, ie will it have the older kernal?

or am I missing something?

What would you think about trying warty or dapper?

---

### Post by Omnios on 2006-05-10
There is 3.0 available on some of the mirrors, some mirrors only have 3.1. As for trying an older Ubuntu not shure f it would work. This is based on the Kernal versions which debian seems to have the older versions available as compared to Ubuntu. Also think next month warty will no longer be supported when dapper coms out. Dapper will have an even newer kernal. The fact that you did get a linux running on the computer leads me to believe it may be a kernal or hardware support issue. ALso this kernal thing as new kernals are released at times they drop support for older hardware such as I mentioned with the murcery pci vid card etc.

---

### Post by damianubuntu on 2006-05-10
8) thanks for your patience 8) 

cheers

---

### Post by Jason_25 on 2006-05-10
Have you tried running memtest AND checking the disk integrity before installing?  If that doesn't turn up anything, I would guess you have a bios/motherboard incompatibility.  Try dapper if nothing else.  It has lower system requirements anyway.

---

