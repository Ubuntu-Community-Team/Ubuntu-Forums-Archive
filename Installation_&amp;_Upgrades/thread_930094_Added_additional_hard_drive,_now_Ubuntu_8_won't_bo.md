---
title: "Added additional hard drive, now Ubuntu 8 won't boot - getting ata frozen status"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by ejvan on 2008-09-25
I just added an additional hard drive to my system.  To be more exact, I had a PIDE drive I'd been using in an external enclosure for data store.  I purchased a PIDE -> SATA converter, put that in and attached it to my SIIG SiL 3114 RAID card (in adapter, not RAID, mode) on the 3rd socket.  The drive is NTFS partitioned, and under XP it was recognized with no issue.  However, it has caused my ubuntu partition to not boot.  I've tried going in with the live CD, but it also fails.

Upon boot, I now get a busybox message, and then it keeps scrolling the following (tried to capture it all; no screen shots, had to write by hand):

ata08.00  status {DRDY}
ata08.00  soft reset link
ata08.00 configured for PIO3
ata08.00 configured for PIO0
ata08.00 EH Complete
ata08.01:  exception EMASK 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

It keeps repeating the above over and over.  

My current guess is that I noticed with the new drive XP re-ordered some drive letters.  I understand they are not related, but I'm guessing that somehow the mappings got screwed up (xp just compensated).  I did have some entries in my fstab, but I can't get to them to delete them to see if that was the issue.

I still have to try disconnecting the new drive to see if ubuntu just doesn't like that drive or adapter, but I have a feeling it's related to mount and my fstab.  I've tried booting to a liveCD and gotten the same results (no boot :(  )  Any help would be appreciated.

---

### Post by ejvan on 2008-09-25
Just an update.  I pulled the new drive and same results, so it's not the new drive adapter.  One bit I forgot about.  I had to update the SIIG SiL 3114 RAID card's bios as it was ancient.  Could this be horking things up?

And the busybox text is that it is loading the busybox shell (ash).

---

### Post by ejvan on 2008-09-29
Bump; anyone have any thoughts?

---

### Post by Dreaming on 2008-09-29
I am using the Sil3512 adapter (same family as 3112) and can't even get ubuntu 8.04 to load before the installation screen. It just does this:

[[IMG]http://img204.imageshack.us/img204/4278/imag0003iz6.th.jpg[/IMG]](http://img204.imageshack.us/my.php?image=imag0003iz6.jpg)[[IMG]http://img204.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Any help would be great. This is after it's booted from the CD, I get a choice of language, choose English, then I choose use ubuntu without installing hoping to set up my hard disk and then install from inside ubuntu.

---

### Post by ejvan on 2008-10-02
Dreaming - 
Check out:

[http://backports.ubuntuforums.com/showthread.php?t=765195]("http://backports.ubuntuforums.com/showthread.php?t=765195")

I did a search for the initramfs error I was getting and found the above thread.  After about 6 pages, I figured I'd first try my BIOS settings.  When I had added a new drive I also removed my floppy drive & disabled it in the BIOS.  I went into the BIOS and simply re-enabled the floppy support even though there is no drive attached.  8.04 booted fine after that.  

Stupid solution, but it works.  

Hope that thread helps you also.

---

