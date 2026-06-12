---
title: "Minimal install, network access"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by dave2001 on 2014-06-17
Sooooo.... I tried version 14.04 clean install using minimal cd and pulling other needed packages and desired desktop several months ago.. so many bugs I went back to 13.10 (Have been using this method of installation since 12.04 due to increasing amount of included software, packages, and configuration I disapprove of or don't use). I go to try again now that a period of time has passed that the usual initial release bugs are worked out.

The minimal installation used to detect and auto-configure network on every system I tried it on.. now it seems Ubuntu has backtracked to pre-12.04 days. The installer didn't even ask for an SSID or password before attempting to configure the network?! Why, why, why does it seem that for every step ubuntu takes forward, it seems to take two steps backward.

I've never learned how to manually configure the network DURING installation. I can muddle through it somewhat after there is a working base system installed.. 
but how to go about it with a normal DHCP isp-supplied modem?

---

### Post by mörgæs on 2014-06-17
The minimal install is indeed... minimal. One can expect only the basic system to work.

You have been lucky if you managed to install using a wirefree connection earlier. Best approach is to install and apply all necessary packages using a wired connection; wirefree settings should be the final step.

---

### Post by dave2001 on 2014-06-20
Yea... the same thought occurred to me, I just think it's silly that a release should move backwards in capability. Having said that however, I just came to this board after attempting just that: Minimal install using (md5-verified) 14.04 mini.iso on my (very capable hardware-wise) desktop using a known-good hardline, high-speed internet connection.

Installation hung indefinitely at 6% of "Installing the base system" while  "Retrieving net-tools"

Really, really, really not impressed so far with the newest LTS.

Ah-hah! Well, apparently it didn't hang indefinitely... only for a long time, about 30 minutes. I happened to leave the installer up while I came to vent on the boards using my laptop, and as I previewed my post, low and behold the installation continued, and went from 6% to the "Choose kernel" screen in about 45 seconds. The adventure continues.....

---

