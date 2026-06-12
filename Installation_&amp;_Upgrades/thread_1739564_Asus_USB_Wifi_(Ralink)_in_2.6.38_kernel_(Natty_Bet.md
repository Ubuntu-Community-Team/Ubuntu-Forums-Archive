---
title: "Asus USB Wifi (Ralink) in 2.6.38 kernel (Natty Beta)"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by fatalGlory on 2011-04-26
I've been tearing my hair out today.  I've been running debian testing for a while, today did a dist-upgrade and discovered my wifi no longer worked.  After trying many things, I downloaded the latest Natty Beta, hoping the excellent distro polishers in team Ubuntu might have sorted it out.

My wifi device is an Asus USB dongle with a Ralink chipset.  The problem appears to be associated with the 2.6.38 kernel upgrade.  I tried the LMDE live cd with the 2.6.32 kernel, wifi works out of the box, after dist-upgrade in LMDE (effectively the same as previous debian dist-upgrade, same problem).  Tried the Natty Beta live cd (with 2.6.38 kernel), same problem.

The natty-beta live cd works fine for my other computer with a realtek wireless chip, so that narrows down the issue in my mind.  I also tried reverting to the old 0.28 version of the ralink firmware package instead of the current 0.29 in debian testing, no better.

Interestingly, the newer kernel tries to load the rt2800usb module and fails, whereas the older kernel appears to have loaded the rt2870sta module and worked fine.  Not exactly sure what the difference between these two is, or what their origin's are.  I tried blacklisting rt2x00usb and rt2800usb in /etc/modprobe.d/blacklist.conf, the system start's with no error, but no wifi either.  Running "modprobe rt2870sta" as root returns module not found.

Not sure what's gone on, but its highly aggravating.  I've already done a couple of reinstalls over the long weekend to try and get it working and it looks like I'll have to do another one back to Debian stable to get a kernel that works with my wifi dongle.

Anybody have any advice or similar problems?

---

### Post by jimna on 2011-04-29
No advice, similar problem. My Asus usb wireless thing stopped working the moment I restarted after upgrading to 11.04. I've been reading other threads with similar issues and haven't found anything yet that will fix it. (I'm also quite the novice) So I'll subscribe to this thread and see what happens.

---

### Post by pppppp on 2011-05-03
Hi, guys. I've just updated from 2.6.32 to 2.6.38 and struggled with a similar issue. My old kernel would load rta2800usb, rta2x00usb and rta2x00lib and fail utterly to use my dongle, so I had to blacklist them all and load rta2870usb. Now it seems it simply won't even enter 2.6.38's playpen, as you have noted - same "module not found" here when I tried to load it -, but rta2800usb suddenly works, so try that (and only that - if I don't blacklist the other modules, they all get together and do some funky, unproductive voodoo).

---

### Post by fatalGlory on 2011-05-05
After reading pppppp's post, I tried installing the fresh Natty release.  No WiFi out of the box, but adding the following to /etc/modprobe.d/blacklist.conf fixed the problem

```
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2800usb
```

Note that the relevant modules are called "rt2xxxxx" not "rta2xxxxx".  With these blacklisted, the rt2870sta driver will load and run properly (I'm writing this reply from the Natty install).  I had done these same steps in Debian testing, but they didn't work, not sure why.  I think I must not not have had rt2870sta installed correctly.

Not quite out of the box, but I still count it as a win for the Ubuntu team for including rt2870sta by default so that the blacklisting fix works.

Guess I'll switch from Debian back to (x)ubuntu for a while.

---

