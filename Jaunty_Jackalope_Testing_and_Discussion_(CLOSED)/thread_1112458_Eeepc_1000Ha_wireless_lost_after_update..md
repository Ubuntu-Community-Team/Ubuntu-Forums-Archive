---
title: "Eeepc 1000Ha wireless lost after update."
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tegwilym on 2009-03-31
I installed Jaunty on my 1000ha netbook computer, set in the WEP code for the wireless for our office, and wreless was working fine with no problems. 
Updated the OS: 
 
 ```
sudo apt-get update 
 sudo apt-get upgrade
```

Reboot, now the wireless doesn't show up at all, and I can't figure out how to turn it back on. I don't get the signal screen or anything now.  Gone.
Wired works,just plug it in.  USB wireless works fine so I'm assuming the driver got messed up somehow.
I had it set on the MadWifi that is build in, and it all worked first time ("out of the box") as they say...
Anyone come across this problem and find a fix for it?  

Tom

---

### Post by jmichael on 2009-04-14
I am having this same problem. When I installed 9.0 on my 1000ha I had to "modprobe ath5k" to get it to works, now after this update wireless is gone and that no longer works to start it. Any info would be greatly appreciated.

---

### Post by tegwilym on 2009-04-14
> **jmichael said:**
> I am having this same problem. When I installed 9.0 on my 1000ha I had to "modprobe ath5k" to get it to works, now after this update wireless is gone and that no longer works to start it. Any info would be greatly appreciated.

Not sure what happened, but I re-installed 9.04, did the updates and the wireless was ok again with no special tweaks.   Maybe the update has a fix for that now?
I just need to figure out how to get the volume levels up again, it's just kind of quiet.  Had the same problem with 8.10, but did something and got it louder.  What did I do?  Of course I forget since it happened mostly by accident!

Tom

---

