---
title: "Weird USB hard drive behaviour"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2009-10-08
I have an Iomega Prestige 500GB USB hard drive. In Karmic when I suspend the computer with the hard drive attached it throws the drive into a "frozen" state where the drive is no longer accessible or responsive which means that it never automatically powers off when it detects the computer has been suspended or shutdown. In addition to that it's not accessible or even visible to the system after resuming from suspend and it doesn't function properly until I turn the drive off and back on. In Jaunty and previous releases this drive has worked perfectly. I've already filed a bug report [here.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440059") Does anyone else have this problem or have an ideas on workarounds?

---

### Post by FuturePilot on 2009-10-09
This is frustrating. :-x

Bump

---

### Post by FuturePilot on 2009-10-11
Anyone? :(

---

### Post by Leighman on 2009-10-11
I'va also noticed mine not spinning down when I shutdown the computer

---

### Post by FuturePilot on 2009-10-15
Anyone have any ideas? I'm still having this problem and it's kind of a show stopper for me :(

---

### Post by novafluxx on 2009-10-15
Has anyone updated your bug report?

---

### Post by FuturePilot on 2009-10-15
> **novafluxx said:**
> Has anyone updated your bug report?

No. 

I've recently been trying to mess around with udev but I still can't pinpoint it. And the fact is there doesn't seem to be much to go off of in the logs. One tough bug. :(

---

### Post by FuturePilot on 2009-10-27
For whatever reason, this hard drive hates USB resets because when it receives one, it just freezes up. It so happens that it gets a USB reset during the suspend process which is causing the drive to be gone from the system on resume. Anyone have any ideas about what would be causing a USB reset on suspend?

---

