---
title: "boot degraded raid does not accept any input"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2012-12-30
I'm running 12.10 and want to replace a faulty raid member, but cannot input the 'y' when prompted if I want to boot into a degraded raid.

I doesn't accept any keyboard input at all and eventually drops me into initram

---

### Post by ronparent on 2012-12-30
What raid level are you using. A two disk raid0 is inoperative if a drive fails! Otherwise there are ways to repair your system from a live cd.

---

### Post by lister171254 on 2012-12-30
Sorry, should have been clearer

I've got a raid 1 for / and raid 5 for /home

disks a, b, c with b a standby for the raid 1.

wanted to replace disk b and the resync the raid 5. 

That all works as I've done something similar before.

When I boot into safe mode, before it get to the prompt the check indicates that the raid1 os ok. 

My problem is that the prompt (for the degraded RAID) does not accept any input

---

### Post by darkod on 2012-12-30
Is it a wireless keyboard? Try wired one.

Alternatively, try to do the operation from live mode, not from your booted system since it can't boot.

You can add the mdadm package in live mode and assemble the array with:
sudo mdadm --assemble --scan

After that fail and remove the sdb partitions, add the new disk and let it sync. It should work although it would be much better if you can get the system to boot and do it from inside. That is why when setting up mdadm I set it to boot degraded, I think it will boot without user input if a disk fails.

---

### Post by lister171254 on 2012-12-30
Yes, its a wireless keyboard, so the question is why I can use that keyboard for the selection of which type of boot, but once I boot into failsafe, I can't.

Looks like a bug

---

### Post by ronparent on 2012-12-31
It may be a script with a faulty error trap that is locking your computer up? On the other hand, if you can clear away the problem booted to a live cd everything could be fully functional thereon.

---

### Post by lister171254 on 2012-12-31
Negative. I've had this before on another one of my servers, so I think it's a bug

---

### Post by ronparent on 2012-12-31
Do a search on launchpad to see if anyone else has reported a similar problem.

---

