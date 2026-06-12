---
title: "Acer Aspire One - Ubuntu 10.4 doesn't boot, but shows blinking cursor"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Reliant39 on 2010-05-25
Greetings, 

Similar problems to mine have popped up elsewhere, but none of the fixes seem to work (or I'm just too stupid). I tried to see what the people at Canonical and elsewhere came up with for Ubuntu 10.4 and, after the live USB checked out fine, I rather foolishly installed the OS on my Acer Aspire One D250 (1GB RAM), to run alongside Windows XP. 

It booted up once, I think, and then no more. I believe the problem MIGHT be the Broadcom WiFi stuff, but I'm not sure. Anyway, booting Ubuntu leads to a blank screen with a blinking cursor... which doesn't appear to go away. 

Recovery mode worked once or twice (had to use ACPI=OFF at least once), then no more. It leads to the same thing: that perpetually blinking cursor. 

What I would like is either a fix to get Ubuntu 10.4 launched, or some way to remove the OS and restore my netbook back to what it was. Unfortunately, the MBR fixes that are posted all over cyberspace are useless, as my hidden partition doesn't contain the rtmbr.bin file it needs to work (don't ask me why--I've already posted that question at the AAO user forum). So it seems a fix to launch Ubuntu is the only solution, so that I can at least set grub to launch Windows XP rather than Ubuntu. 

Thanks in advance for your time and help.

---

### Post by dino99 on 2010-05-25
[http://ubuntuforums.org/showthread.php?t=1477490](http://ubuntuforums.org/showthread.php?t=1477490)

---

### Post by Reliant39 on 2010-05-25
Apologies for asking something that was already answered, and thanks for the swift reply!

The solution posted in that thread worked like a charm! Ubuntu launched as it should and I was able to change grub. Will be installing the proper drivers next.

Thanks again!

---

