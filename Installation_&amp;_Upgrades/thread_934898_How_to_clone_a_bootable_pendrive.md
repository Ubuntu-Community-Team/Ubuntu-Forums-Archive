---
title: "How to clone a bootable pendrive?"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by risbac on 2008-10-01
Hello!

I'm trying to clone a USB bootable pendrive which has been configured with ubuntu. I would like to be able to very quickly and easily format a new pendrive with this system.

What I tried was simple to dd the complete pendrive to my computer, then dd it back to a new pendrive. "Boot Error" at boot. I tried to fix the MBR, same problem... I thought that with DD I would have exactly the same pen drive, so it would work the same way. But apparently I'm not that clever :)

Any help would be welcome!

---

### Post by C.S.Cameron on 2008-10-01
I just got a Flash drive how I want it, and was wondering the same thing myself.
Think I recalling something about it being possible in these forums.
I just got a few new thumbdrives to play with, will let you know if I find anything that works.

---

### Post by C.S.Cameron on 2008-10-02
Got it working!
Booted computer using primary pendrive, (sdb).
(can also boot from HDD or Live CD).
Inserted pendrive to clone o/s from, (sdc).
Inserted pendrive to clone o/s to, (sdd).
In terminal ran:
sudo dd if=/dev/sdc of=/dev/sdd
After operation completed, rebooted with sdd.
So far everything looks identical to sdc.
Although identical make and model sdd has a few more megs than sdc thus a bit of unallocated space at the end.
Good luck

---

### Post by caljohnsmith on 2008-10-02
> **C.S.Cameron said:**
> Got it working!
Booted computer using primary pendrive, (sdb).
(can also boot from HDD or Live CD).
Inserted pendrive to clone o/s from, (sdc).
Inserted pendrive to clone o/s to, (sdd).
In terminal ran:
[COLOR="Red"]sudo dd if=/dev/sdc of=/dev/sdc[/COLOR]
After operation completed, rebooted with sdd.
So far everything looks identical to sdc.
Although identical make and model sdd has a few more megs than sdc thus a bit of unallocated space at the end.
Good luck
Is that maybe a typo? Did you mean:
```
sudo dd if=/dev/sdc of=/dev/[COLOR="Red"]sdd[/COLOR]
```
Always be super careful when using dd, as one slip of the fingers or wrongly specifying the the input/output can lead to disastrous results. :)

Also, just as a point of interest, dd uses a block size of 512 bytes by default (exactly one sector) when it does its copying; if you want to speed things up a bit, you can use a larger block size, but then also include the "conv=notrunc" to make sure you copy everything even if your source is not an exact multiple of the block size you specify:
```
sudo dd if=/dev/sdc of=/dev/sdd bs=10M conv=notrunc
```

---

