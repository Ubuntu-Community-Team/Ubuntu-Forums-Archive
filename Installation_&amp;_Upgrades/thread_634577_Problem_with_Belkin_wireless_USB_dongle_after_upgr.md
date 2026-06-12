---
title: "Problem with Belkin wireless USB dongle after upgrade to Gutsy"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by QuantumCaffeine on 2007-12-07
Hi all,

(Apologies if this question has already been done to death elsewhere, but I can't find an answer that works.)

I have an old Belkin wireless USB dongle (lsusb lists it as ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi) that used to work just fine under Feisty. Unfortunately, I've just upgraded to Gutsy and it's now nowhere to be found: it's not listed under "Network Settings". (In the Restricted Drivers Manager I can see "Lucent/Agere linmodem controller driver" but it's marked "Not in use". I'm not even sure if that has anything to do with the Belkin dongle.)

Some digging around has pointed me to the Serialmonkey rt2570 driver. Installing this and using "sudo modprobe rt2570" has added a wireless device back into "Network Settings", but I still can't get it to work.

What am I doing wrong?

Cheers,

QC

---

### Post by QuantumCaffeine on 2007-12-07
Sorry to reply to my own post, but I've just discovered the problem. Before installing the rt2570 Serialmonkey driver, I mistakenly installed the rt73 driver, and that's the one that's currently being invoked at startup. By doing "sudo modprobe -r rt73" then "sudo modprobe rt2570", I can get the wireless going, which is good.

That just leaves one question: how do I get rid of the rt73 driver, so that the rt2570 one is invoked at startup instead? (I was hoping "sudo make uninstall" would do it, but no such luck.)

Cheers,

QC

---

