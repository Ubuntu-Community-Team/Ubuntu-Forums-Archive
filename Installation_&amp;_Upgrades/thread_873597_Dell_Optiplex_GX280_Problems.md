---
title: "Dell Optiplex GX280 Problems"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by Lord C on 2008-07-29
Having some major problems on this Dell.

I had a Gutsy live CD on me, which loaded up fine. But I want to setup a webserver, with no GUI.

So I downloaded ubuntu-8.04.1-server-i386.iso (correct checksum: 7232c6004ba438890cd09aded162dc8e).

I tried booting from USB using unbooting, got to the stage where it was looking for packages and it 'Couldn't find CD-Rom'.
So I burnt the cd-rom, inserted it, and it installed some packages before giving me 'Coulnd't find a suitable kernal' error.

So I restarted, with only the CD Rom in.
Now after selecting English and Install, I don't even get to the installer stage. I just see;
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1).

I have tried re-burning the disk at 2.4x speed. 

I did a Integrity test on both discs and they both came back with a problem :s

The ./dists/hardy/main/dist-upgrader/binary-all/hardy/tar.gz file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.

On the other disc is was ./dists/hardy/main/binary-i386/Packages file failed the MD5

I'm currently re-downloading the ISO. There shouldn't be anything wrong with the CD-Rs, they are Verbatim.
Any ideas? Could possibly be the crappy hardware?

[Edit][I]Re-downloaded from a different source, and burnt with a different program (clone-cd instead of imgburn), at a different speed (4x).

All seems to be going well this time.[/I][/Edit]

---

### Post by Spitphire on 2008-10-14
How many hard drives can the Dell Optiplex GX280 hold? What type of HD does it support (sata, etc..)?

I think it's a great choice for a home server.. just curious about drive space..

---

### Post by Lord C on 2008-10-16
It has a couple of SATA connectors, and the usual two IDE ribbons.

So I suppose you could have 10 HDDs if needed.

But I highly discourage the purchase of Dell GX280s. They are ****.
They never last more than 3 years, either Dell has some kind of 'upgrade feature', or they used really cheap hardware.

---

### Post by Spitphire on 2008-10-17
LOL.. I read your reply a little too late.  I just received a used one.  It's the slim one though and not the desktop edition.  Installation of ubuntu went great, it only has one sata connection, but it has IDE so i'm happy.  Going to put two more hard drives inside. I have to squeeze them in somehow.. should be entertaining how it looks in the end..

Great machine so far, hope it doesn't fail on me.  It's mostly just a glorified 'headless' NAS for me..

Thanks,
Spit

---

### Post by Lord C on 2008-10-17
Just take a look inside and make sure the caps arn't learking already.

That, and be careful with the CPU, when the the useage gets over 0.25 the fan turns up - at this point it can get stuck on 'load mode'.

When the system has completely failed, the fan will just keep getting loader and loader, until you have to turn off the PC for fear of waking the neighbours.
It's a good way of knowing when they server has crashed though - since usually 'loadmode=fail'.

Goodluck with yours lol. I'm on my third and final dell.

---

### Post by Spitphire on 2008-10-19
woah, sounds great! hah.. thanks for the warning.

---

