---
title: "Problems With Dual-Boot Install"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Lull The Conqueror on 2008-07-11
All right, I've been lurking about the forums trying to resolve this and getting nowhere, so I figured the best course of action would be to come right out and ask.

For a month or two, I had my system set up to nicely allow dual-booting in Ubuntu 7.10.X (whatever the last version was) and Windows Vista (not because I particularly care for it, but because there are some programs I need to be able to run for college work).  Then I tried to upgrade to 8.04 using the Update program, and the trouble started.

The update hung about halfway through, and after letting it sit for about half an hour hoping it would resolve itself, I did a hard reset.  The GRUB loader still showed the old version, and naturally when I tried to boot to that it didn't work.  Actually, it did work, but when I logged in all I got was the desktop background and a cursor.  So for a while I just used Windows, with a clean install of Ubuntu 8.04 running on my laptop.  Earlier today I decided that having half my main hard disk inaccessible and useless was not a desirable state of affairs, so I resolved to get 8.04 running on that partition.

I'd chronicle all the different ways I tried to do it, but it's probably immaterial; suffice it to say that the last thing I tried to do was reformat the ext3 partition and do a clean install.  I tried to do this several times, sometimes just selecting "Install Ubuntu" from the Live CD and sometimes starting a Live session and trying to install from within that, but every time the dialog box disappeared somewhere between 30% and 40% completion.  When I tried to boot into Windows, GRUB wouldn't start (it gave me Error 15, if that's important), so I consulted some other forums using my laptop and installed the Windows boot loader.  Then I tried installing Ubuntu two or three more times, but the same thing kept happening.

So basically at this point I have a computer that runs fine in Vista, but has half of C: inaccessible, and nothing I can figure out will get Ubuntu to install on that partition.  Every install attempt was from the Live CD.  Is there anything I can do short of reformatting the entire disk and starting fresh to get it to install?  I really liked being able to boot into Ubuntu for general computing and Vista for classwork and some games.

Some system specs that might be important (I really don't know much about this stuff, can you tell?):
Motherboard: Gigabyte GA-MA790FX-DS5
Processor: Athlon 64 X2 6400+ (dual-core)
RAM: 8GB
Main HD: Western Digital Raptor 150GB

---

### Post by Herman on 2008-07-11
I have had the problem of the install stopping while installing software too, it has happened to me a few times and every time it has happened to me it seemed to have been cause either by a scratched or dirty CD/DVD or a dirty optical lense. Cleaning the optical lense and/or the media seems to do the trick for me.
I'm not saying that's definitely your problem, only that it seems that way to me. Yours might be entirely different.
Anyway, it even happened to me once when I was making an installation guide, so I included how to clean the CD/DVD drive as part of the guide, [Hardy Heron Beta / Gutsy Gibbon Graphical Installation C]("http://www.herman.linuxmaniac.net/p22.html").
Apart from that I don't know.

---

