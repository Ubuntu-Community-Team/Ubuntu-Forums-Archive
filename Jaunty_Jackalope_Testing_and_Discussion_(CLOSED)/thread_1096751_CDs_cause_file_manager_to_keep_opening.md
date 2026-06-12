---
title: "CDs cause file manager to keep opening"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TaintedBllack on 2009-03-15
Whenever I try to put a cd in it causes nautilus to close and then a bunch of file managers keep popping up in the window list until I remove the cd. Are there any fixes available for this?

---

### Post by jfernyhough on 2009-03-15
Erk. Sounds like something dodgy is happening with HAL polling your drive. There are two possible workarounds - one, disable HAL from polling the drive (can't remember the command), two, turn off the autorun behaviour:

Open Nautilus,
Edit, Preferences, Media

I've checked the box for "Never prompt or start ..." and unchecked the box for "Browse media when inserted". The second one is key here, I just hate it trying to run Windows software when I insert a CD.

---

### Post by taavikko on 2009-03-15
> **jfernyhough said:**
> Erk. Sounds like something dodgy is happening with HAL polling your drive. There are two possible workarounds - one, disable HAL from polling the drive (can't remember the command)

hal-disable-polling

---

### Post by TaintedBllack on 2009-03-16
> **jfernyhough said:**
> Erk. Sounds like something dodgy is happening with HAL polling your drive. There are two possible workarounds - one, disable HAL from polling the drive (can't remember the command), two, turn off the autorun behaviour:

Open Nautilus,
Edit, Preferences, Media

I've checked the box for "Never prompt or start ..." and unchecked the box for "Browse media when inserted". The second one is key here, I just hate it trying to run Windows software when I insert a CD.

I tried out those settings and it still gives me the same issue and I don't understand how to use the hal-disable-polling command. Please help me out with this I just need to be able to burn some CDs.

---

### Post by taavikko on 2009-03-16
If command is unknown to you, check out it's man page
```
man hal-disable-polling
```

Try burning with commandline
Utilities such as cdrdao, wodim should assist you.

Sorry to be an A**hole, but you're aware that this is an alpha stage OS,
So problems will be here...
Without basic knowledge of how things work, not worth in using...

---

### Post by dyn on 2009-03-19
I'm experiencing the same problem. I'm using 9.04 alpha 6 64 bit & 32 bit in VMWare Fusion 2.0.2 and ran into this problem when trying to run the live cd and when trying to install the VMWare Tools (it mounts the iso in the vm). Disabled the automatic mounting of media devices in Nautilus and used the hal-disable-polling on /dev/cdrom. Tried to install the VMWare Tools again by selecting "Install VMWare Tools" from the VMWare Fusion menu. Normally it will automount the cd but after running the above one would need to mount it oneself, so I did. This resulted once more in Nautilus trying to start itself over and over again. So I think that the problem is more related to the part when the cdrom gets mounted. Does anyone else have the exact same issue?

---

### Post by TaintedBllack on 2009-03-25
Sorry to bring this back up but this problem is driving me crazy.. Its the only problem I have with Jaunty everything else works perfectly. Please help me to sort out this issue.

---

### Post by dyn on 2009-03-30
Issue seems related to bug [325973](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325973).

---

