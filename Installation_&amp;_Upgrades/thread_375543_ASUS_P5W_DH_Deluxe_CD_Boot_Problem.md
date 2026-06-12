---
title: "ASUS P5W DH Deluxe CD Boot Problem"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by lukej on 2007-03-03
Let me start by saying that this isn't an Ubuntu specific problem, nor is it a Linux specific problem.  I noticed the same type of behavior when I tried to boot from the gparted live CD, as well as when I tried to boot from the partition magic CD.

What happens is that the BIOS loads, detects all of the IDE devices, including the CD-ROM drive.  It will then proceed through the boot order and it will begin booting from the CD-ROM (an NEC 3250).  With the case of Ubuntu, it gets all the way to the splash screen, which I disabled in later runs to see what was actually happening.  Basically the loader gets to the point where it tries to load the driver for the CD drive and it can't.

It's the same issue with the partition magic CD also, which comes with a version of DR-DOS to load up the program.  The driver fails to load, it tries to swtich to drive Y, but it can't.

I used this same exact drive on my last system and had no such issues.  I believe it to be motherboard/controller specific.  Can anybody give me any ideas to help me with this problem?

If it helps at all, I'm running a RAID0 array of 2 SATA drives on the Asus EZ-Raid ports (basically set a jumper and you've got RAID).  And I also have another SATA drive attached to one of the other ports, which I'm attempting to install Ubuntu on.  I've already successfully installed Windows XP, with no issues (other than the stupid 127GB limit of < SP2...)

I appreciate your help in advance.

Thanks,
Luke

---

### Post by Grimvant on 2007-03-04
I have the same motherboard and have not yet been able to install Ubuntu. I have tried Dapper, Edgy, and ubuntu ultimate ([http://ubuntusoftware.info/)](http://ubuntusoftware.info/)). After a failed attempt at installing Ubuntu ultimate I filed a bug report through ubiquity. I received a response which follows:
"*** This bug is a duplicate of bug 86427 ***

Thanks for your report. I tracked this down via bug 86427, so there'll
be a fix in my next upload.

** This bug has been marked a duplicate of bug 86427
   Ubuntu installation crashed at ca. 80-82%

-- 
installer crashed @about 90% through
https://launchpad.net/bugs/83403"

Below are a few other related responses:
"ubiquity (1.3.23) feisty; urgency=low

  * Enable migration-assistant by default. Replace --migration-assistant
    option with --no-migration-assistant.
  * Add a console-setup-apply script rather than hacking console-setup's
    post-base-installer script (which is being renamed and changed in ways
    that aren't appropriate for ubiquity).
  * Make sure we never try to remove the kernel package corresponding to the
    running kernel (LP: #86427).
  * Automatic update of included source packages: base-installer
    1.70ubuntu5, hw-detect 1.45ubuntu2, partman-base 100ubuntu5.

-- Colin Watson <cjwatson@ubuntu.com>  Wed, 28 Feb 2007 14:16:58 +0000

** Changed in: ubiquity (Ubuntu)
       Status: Fix Committed => Fix Released

-- 
Ubuntu installation crashed at ca. 80-82%
https://launchpad.net/bugs/86427"

and:
"upload made yesterday. installation has gone. everything ok.

Thank you and best regards,
gmx99


>From: Shark <simdet@gmail.com>
>Reply-To: Bug 86427 <86427@bugs.launchpad.net>
>To: [email]gmx99@hotmail.com[/email]
>Subject: [Bug 86427] Re: Ubuntu installation crashed at ca. 80-82%
>Date: Thu, 01 Mar:11:52 -0000
>
>Thank you, I wait your next upload (more or less, when?).
>Again Thank you.
>
>--
>Ubuntu installation crashed at ca. 80-82%
>[https://launchpad.net/bugs/86427](https://launchpad.net/bugs/86427)

_________________________________________________________________
Die neue MSN Suche Toolbar mit Windows-Desktopsuche. Suchen Sie gleichzeitig 
im Web, Ihren E-Mails und auf Ihrem PC! -  [http://desktop.msn.de/](http://desktop.msn.de/) Kostenlos 
downloaden!

-- 
Ubuntu installation crashed at ca. 80-82%
https://launchpad.net/bugs/86427"

I am not really sure what all of it means other then the comment that it will be fixed on the next upload. Perhaps it will make more sense to you.

---

