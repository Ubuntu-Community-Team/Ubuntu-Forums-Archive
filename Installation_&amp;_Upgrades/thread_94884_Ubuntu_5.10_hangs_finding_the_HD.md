---
title: "Ubuntu 5.10 hangs finding the HD"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by outstanding on 2005-11-25
Hi Team
setting up on a compaq proliant DL380 server.
I am using 3 X 18.2Gb ultra3 drives in a raid 5 config

Install going well until the reboot, starts the splash screen and loading etc

gets to the messages

Begin: Mounting root file system ...
Begin: Running /scripts/local-top...
Done.
Alert! /dev/ida/c0d0p1 does not exist. Dropping to shell!

then load BusyBox shell

have tried formating the drives as normal or LVM gives the same bailout point

Any ideas

Craig

---

### Post by poptones on 2005-11-25
I tried this as well and it did not work on a raid5. I did not check into it in more depth but I suspect it is because the kernel was not compiled with support for raid5 in this method. Others report raid0 or 1 work like this, but I know raid5 does not.

I took the easy way out and setup a 1.8gb partition on each of the drives and simply mirror the root partition manually (actually, via cron). This has the edded benefit of providing me an easy way to roll back in the event of a bad upgrade... but if you are setting up a server this probably ain't the method for you.

---

