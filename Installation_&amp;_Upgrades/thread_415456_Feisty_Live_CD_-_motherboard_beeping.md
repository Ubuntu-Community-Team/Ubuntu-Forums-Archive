---
title: "Feisty Live CD - motherboard beeping"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by MartynM on 2007-04-20
When booting from the Feisty Live cd my motherboard's (ASUS P4C800) speaker beeps continuously but not with any sort of rhythm so I don't think it's a hardware error.

There appears to be a bug report of something similar happening on a DQ965COEKR motherboard Bug ref 80535 ( https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535")  I don't think it's related to the quiet boot though as that report is suggesting, I turned quiet boot off and the beeping remains.

I can't find a report of anybody else having this issue. I'm intending to do a clean install partly because my Edgy install wont do a dist upgrade, but mainly because i simply want a fresh system again. Does anyone know whether it's likely to be safe to proceed with a full install from this disk image ignoring the system beeps, or is there a better way to do it?

I'm tempted to stick with Edgy for a while, maybe do a fresh install of that instead.

This is disappointing.

---

### Post by MartynM on 2007-04-20
Ker-bump!

Nobody else having this problem or suggest anything?

 I guess judging by the amount of install probs getting posted here that this must be just a really minor issue. I recon I'm going to wait for a while before going down the feisty route.

I think I'm going to re-install Edgy for now until Feisty settles down a bit but I can't seem to find a link to the ISO any more on any of the mirrors, has it been removed?

.

---

### Post by etherealremnant on 2007-04-20
I had the same issue.

The odd thing is that it doesn't happen every time I boot the Live CD. And if I give it some time, it loads X like normal and works fine. Then when I shut it down, it beeps continuously until it shuts off.

My board is an Intel D975XBX2 (Bad Axe 2)

Also of note, it hasn't done it once since I installed Feisty to the drive.

---

### Post by MartynM on 2007-04-20
Interesting. How did your install go, did you get the beeping all the way through it? Is your Feisty install now running ok?

Thanks for the info etherealremnant, I'm plucking up the courage to actually go for an install, if I know for sure that this beeping is purely a bug on the Live CD and not something not being run badly on the motherboard then i might dive in and install. It's going to be a noisy experience though.

BTW I found an edgy link, dur.

---

### Post by etherealremnant on 2007-04-20
Once X launched, the beeping stopped and it hasn't beeped once since I got it installed.

Now that I figured out how to get my 8800GTS to work with acceleration, I'm totally happy with Feisty. Definitely a nice upgrade from Edgy. :)

---

### Post by MartynM on 2007-04-20
Thanx again ,:-k  I think I'm going to go for it in the morning though as my girlfriend's asleep in the room next door. I'll post back with the result just in case anyone else has the same issue.

Cheers.

m

---

### Post by MartynM on 2007-04-22
Right, i finally went for an install ignoring the continuous beeping coming from my computer's internal speaker, got to the reboot and it silently went to desktop. Perfect!

Or so i thought. After having a good look round and setting up a few things, I opened the terminal to fire off GLX gears to check how my graphics card was doing and ..beep....beep....beep.

I cannot run a terminal at all in this system, every second or so  the syslogl is logging the following every time the computer makes a beep (just the last 3 beeps here);

"Apr 22 13:54:53 username-desktop kernel: [ 6268.341028] EDAC MC0: UE page 0x37b9a, offset 0x0, grain 4096, row 1, labels ":": i82875p UE
Apr 22 13:54:54 username-desktop kernel: [ 6269.338639] EDAC MC0: UE page 0x37b9a, offset 0x0, grain 4096, row 1, labels ":": i82875p UE
Apr 22 13:54:55 usename-desktop kernel: [ 6270.336244] EDAC MC0: UE page 0x37b9a, offset 0x0, grain 4096, row 1, labels ":": i82875p UE" (from the syslog)

If I try to run a terminal all it does is print this every second.

"Message from syslogd@username-desktop at Sun Apr 22 14:02:36 2007 ...
username-desktop kernel: [ 6730.249374] EDAC MC0: UE page 0x37b9a, offset 0x0, grain 4096, row 1, labels ":": i82875p UE"

Every other thing about this install seems to run ok, except for anything that requires realtime priority because this error (if that's what it is) is constantly ticking away behind the scenes.

Can anyone shed any light on this? This system is pretty unusable to me really but I want to get to the bottom of it rather than roll back to Edgy. I've never filed a bug report for this sort of thing before, what's the correct procedure?

I'd be grateful for a bit of help, I'm as a complete loss to figure out what this is.

Cheers

m

---

### Post by MartynM on 2007-04-22
Bump
Anybody have any ideas or advice? (polite)

---

### Post by MartynM on 2007-04-22
Does anyone know how to report a bug, or get some advice from anyone who knows something about Feisty? I can't seem to get an answer here and Launchpad seems to be a closed shop of developers.

Surely I can't be the only one with this problem.

How are you supposed to report a bug?

---

### Post by wnelson on 2007-04-22
I found this here, it may help.

[http://fcp.surfsite.org/modules/smartfaq/faq.php?faqid=2721](http://fcp.surfsite.org/modules/smartfaq/faq.php?faqid=2721)

Walt

---

### Post by MartynM on 2007-04-22
Thanks for the help Walt, I wish I understood a little more about what that was about but I did a search on my ASUS P4C800 motherboard and EDAC on google and it came up with this page

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0605.2/0078.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0605.2/0078.html) 

Here's a quote. 

"Every one of our ASUS P4C800-E and ASUS P4C800 based machines
> that I've installed a 2.6.16 smp based kernel on is logging
> messages of the form:
>
> EDAC MC0: UE page 0x1fffa, offset 0x0, grain 4096, row 0,
> labels ":": i82875p UE
>
> every second or so. So I've downgraded them back to 2.6.15. I
> believe the message is moaning that the ECC memory has
> unrecoverable errors. However, the memory in the machines
> I've tried passes memtest. And I'd've expected system hangs
> which we don't get.

Well, memtest passes if I don't enable ECC in memtest. However, if I do,
it fails. So it looks like we've got a memory/memory controller issue
(the fact that it's happening on all machines with these motherboards
implies to me that's a controller/bios issue rather than a memory
issue). If I update the AGP aperture in the BIOS to 256Mb (from 64Mb),
memtest with ECC enabled passes but linux then boots up extremely
slowly. So is this also going to be motherboard/bios issue?

-- 
Andy, BlueArc Engineering"

That appears to be the root of the problem, I'm buggered if I really understand it but it appears to be a bug in the kernel relating to my mobo.

I really want to know how I go about reporting this properly to the right people otherwise it's not going to be fixed in a while.

Thanks again for your help, that was very useful.

m

---

### Post by MartynM on 2007-04-22
As an update to this, I disabled error correction in my bios and the problem went away, not sure if it's ok to run like this but it all seems ok for the moment.

 I think I'll upgrade my bios to see if it fixes the problem, I've never done it before but I think it's probably sensible to make sure I'm on the latest bios version before filing a proper bug report. It's interesting that Edgy didn't have a problem and Windows is still running perfectly though, it has something to do with the latest kernel.

Many thanks to wnelson for that link, that really helped.

Cheers.

m

---

### Post by wpshooter on 2007-08-24
> **MartynM said:**
> As an update to this, I disabled error correction in my bios and the problem went away, not sure if it's ok to run like this but it all seems ok for the moment.

 I think I'll upgrade my bios to see if it fixes the problem, I've never done it before but I think it's probably sensible to make sure I'm on the latest bios version before filing a proper bug report. It's interesting that Edgy didn't have a problem and Windows is still running perfectly though, it has something to do with the latest kernel.

Many thanks to wnelson for that link, that really helped.

Cheers.

m

Looks like the last post on this thread was back in April of 2007.

It is now August 2007.

I have this same BEEPING problem with my ASUS P4C800-E Deluxe motherboard when installing the Feisty version of Ubuntu.

Does anyone know if any progress has been made in finding a solution to this problem ?

I have reported this in Malone several months ago and to date, I can not see where that report has resulted in any solution to this problem.

I have found (like the above quoted post) that if I turn ECC off in the BIOS, that the BEEPING problem goes away.  BUT surely there is a better solution than that to this problem.  I have also updated the BIOS on my motherboard to 1023 the latest non-beta version according to the ASUS website and that still has not remedied this problem.

Has anyone that has had this problem on an ASUS P4C800-E deluxe or similar motherboard, found the CORRECT ultimate CAUSE and FIX for this problem ?

I have been wondering if it is possible that the Kingston ECC memory modules that I am using are possibly defective BUT having talked to Kingston about all of this, they seem dead-set that this is not a problem with their memory modules in spite of the fact that as I have told them that when I run Memtest version 3.3 on their ECC modules for this motherboard and turned on the ECC checking feature of Memtest, that I get just a whole slue of "uncorrected errors" under that column labeled "GOOD" in the Memtest program.

Anyone out there having these BEEPING problems when using Feisty, please report your experiences and findings here, so we can see if we can possibly get to the root of this problem.

I.E., is this a Ubuntu kernel problem, a motherboard/BIOS problem or a defective memory module problem, I would think, it would have to be one of these three.

Thanks.

---

### Post by wpshooter on 2007-08-26
bump.

---

### Post by wpshooter on 2007-08-27
bump.

---

### Post by wpshooter on 2007-08-28
bump.

---

### Post by wpshooter on 2007-08-29
bump.

---

### Post by jestrange on 2007-11-28
I believe I'm experiencing a similar issue on my EVGA nForce 680i SLI motherboard and the Gutsy Ubuntu live CD.

Basically my goal is to dual boot Windows XP and Ubuntu on separate hard drives.  My system currently has one hard drive with a full Windows partition on it.  I bought an additional hard drive for this purpose.  Before installing the new hard drive, I booted into Ubuntu using the live CD.  I had no problems that I was aware of.  Ubuntu loaded fine and everything ran.

I determined that everything was cool and installed my new hard drive.  I disconnected the Windows XP drive and was going to install Ubuntu on the new drive.  My computer passed POST and I started to boot into Ubuntu.  However, this time my motherboard started beeping alot.  My motherboard has an indicator on the motherboard which displays an error code.  According to my motherboard manual, this error is a CheckSum - "Check Integrity of ROM, BIOS and message" error.  I was still able to boot into Ubuntu.  Nervous about the error, I decided to shut down.  Again the motherboard started beeping.

I've booted into Ubuntu a few other times, with the beeping occurring sometimes.  My last boot into Ubuntu, there was not beeping but the error code was still displayed.

I'm still able to boot into Windows XP normally without the beeping.

Should I still install Ubuntu ignoring this since I'm still able to boot into Ubuntu?  Could this damage my motherboard?

---

