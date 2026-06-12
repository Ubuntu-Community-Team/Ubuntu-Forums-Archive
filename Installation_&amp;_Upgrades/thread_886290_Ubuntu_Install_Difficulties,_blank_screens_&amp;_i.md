---
title: "Ubuntu Install Difficulties, blank screens &amp; install freezes."
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by heroimprisoned on 2008-08-11
Hello, ubuntuforums.  I've been trying to put ubuntu on my desktop for a while now, and haven't had much luck.  I was recently directed to using Wubi for the installer, and I managed to get Grub installed.  I chose to start ubuntu, and my screen went black as soon as I told it to install, with a blinking cursor in the upper right corner of the screen.

I restarted, and this time chose to install in verbose mode.  I managed to see a few more things happen, and witness a few random pauses in the install process that I might have considered freezes before I had a text prompt telling me what was going on, but I digress.

The installer said something about my discs and doing something with various file systems, which seemed pretty normal, and I walked away from it for a second to drop something in the mail.

When I came back, the screen was black.  My monitor was still reading a signal, but nothing was displayed.  I didn't even get a chance to copy down whatever the screen had said before, and it's still here, about 15 minutes later, on the black screen.

EDIT:  Here are the last few lines from verbose mode that I managed to copy down:



I am running a 64 bit AMD 3200 on a Chaintech VNF4Ultra board, with a WD Raptor for the system drive.  I have two gigs of ram, no onboard video, and no ******* idea what could be going on.

Help?

EDIT #1:
Here are some of the last few lines from verbose mode that I managed to copy down:

```

[275.972820] loop: module loaded
[278.218841] ISO 9660 Extensions: Microsoft Joliet Level 3
[278.685600] ISO 9660 Extensions: RRIP_1991A
[279.587601] Registering unionfs 1.4
[279.590055] unionfs: debugging is not enabled
[281.599738] squashfs: version 3.3 (2007/10/31) Phillip Lougher

```

and then it just ... stops.  If I come back to it, the screen is black.  I'm trying it again this time with the graphical safe mode, we'll see if that changes anything.

EDIT #2:

Well, well, looks like the black screen portion of this problem is just a screensaver.  That's pretty cool - but it still doesn't explain why the installer just hangs out here for so long.  Anyone got any ideas/suggestions for help?

---

### Post by heroimprisoned on 2008-08-11
Bumping doesn't seem to be a problem on these forums, so I'm going to do it with an update.

I left the system on overnight, and it seems to have progressed.  I am now at a graphical screen with the Heron background and a progress bar labeled "Checking The Installation".  The bar itself is at about 66%, and is "Copying Files..." but hasn't progressed more than a single percent in an hour.

It seems really unusual that the installation would take so long.  I ran JKDefrag on the drive I'm installing to right before I started the install, and I can't imagine why it's so slow.  Any ideas?

---

### Post by lemtargatwing on 2008-08-11
I'm not gonna claim to be a guru, I'm just gonna tell you what I think about it.  When I installed Fedora Core 5 on my PS3, I went to work from 8-cl (midnite is close, we didnt get out till 1 though).  I started the installation which was the full install at around 7.  It still was not done when I got home, and I have no idea when it finished, because I woke up late the morning after and had to rush to school.  In my experience with computers, sometimes things just take a bit longer than they should.  If it continues to remain like that for an extremely long time, then you should be worried. Again, I'm no guru.  Just my opinion.

---

### Post by heroimprisoned on 2008-08-11
Fair enough.  I'm happy for any response, guru or not.  I'd be curious to see if anyone else has similar experiences, for example.

73% now... about 7% an hour means I still have quite a ways to go.

---

### Post by heroimprisoned on 2008-08-11
My install was at about the 36 hour mark and at 95% on the progress bar, "Checking for packages to remove", when I decided to can it and figure out exactly what the hell was going wrong.

I've heard that these forums are really helpful, but haven't really gotten any use out of posting here yet.  Is there some vital piece of information that I'm not giving you guys?  It seems absolutely insane that, even using wubi, an install would take 36+ hours to complete.  What other possible reasons are there for this?

I read something in another thread about the possibility of a HD driver causing a screwup like this.  I have a WD Raptor 74 gig that I was trying to install Heron on, a Maxtor SATA drive, and a Maxtor IDE drive.  Anything ringing any bells for anyone?

---

### Post by xen-uno on 2008-08-11
36 hours? Hmmm ... I doubt you'll have a good install when it completes. Did you check to see if any BIOS updates are available from Chaintech? I think you do have a HD driver issue or have the SATA interface misconfigured in the BIOS (where you can select RAID, AHCI, or IDE). If not familiar with this BIOS setting, see ...

[http://forums.tweaktown.com/f69/sata-bios-question-26543/](http://forums.tweaktown.com/f69/sata-bios-question-26543/)

RAID is the best setting. AHCI, I believe, is a subset or is fully duplicated by RAID.

---

### Post by heroimprisoned on 2008-08-11
I'll give the RAID setting a shot and see if there's a bios update.  Last I checked, there wasn't.

---

