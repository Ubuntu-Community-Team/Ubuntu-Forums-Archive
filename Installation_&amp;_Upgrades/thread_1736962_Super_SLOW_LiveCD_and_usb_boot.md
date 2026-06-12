---
title: "Super SLOW LiveCD and usb boot"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by cwwilson721 on 2011-04-22
I'm not a Linux noob, by any stretch, but this is driving me INSANE.

I have an Acer Aspire 4320 laptop, and I'm trying to install 10.10 on it.

The LiveCD, and the LiveUSB, take over 3+ HOURS to boot to a desktop. Then, it can't format the drive.

Am I missing boot options (i.e. 'noapic') or something?

Do I set the drive in bios to ide or AHCI? (If set to ide, it takes ALOT longer..approx 45 min to get to the "run" or "install" screen)

Any ideas would be VERY much appreciated

EDIT: I did manage ONCE to get to 'check this drive for errors', no killers found. (At the 'keyboard screen, I pressed 'space'). Do I need to add any other options here?

PS: The only 'guides' I have found only go to Gutsy, so...

---

### Post by mörgæs on 2011-04-23
Have you tried the alternate ISO?

[www.releases.ubuntu.com](www.releases.ubuntu.com)

---

### Post by varunendra on 2011-04-23
How much RAM do you have?

Is your current OS (Vista?) on it working flawlessly?
AHCI should be okay, but sometimes a failing HDD may cause such problems. So I'd suggest to detach it and see if the boot-up speed improves.

---

### Post by cwwilson721 on 2011-04-23
> **varunendra said:**
> How much RAM do you have?

Is your current OS (Vista?) on it working flawlessly?
AHCI should be okay, but sometimes a failing HDD may cause such problems. So I'd suggest to detach it and see if the boot-up speed improves.I didn't think of that...

That would let it try to boot w/out the added complexities. It would also tell me if the HDD was in Windows (IT'S FAILED!) mode...lol

---

### Post by cwwilson721 on 2011-04-23
Okay...Here's my answers:

Yes, I did try alt. CD. FAIL the same way.

I'm not an idiot about memory. 2GB is plenty, and memtest+ worked for 24 hrs.

Pulling the hdd: YEAH! Booted almost as fast as my desktop w/4GB and the 5200+ AMD dual-core.

Time to buy a new hdd. The thing that threw me was it passing the disk test. I guess the logic board went the way of Windows 2.0..

Thanks!!

---

### Post by varunendra on 2011-04-23
> **cwwilson721 said:**
> It would also tell me if the HDD was in Windows (IT'S FAILED!) mode...lol
:D :D

> **cwwilson721 said:**
> Pulling the hdd: YEAH! Booted almost as fast as my desktop w/4GB and the 5200+ AMD dual-core.

Time to buy a new hdd. The thing that threw me was it passing the disk test. I guess the logic board went the way of Windows 2.0..

Thanks!!

:) Thanks for the good news early in the morning :).

By the way, low level formatting (using seagate disk manager) once did the magic for me, gave that disk another 7-8 months before ubuntu started to struggle again (it was a 3.5" drive, had Win XP earlier, and zero-filling drive failed, but low-level formatting somehow passed).

---

### Post by cwwilson721 on 2011-04-24
That's not possible :(

After my last post, I connected up the drive to an open SATA port on my desktop (Yea for UNIVERSAL standards!), and...Well, it's as toasted as a OC'd I7 running at 14GHZ on air...Yep, fried to a crisp.

Thanks, all, for the replies. I'm kicking myself for not doing that, because I should know better (Been messing with these bloody things since 1973)

Again, thanks.

---

