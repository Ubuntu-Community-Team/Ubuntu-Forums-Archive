---
title: "Unable to boot after installation with SATA and IDE"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by pureblood on 2008-01-11
I am posting this problem, for which I have a solution, because I believe is extremely serious since it prevents the booting after installation.
My computer has two hard drives, a fast SATA drive (the one with the small connector) used for the operating system and an older ATA drive (that is an IDE drive with the old large connector) used exclusively only for data storage. I don't have the computer available now but i believe the first drive is recognized as sda and the second one as hda. After booting the Gutsy installation cd without problems and installing the system on the SATA drive, I reboot the machine. At that point grub is unable to boot the system.
The problem is simple. The installation decided the SATA drive was the second drive and put on grub the line (hd1,0) instead of the line (hd0,0) preventing the booting of the system. Also these two lines were added to /boot/grub/menu.lst
map (hd0) (hd1)
map (hd1) (hd0)
The result is very simple. The system does not boot and a beginner would never be able to understand why making the claim that linux is easy to install a complete lie. Moreover, it seems that the two aforementioned line are also responsible for making Windows (that I had on the SATA drive) unbootable as well. Basically a complete installation disaster.
I believe the same problem is described on the following forum:
[http://forums.fedoraforum.org/archive/index.php/t-348.html](http://forums.fedoraforum.org/archive/index.php/t-348.html)
Even if the amount of people having this combination of SATA and IDE drive is small I think this bug cannot be allowed to be overlooked by whoever is responsible for the automatic initialization of /boot/grub/menu.lst
Since I don't know who this person is I hope by posting this message to raise some awareness of the problem.

---

### Post by DavidTangye on 2008-01-11
As I understand it, IDE's are chosen by BIOS ahead of SATA. Therefore the IDE is normally hd0, and the SATA is hd1 in grub terminology. My guess is that grub is on the boot sector of the IDE, as that is where the bios will boot it. Grub could then boot ubuntu off the SATA, ie hd1 without problem, but it does the drive switch for the sake of Windows.

Can anyone confirm that my understanding is correct?
Where in menu.lst is the map switch appearing? Can you post it up here?

I agree that this stuff is not simple and is beyond most people.
 It would probably have been OK had you installed onto the IDE, but I understand that for performance reasons you would probably not want to do this. I guess that mixing IDEs and SATAs is a pain.

---

### Post by Therion on 2008-01-11
I run a dual-drive system myself with mixed drives: SATA drive for the OS'es (I dual boot Ubuntu/WinXP), and a secondary PATA drive for data storeage.  It's not a problem to run with mixed drives, once everything is correctly installed.  

The install solution for me was to simply disconnect the PATA drive (I physically unplugged the power and data cables) before installing Ubuntu.  Once the install was complete I simply reconnected the PATA drive, mounted it, and all was good from that point on.

I can't positively confirm that **DavidTangye's** explanation is correct, but that is my understanding of how things work as well: IDE drives have some kind of boot-device priority in the BIOS for whatever reason.

---

### Post by logos34 on 2008-01-11
Yep, you guys are right--grub is programmed to priviledge pata over sata.  It checks the IDE channels first for hard disks and, if any are present, assumes the first one is the boot drive, regardles of the actual Bios hard disk boot priority.  (Remember: grub predates the sata interface).  Sometimes it gets the order right, though.  

It's my one gripe with grub, they've never updated it for the 'sata era'.  (Grub2 may fix this, but I have yet to try it out.  Others are already experimenting with it--there are a few posts in the forum).

pureblood,

Can you get it to work if you switch the hard disk boot order in the Bios (IDE drive first)?

---

### Post by pureblood on 2008-01-20
Thanks to all the people that replied to my post to shed some light on what happened. I don't have the machine with me (it is about 6000km far from me now) but I can tell what I remember:
1) The BIOS settings are to boot the SATA drive first, so the BIOS does not choose the PATA as the primary hard drive.
2) Grub is installed on the SATA drive (I guess it doesn't really matter much, once it starts does it even remember?)
3) Grub recognizes the SATA drive as hd0 and the PATA drive as hd1 (does it read that from the BIOS? I don't know)
4) During the installation process in the menu.lst file the booting was believed to happen from hd1.
Who decides the mapping of the drives at installation? Grub seems to me to run fine with the BIOS settings. The whole issue seems to be at installation. Can anybody shed some light on that?
This post might be also interesting: [http://linuxgazette.net/141/anonymous.html](http://linuxgazette.net/141/anonymous.html)

---

