---
title: "upgrade to 13.10 froze, now won't boot"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by rane2 on 2013-10-23
I think I'm screwed.  I tried to upgrade to 13.10 and about half way through it froze and I had to reboot. Now it won't load. I get to grub and select Ubuntu and then I just get a black screen with a blinking cursor. After about 20 seconds it says login and then that goes off and I am back to a black screen. 

I tried going into recovery mode, but after I select an option I get this

Fsck from util-linux 2.20.1
/dev/sda5: Superblock last mount time is in the future. 
(By les than a day, probably due to the hardware click being incorrectly set) FIXED

Then a simple message about write time and:

/dev/sda5: clean, 787065/38682624 files,  46360061/154712064 blocks

Under that a flashing cursor and nothing else happens. 

I can go into root, but I don't know what I can do there to fix it.

---

### Post by rane2 on 2013-10-23
I'm trying to run the upgrade from the command line,  but I keep getting the message:

W: not using locking for rear only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

When I do that it says:

Dpkg: error: unable to access dpkg status area: Read-only file system

---

### Post by marianoa on 2013-10-23
Do you have a live CD or USB pendrive? You could boot using it, try to mount the hard drive and explore it a bit, to see if your home folder is accessible and maybe backup it somewhere. Then you could proceed to a clean install and restore your home. Dunno if you can do anything without reinstalling from scratch

---

### Post by rane2 on 2013-10-23
Okay, I've made some progress. I did:sudo mount / -o remount,rwand then ran sudo dpkg --configure -a againIt did a whole bunch of stuff that took about 20 minutes. I restarted and now it boots, but it is really slow.

---

