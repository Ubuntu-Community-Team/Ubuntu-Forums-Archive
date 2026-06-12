---
title: "Can't detect CD / DVD drive!!  Can't run Live CD !!!"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by ubuntu_seeker on 2005-03-08
> As with Array CDs 4 and 5, this release includes both the Install CD and
the Live CD.

This is scheduled to be the last Array CD release before the Hoary
Preview. As such, we'd very much appreciate anyone who can test it to do
so and file bugs on any problems you encounter.


Ok, bug / problem fix sought ;) :):

I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD/DVD drive, meaning, it could not find a driver for my CD/DVD so then I have to stop the installation.  That is, I keep ending up back at the install menu where it says that the CD drive has not been detected yet.  It asks me if I want to pick a driver from a list, and I've tried various ones "cdrom" etc. with no luck.

I've seen others post about this same problem in several places (at least 3 threads), but still there have been no replies... hoping for one soon.  :)

My hardware is: Dell XPS Gen 3 (Pentium 4 3.6 GHZ), DDR-2 RAM, SATA 7200 rpm hard drive.

The CD-ROM is a CD / DVD RW combo drive...  I believe it's an IDE drive.. listed in XP properties as "HL-DT-ST DVD+RW GRA-4120B".

MEPIS had no problem detecting my CD drive. And the drive works just fine in Windows XP SP2.

Thanks for any ideas!!! :^D.

I'd really like to be able to try out the live CD before installing Ubuntu. I'd much prefer to go with Hoary since Warty is kinda out of date by now.

I wish I could install Ubuntu    ](*,)

---

### Post by gungaden on 2005-03-09
Try posting to the forum at this URL.....it is for Hoary issues:

[http://www.ubuntuforums.org/forumdisplay.php?f=21](http://www.ubuntuforums.org/forumdisplay.php?f=21)

---

### Post by ubuntu_seeker on 2005-03-09
[QUOTE=gungaden]Try posting to the forum at this URL.....it is for Hoary issues:

[http://www.ubuntuforums.org/forumdisplay.php?f=21](http://www.ubuntuforums.org/forumdisplay.php?f=21)[/QUOTE]

Ha!  I already did ;) :)....  and to think that one guy was giving me flak for cross-posting my problem too much... *laugh*.  ;).. here someone else is actually urging me to do it...  you can never please everyone ;)

---

### Post by robbo312 on 2005-03-10
[QUOTE=ubuntu_seeker]Ok, bug / problem fix sought ;) :):

I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD/DVD drive, meaning, it could not find a driver for my CD/DVD so then I have to stop the installation.  That is, I keep ending up back at the install menu where it says that the CD drive has not been detected yet.  It asks me if I want to pick a driver from a list, and I've tried various ones "cdrom" etc. with no luck.[/QUOTE]

I have this issue (also with a Dell), if you do a dmesg on the terminal and if you get something simular to this...

ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe

then thats looks to be the reason, I believe it's because the SATA driver is loaded before the ide-generic drivers..  Didn't get around it, but I installed Ubuntu by booting up from a gentoo CD, partitioned/formatted the drives and then copied the Ubuntu CD/DVD to one of the partitions.

On booting from the Ubuntu CD I mounted the said partition to /cdrom and then continued with the install.

Once installed I still got the same issue but followed this link to solve...

[http://kerneltrap.org/node/3971](http://kerneltrap.org/node/3971)

---

### Post by ubuntu_seeker on 2005-03-11
> I have this issue (also with a Dell), if you do a dmesg on the terminal and if you get something simular to this...

ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe

Bingo!

I just did dmesg and got *exactly* the same thing... but boy I'm not sure your fix applies to booting the Live CD!!  eheh... since your fix involves installing the CD to HD first.... oh well... maybe a future Live CD will correctly handle my system!  (like mepis and knoppix do.. eheh ;)

---

### Post by robbo312 on 2005-03-12
[QUOTE=ubuntu_seeker]Bingo!

I just did dmesg and got *exactly* the same thing... but boy I'm not sure your fix applies to booting the Live CD!!  eheh... since your fix involves installing the CD to HD first.... oh well... maybe a future Live CD will correctly handle my system!  (like mepis and knoppix do.. eheh ;)[/QUOTE]

Yep your right it wasn't for the LiveCD it was for installing Ununtu (came across your message when trying to find a fix, and only quickly read your post!).

---

### Post by kahping on 2005-04-03
have you tried going into your BIOS and seeing if changing to Combination mode helps?

motherboards that support S-ATA have BIOS settings allowing them to specify the mode the controller should operate in, i think. there should be AHCI, RAID, SATA Only, Combination, etc...

somebody correct me if i'm wrong on this.

kahping

---

### Post by ubuntu_seeker on 2005-04-04
These things have been discussed in similar threads...:

our Dell machines don't have that many modes to choose from in the BIOS... basically AHCI (which you don't wanna switch away from or you lose the speed of command queueing), regular ATA, and SATA / PATA "combo mode" where if you run with that, yeah you may be able to access Ubuntu, but then your Windows XP partition may be not usable... so really those BIOS tricks won't help us... and besides we don't wanna have to muck with the BIOS just to have a CD drive detected :), but thanks for tryin' to help  :)

[QUOTE=kahping]have you tried going into your BIOS and seeing if changing to Combination mode helps?

motherboards that support S-ATA have BIOS settings allowing them to specify the mode the controller should operate in, i think. there should be AHCI, RAID, SATA Only, Combination, etc...

somebody correct me if i'm wrong on this.

kahping[/QUOTE]

---

