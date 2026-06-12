---
title: "HELP!!!! Fresh Install Karmic Intel Graphics Black Screen"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by cougarmaster on 2009-12-29
Hi everone I have been using ubuntu for sometime now and was happy with the upgrade from 9.04 to 9.10. Especially the bluetooth audio which works flawlessly and also my wireless apple keyboard loved it. I didnt have any problems using ubuntu in virtualized or hardware using AMD and NVidia combo. As a desktop environment I have been pusing companies to use it as thier primary OS and also as a remote desktop solution with X2GO. The customers that are using it are people who dont need MS Windows for their daily use. Even some sites which were giving trouble using firefox are now updating their websites to cater for the firefox users. 

Anyway the problem now arises for some new slim type desktops a client purchased which uses ATOM processors and onboard intel 945 graphics. The first time I tried to install ubuntu 9.10 gave blank screen. So I installed 9.04 and installed ok. Then I upgraded to 9.10 again no problem. The problem is the client wants a fresh install of 9.10. So I searched around and used F6 edited the boot param with i915.modeset=0. The CD booted into the desktop and started installation. That went flawlessly except for a crash report but the installation went on without any intervention. After the installation the computer rebooted. The boot process wen on without a hitch showing the ubuntu white logo in the middle. Then when it was going into the login page the screen went black like before. Then I boot the CD again with the param and went into the desktop and tried to edit the boot.cfg but could not find it anyway on the HDD. Then I went into /etc/default/grub but had no idea what todo as I wasnt able to update the grub since I booted with the CD. Please help I am banging my head all over the place.

All the thanks in advance.
Eric

---

### Post by MooPi on 2009-12-29
Since it is a fresh install, maybe back out and start fresh again. This time use the alternate install disk which uses less ram to complete. I have used this method on an Atom based shoebox computer. There are additional install methods given on the CD and can enable less capable system to complete the install without error.

---

### Post by cougarmaster on 2009-12-29
> **MooPi said:**
> Since it is a fresh install, maybe back out and start fresh again. This time use the alternate install disk which uses less ram to complete. I have used this method on an Atom based shoebox computer. There are additional install methods given on the CD and can enable less capable system to complete the install without error.

Ok I will try that and thanks for the quick reply.

Dang! It worked!!! QQ all that time lost to this. Thanks MooPi!!

---

