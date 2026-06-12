---
title: "moving hard drive"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by mudlark on 2007-01-23
Hi,
i've an IDE HDD with 6.02 on a Pentiumn 3 machine.

In would like to move the hard drive into a new box with intel core2 duo processor and 945 chipset. Am I likely to have any problems or will the drive boot in then new box?

Thanks for any advice.
Mike.:)

---

### Post by logos34 on 2007-01-23
> Am I likely to have any problems

Sure, all kinds!  Think about it for a sec: you're moving an old version of Ubuntu installed and configured on old hardware to a new machine with bleeding edge dual-core cpu, recent chipset and new graphics.  I'd be surprised if anything worked.  Besides, you need a kernel compiled with SMP for your processor, as well as new lan, audio drivers, etc.  

The only way is a new install.  You'll have to backup all your personal files.

Download the LiveCD (x86 or AMD64 or both) and take it for a test spin.  You might want to get the (text-based) alternate install cd as well, just in case you have trouble with the other during install.  And do verify the md5sums of the dl'd isos, burn them slowly and run the cd integrity check--so many problems can be avoided with these simple steps.

---

### Post by mudlark on 2007-01-23
Thanks for that!

I've only ever migrated windows hdds and have had few problems.

I just moved my son's hdd from the machine i'm using now to an AMD 64 dual core with no problems.

Ah well start from scratch.. again..
Thanks again,
mike.

---

### Post by logos34 on 2007-01-23
> I've only ever migrated windows hdds and have had few problems

Yeah, a about a year agoI tried booting from an old 3,2GB Windows 95 disk on a brand new computer and it worked--barely.  On the other hand, reading from the drive in Windows XP Pro worked fine. But that's windows.  

> I just moved my son's hdd from the machine i'm using now to an AMD 64 dual core with no problems
His hdd has an ubuntu on it and there were no problems???  Hard to believe.  But at the very least it's not running optimized for dual core--that has to be done at install time (linux detects your hardware and does it for you).

---

### Post by mudlark on 2007-01-23
No.... My son's HDD had XP on it and I moved the HDD to a new box.

I'm having a sulk now. i've just got the machine working well such that I've decided to junk windows and now I can't migrate to new hardware. Doh!

I've still got alot to learn.
M.

---

### Post by logos34 on 2007-01-23
Oh, I see.  

Well, good luck to you.  You might want to do search of the forums and/or wiki for your board and its various controllers--you know, to get the heads up on any potential problems (hopefully none!) with sata, ethernet, etc.  (e.g. there are issues with the gigabit lan controller on the i945-based Asus P5BL or N series)

---

### Post by mudlark on 2007-01-24
Hi all those folks out there.

I decided to do a fresh install. I'm running kubuntu 6.10 from a cd ROM that I downloaded back in November 2006.

just for those thinking about using some of the latest gear I have an ASUS P5B-VM motherboard and a DVd-Rom running on the IDE cable. The HDD is SATA using an intel chipset SATA port. Sound is OK off the board and the LAN port works.

There are no obvious hardware/driver failures.
I'll post any problems.

cheers,
Mike.

---

### Post by mudlark on 2007-02-07
For all those interested, i have fitted a sata dvd rw drive and it works well

---

