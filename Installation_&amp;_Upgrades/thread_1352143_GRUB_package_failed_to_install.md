---
title: "GRUB package failed to install"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by PFree on 2009-12-11
Hi,

This is my first attempt at using Linux of any kind, so I must admit my experience level is zero o to nil, at best.

I'm trying to install ubuntu 9.10 on a newly built system. The install gets to 94%, attempts to install GRUB, and fails with error message: "The grub failed to install into /target/. Without the GRUB boot loader, the installed system will not boot."

I'm not sure what's causing the problem. I've tried several configurations of the HDD's including RAID 0 (full volume), IDE - which I REALLY don't want to use anyway, and finally I configured a RAID 0 5Gib partition and tried installing again.

Prior to (last) installation I used Live CD to create a boot partition (ext3) at 8Gib. Then, ran the installation. The install ran to the same point and died with the GRUB error. The MBR partition is there, but if the pointer/s to get to it are wrong, I have no idea how to rectify the problem.

I'm fairly sure the problem resides with HDD configuration, but for the past 2 days I haven't been able to find a solution. It seems everybody using ubuntu has it installed as a secondary operating system, which makes finding information on how to install it as a primary/stand alone operating system hard to find, if it exists.

If anybody has any experience with installing ubuntu as a primary OS on a new box I would really appreciate any direction to documentation or help you would share with me.

Regards.
Paul

---

### Post by darkod on 2009-12-11
> **PFree said:**
> Hi,

This is my first attempt at using Linux of any kind, so I must admit my experience level is zero o to nil, at best.

I'm trying to install ubuntu 9.10 on a newly built system. The install gets to 94%, attempts to install GRUB, and fails with error message: "The grub failed to install into /target/. Without the GRUB boot loader, the installed system will not boot."

I'm not sure what's causing the problem. I've tried several configurations of the HDD's including RAID 0 (full volume), IDE - which I REALLY don't want to use anyway, and finally I configured a RAID 0 5Gib partition and tried installing again.

Prior to (last) installation I used Live CD to create a boot partition (ext3) at 8Gib. Then, ran the installation. The install ran to the same point and died with the GRUB error. The MBR partition is there, but if the pointer/s to get to it are wrong, I have no idea how to rectify the problem.

I'm fairly sure the problem resides with HDD configuration, but for the past 2 days I haven't been able to find a solution. It seems everybody using ubuntu has it installed as a secondary operating system, which makes finding information on how to install it as a primary/stand alone operating system hard to find, if it exists.

If anybody has any experience with installing ubuntu as a primary OS on a new box I would really appreciate any direction to documentation or help you would share with me.

Regards.
Paul

OK, lets clarify something first. Are you trying to install on raid or you tried raid after no-raid install failed?
If you are installing on raid the standard desktop cd won't do. You need the alternate install cd. I would also recommend to consider LVM if ubuntu is your only OS, but because this is your first attempt you might skip that.
The beauty of LVM is that you dedicate your whole hdd to it, but it allows to dynamically change partition sizes without formatting.
Alternate install cd here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by joes7 on 2009-12-11
Let's try something. Download the latest version of GRUB and replace your old Grub with it (on the disc, if you are using re-writable). Make sure that files have the same name, so backup before attemping. 

Good luck, and Merry Christmas:D!

---

### Post by PFree on 2009-12-11
> **darkod said:**
> OK, lets clarify something first. Are you trying to install on raid or you tried raid after no-raid install failed?
If you are installing on raid the standard desktop cd won't do. You need the alternate install cd. I would also recommend to consider LVM if ubuntu is your only OS, but because this is your first attempt you might skip that.
The beauty of LVM is that you dedicate your whole hdd to it, but it allows to dynamically change partition sizes without formatting.
Alternate install cd here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Thanks for the reply Darkod.

I tried installing both ways, multiple times. I shouldn't even have even mentioned using IDE as an option because if I had to go that root I'd just install XP from my failed system.

This mainboard/cpu on the new build is designed to function best using RAID. It's a Intel DQ45CB M/B and Q8200 Core 2 Quad CPU.

I misunderstood the documentation on the alternate install package... I really appreciate you pointing that out. Thanks! Now, that raises another question...

I read somewhere over the past few days that a newbie like myself would be better off installing the 32 bit version over the 64 bit version. I'm not sure how much more difficult it could be since I already don't know what I don't know. I'm starting from scratch regardless, learning Linux. Given the situation, it seems to me that I should just bit the bullet and go for the 46 bit version. What say you? Unforeseen problems?

Regards,
Paul

---

### Post by darkod on 2009-12-11
> **PFree said:**
> Thanks for the reply Darkod.

I tried installing both ways, multiple times. I shouldn't even have even mentioned using IDE as an option because if I had to go that root I'd just install XP from my failed system.

This mainboard/cpu on the new build is designed to function best using RAID. It's a Intel DQ45CB M/B and Q8200 Core 2 Quad CPU.

I misunderstood the documentation on the alternate install package... I really appreciate you pointing that out. Thanks! Now, that raises another question...

I read somewhere over the past few days that a newbie like myself would be better off installing the 32 bit version over the 64 bit version. I'm not sure how much more difficult it could be since I already don't know what I don't know. I'm starting from scratch regardless, learning Linux. Given the situation, it seems to me that I should just bit the bullet and go for the 46 bit version. What say you? Unforeseen problems?

Regards,
Paul

Go with 64bit, no problem.
Another thing, if you tried first with raid, some raid settings would already be on the drives and 9.10 can "see" them. It makes it confused and sometimes even does not "see" the drive as destination at all.
So... Make up your mind if you want to go with RAID0 or not. Personally I think you will be fine installing on raid.
If raid YES, try the alternate install cd but be warned the installer is text based. You still end up with desktop GUI but the install process is good old text based linux. :) Another thing to learn. :)
If raid NO, boot with desktop cd, Try Ubuntu option, open terminal (in Applications-Accessories) and execute:
sudo apt-get remove dmraid

That should remove any traces of raid settings on the drives. After that boot with the cd again, select Install Ubuntu and you should have no problems installing on single drive, not raid. Of course, if you decide not to go with raid disable any raid settings in BIOS before trying the above command.

---

### Post by PFree on 2009-12-11
Thanks for the advise Darkod. I'm going with 64 bit w/raid. I'll post on how it goes. Should be interesting!

---

### Post by darkod on 2009-12-11
> **PFree said:**
> Thanks for the advise Darkod. I'm going with 64 bit w/raid. I'll post on how it goes. Should be interesting!

Just so you don't say that I'm lying to you. :) Read here:
[http://ubuntuforums.org/showthread.php?t=1351580](http://ubuntuforums.org/showthread.php?t=1351580)

---

