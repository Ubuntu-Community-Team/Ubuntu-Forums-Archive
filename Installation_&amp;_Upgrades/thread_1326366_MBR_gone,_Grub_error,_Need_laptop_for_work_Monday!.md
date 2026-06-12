---
title: "MBR gone, Grub error, Need laptop for work Monday!"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by nads1978 on 2009-11-14
Hi, I'm in some serious trouble! or will be with my IT dept if can't get help!

I installed 9.10 on a USB stick, but unfortunately it overwrote my HDD MBR with Grub. (The USB install doesn't work either.)

My HDD had "Boot Magic" with Win98 & XP (both needed for work)

I realise that "Boot Magic" may now not be there.

I would be happy to get the standard XP MBR back, even if it means I loose the win98 partition. (can run DOS on USB)

**Problem is, I have no access to the XP recovery dis**k, as I am out the country. I also have no floppy drive. 
[B]
Resources I have[/B]; several USB keys, and blank CD/DVDs. I also have Simply Mephis, Puppy & Tiny core - all live CDs. Internet access also (via live Ubuntu) I could get use of a colleagues laptop to burn any CDs that may help.

I am running Thinkpad T61

Please, someone save my butt!


ps.
When booting, the Grub error is:

GRUB loading
error: no such disk
grub rescue>_

---

### Post by darkod on 2009-11-14
Search online for something like "xp recovery rescue disc". Burn it on CD and use it, where you download it maybe it will even have short instructions. If not, once you can boot into recovery console come back if you don't know the commands.

---

### Post by gdonwallace on 2009-11-14
You might try this if you have access to the Internet from somewhere else.

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

It is supposed to repair damaged MBR from a linux install.  

I have not used it so I am not sure exactly what it will do.

Again, if you have access to the Internet, you might do a quick search on MS website to see if they have any utilities that will allow you to fix an MBR for you system.

---

### Post by nads1978 on 2009-11-15
I had no joy with that, but if anyone is interested this is what I did:

Got external 3.5" floppy.
Made XP boot disk from a colleague.
Fdisk would not work with that version of dos :rolleyes:
Accessed hidden partition that had Win98 on.
Ran program called xtgold.com,
This was some sort of file explorer,
Went to Boot Magic file, and found a file called RestrMBR, ran it from there (pushed 'x' I think to execute it.

Restart computer, straight into XP flash screen.
XP scandisk (or similar) utility took 30 mins sorting out files, than rebooted straight into XP.

I have lost the ability to run Win98 partition, but I only need it occasionally so will put it on a USB key!

Think I will get another laptop for playing with, leave the work one for work!

:D

---

### Post by darkod on 2009-11-15
Glad you got it working one way or the other. :)
Above the first post, use Thread Tools to mark it as solved.

---

### Post by nads1978 on 2009-11-15
> **darkod said:**
> Glad you got it working one way or the other. :)
Above the first post, use Thread Tools to mark it as solved.

Done.
Thanks for the help. :D

---

