---
title: "Cannot boot after upgrade"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Steve1961 on 2010-03-23
I ran an upgrade on mt karmic system last night, and on rebooting I get the following error message:

Mount: Mount Point 0 does not exist
Mount 0 terminated with status 32
Mountall: Filesystem could not be mounted

The system then just hangs.  I've checked that fstab has the correct UUIDs and can't see anything obvious.  For information I dual boot and have windows on the first partition and ubuntu on a logical partition.  I don't have the infamour proc line associated with virtualbox in my fstab so don't think that's the issue.  Anyway have any ideas?

---

### Post by dino99 on 2010-03-23
so you can't boot from Karmic, even in recovery mode ?
why are you talking about virtualbox ?
can you have some info from logs (viewing them via Windows or with your network)

---

### Post by Steve1961 on 2010-03-23
Sorry, I wasn't clear.  I ran a dist-upgrade from karmic to Lucid Beta1.  The virtualbox error I mentioned seems to happen if you have the modified proc line in fstab to enable usb support, but that isn't an issue in my case.  As for getting the logs, well yeah, I could probably access them using a live cd if it comes to that, but hardly from windows - no ext4 driver for windows yet to my knowledge.

---

### Post by dino99 on 2010-03-23
> **Steve1961 said:**
> Sorry, I wasn't clear.  I ran a dist-upgrade from karmic to Lucid Beta1.  The virtualbox error I mentioned seems to happen if you have the modified proc line in fstab to enable usb support, but that isn't an issue in my case.  As for getting the logs, well yeah, I could probably access them using a live cd if it comes to that, but hardly from windows - no ext4 driver for windows yet to my knowledge.

So i see 2 ways to go ahead:
- try to repair but how ?
- format then make a clean install with a daily snapshot on usb (no need to burn)

Of course i hope you have a separate /home or backup.

---

### Post by Steve1961 on 2010-03-23
Well yes, try and repair.  If I have to do a clean install so be it, but thats just not something I intend to consider until Ive at least tried to fix this

---

