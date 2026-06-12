---
title: "upgraded 11.04 -&gt; 11.10 get error message when booting"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by krackersk on 2011-10-26
Hi All,

I upgraded from 11.04 to 11.10 on my ASUS Eee PC and now when ubuntu is loading I get the message

serious errors were found while checking the disk drive for /home

and it asks me if I want to ignore, skip mounting or manual fix

If I ignore it seems to load up fine, haven't had any problems with it yet.

If I 'manual fix' it drops me to the command prompt.

Can somebody shoot me some ideas on how I go about diagnosing this problem?

---

### Post by krackersk on 2011-11-01
So I booted in recovery mode and this is the message that is shown:

fsck: fsck.btrfs: not found
fsck: Error 2 while executing fsck.btrfs for /dev/sda3
mountall: fsck /home [449] terminated with status 8
mountall: Unrecoverable fsck error: /home
/dev/sda8: clean, 277601/858480 files, 1468624/3428608 blocks (check in 5 mounts)
/dev/sda1: clean, 255/490560 files, 166268/979933 blocks
Serious errors were found while checking the disk drive for /home
Press I to ignore, S to skip mounting, or M for manual recovery

Any ideas?

---

### Post by dino99 on 2011-11-01
btrfs is still like an adventure, very buggy itself and system not fully ported to.

---

### Post by krackersk on 2011-11-01
Yes, I know that btrfs is new but I have also installed 11.04 on a different partition with it references the same home drive partition as 11.10 and I do not get this error message. This would suggest it has something to do with the upgrades and not the file system

---

### Post by kesten on 2011-11-23
Krackersk,
I had the same problem upon migrating 11.04 to 11.10.  I'm on an asus laptop 1.5 yrs old.

Message: serious errors encountered while checking disk ... both for my /DATA and /OS (originally my C and D drives back in my windows 7 days.)

Following advice on another forum, I ran SmartData command from DiskUtility
On C drive
I had a warning for Realocated Sectors (bad sectors) being 60.
And a failing Airflow Temperature of 57C

On D drive
I had a warning for Realocated Sectors being 60
And a failing airflow temperature of 57C

I'd be curious to see what other users with this error are getting.  Both are serious errors, but the fact that it only occurred after switching to oncelot, and even more suspiciously, that both C and D drives report exactly 60 bad sectors (what are the odds!?) makes me wonder.

The same forum recommended double checking with another utility - they recommended GSmartControl, but it didn't work on my hardware.

All the same, i'm starting some serious backing up of everything...

kesten

---

### Post by davidp03 on 2011-12-17
I've got the same problem here. GEtting an error while booting which reads:

"Serious errors were found while checking the disk drive for [/media/storage].
"Press I to ignore, S to skip mounting, or M for manual recovery."

I also started getting this error after upgrading to 11.10 from 11.04.

dp

---

### Post by lpc921 on 2012-01-07
I had the same problem. I changed the last number (pass) to 0 in fstab and the error message is gone. Don't know if that will affect other things.

---

