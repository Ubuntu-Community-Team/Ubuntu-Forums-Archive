---
title: "Ubuntu Server boot-loops after upgrade to 14.04.1"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by jethro1138 on 2014-07-24
Hi all,

This is actually the second Ubuntu Server where I've had that happen... last time I just reinstalled the whole thing from scratch but I'd rather avoid that on this machine.

Upgrade goes fine, no errors, no problems at all. After reboot, though, it... well, tried to boot, gets as far as Initializing Swap, and then reboots. Then it just black-screens after GRUB and keeps rebooting. Have to actually power-cycle to get anything else.

HOWEVER. If I catch grub in time and have it go to Recovery Mode, get to the recovery menu and do ABSOLUTELY NOTHING other than say "Continue" - the server boots with no problem, and everything works fine!

No idea what the deal is and the server never gets far enough for me to look at logs. 

Anyone have any ideas?

---

