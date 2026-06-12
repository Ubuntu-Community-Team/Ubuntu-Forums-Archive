---
title: "Gave up waiting for root device"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by bobbryce on 2010-04-03
Can anyone please help a Newbie?
Just installed Ubuntu Server v9.10 over an existing working XP installation containing two conventional IDE drives (were drives C: and D: under windows).
I'm new to Linux and was following instructions on creating a simple file server (Tad Harrison 14th Feb 2009).

Everything appeared to go fine with the install, but after the first reboot, all turned to rats.
Message was 'Gave up waiting for root device' followed by advice on common problems.  Followed up with 'ALERT! /dev/disk/by-uuid ................  does not exist. Dropping to a shell'

I followed advice in Tad's notes for updating the system if there was a problem. I successfully went through an update and now have a new option at boot-up - but still have the same problems - the root seems to get mounted, it seems to run '/scripts/local-top' and then sits waiting for the root file system.

Of course my windows operating system is trashed so I can't use that to explore, and I'm brand new to Linux so don't know how to find my way around....

Is it possible it's getting confused on my two drives? Do I need to manually disconnect the second one?

Can anyone recommend what to do next?
Many thanks

---

### Post by bobbryce on 2010-04-03
Folks - more information.

After failing to get the Server software to work, I tried loading the Desktop software and had success first time.

This must be a bug in the Server installation - yes?
Maybe I should try an older version of the Server software....

---

### Post by bobbryce on 2010-04-04
More info....
Tried installing an older version of Server - 8.0.4 LTS. This one works more or less fine, so still thinking that v9.10 has problems.

Strange problem in installation of 8.0.4 - halfway through it failed trying to mount my CD ROM. This was clearly daft since it had been successfully reading from that. The only way forward was to remoce CD from CD drive and put it into the DVD drive and its been happy there ever since!

---

