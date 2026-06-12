---
title: "Unstable Linux (obscenities removed, mods)"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by seanmc42 on 2006-03-14
This is like the third time that Linux has crashed and destroyed my data -
People always talk about how stable this piece of [OBSCENITY]  is....

Funny thing is, I really would like to get away from M$,
but Linux is [OBSCENITY].
Not only did it crash and require re-installation, but it wiped the partition table off of a completely seperate and unmounted HDD!!!

This is the 2nd time that's happened to me!

Why is Linux so unstable?

---

### Post by IYY on 2006-03-14
"Linux" is not unstable. But on certain hardware, there can be problems. Very serious problems. For example, I have one machine on which Linux will just not work right. It constantly crashes. However, on any other machine I've ever seen, it works perfectly. In fact, if it's running on hardware that it "likes", Linux will **never** crash. In the very literal sense of the word: I've had months of uptime, nearly a year now on one machine.

You just have bad luck. ;)

---

### Post by kassetra on 2006-03-14
[quote=seanmc42]This is like the third time that Linux has crashed and destroyed my data -
People always talk about how stable this piece of [OBSCENITY]  is....

Funny thing is, I really would like to get away from M$,
but Linux is [OBSCENITY].
Not only did it crash and require re-installation, but it wiped the partition table off of a completely seperate and unmounted HDD!!!

This is the 2nd time that's happened to me!

Why is Linux so unstable?[/quote]

Your question, as you've phrased it, you must realize, is quite potent.

Let me see if I understand you correctly:
You've attempted to install Ubuntu linux onto a previously Windows-only computer and you have written over your data a few times, and while trying to do the install you've also wiped out the partition tables?

Is this correct?

---

### Post by taurus on 2006-03-14
What is the spec of your machine?  I have installed Linux on bunch of systems and they are working just great.  I have a Linux machine running as an ftp server on a Dell 600MHz with 256MB and that baby has been on for more than 4 months...

---

### Post by KansasJoe on 2006-03-14
sounds like a problem isn't the os but somewhere between the keyboard and chair...was there something in particular you were during when it decided to crash

---

### Post by Swab on 2006-03-14
[QUOTE=KansasJoe]sounds like a problem isn't the os but somewhere between the keyboard and chair...was there something in particular you were during when it decided to crash[/QUOTE]

Probably he was in the middle of ranting about something else...

---

### Post by seanmc42 on 2006-03-14
No - forgive my lack of details as I was quite enraged when I typed it.
Here is what has happened:

I have a successfully installed Linux box. This has been  on more than one machine, with different hardware configurations.

The first time Linux wiped another partition, I had RedHat 7.1 (or maybe 7.2), and a Windows 2000 dual-boot.

Redhat crashed, and detroyed the partition table, affectively ruining EVERYTHING.

Last night, my Ubuntu 5.4 (Hedgehog) crashed, wiping itself AND the partition table on a completely different harddisk! It wasn't the windows partition, but a purely data (300GB) disk on which I had lots of multi-media.


I have had Linux also crash many times where it only caused damage to it's own partitions... running fsck at startup, and not being able to recover.

I am now running 5.10 with WinXP on a seperate disk (3 HDD's, 1 DVD).
I have WinXP on HDA, Ubuntu on HDB, teh DVD @HDC, and the BIG 300GB disk @HDD.

---

### Post by landotter on 2006-03-14
run a diagnostic on your HDD. When they start to go, the read/write gets sketchy and any OS will crash.

---

### Post by seanmc42 on 2006-03-14
landotter - Good Idea, though this has happened on > 1 machine when other OS' had no problems - although it still COULD be the HDD.
Also, the HDD (The big 300GB disk that got wiped this time) is brand new...

Any recommendations for trying to restore it?

---

### Post by evilgold on 2006-03-15
How did linux CRASH? and remove your partition table? for one thing, your partition table isnt part of linux, its its own thing. Thats why linux,bsd,windows, ect can all read each others partitions. The only way your partition table could be broken is if you did somthing to it, or you hard drive itself is bad.  I've also noticed that windows is fairly bad at figuring out if a hard disk is bad, I have a 30gb maxtor with the first 2gigs being completly filled with bad sectors, yet the only way windows gets this is if i format it and completly fill the drive (because of window's fragmentation problems).

test your hard disk very well. Also make sure that your boot loader is configured properly. There is no reason why a linux "crash" would affect your windows partition. Also...linux doesnt crash. Seroiusly, there is no linux eqivilant of the blue screen. worst case you'll get a busy box shell, or you can chroot with a live cd.

---

### Post by jason.b.c on 2006-03-16
Maybe this might help.:) :confused: 

[www.ultimatebootcd.com/](www.ultimatebootcd.com/)

;)

---

### Post by dolson on 2006-03-19
The only time that I've ever had Linux wipe OTHER drives that I stored only data on are when I am screwing about with hdparm - as root - and the DMA mode settings. Set it to the wrong one for your system, and BAM, all data is gone. The same thing would happen in Windows if you even had the ability to set hardware to any value you want in that world...

Other than that, yes, "Linux" has crashed on me before, but it's been likely due to faulty hardware or an experimental kernel/driver. In the Linux world, we call it a kernel panic. You will know if you get one.

I'd like to know how sean's system is wiping out his data... If it's hdparm-related, which wouldn't shock me, then it's a mistake you should not make more than twice... I've done it twice, and I swore up and down after the first that I'd never do it again. I hope I won't do it a third time.

---

