---
title: "Accident while upgrading"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by wzwilliam on 2008-11-25
Hi there, you guys. I tried to upgrade my laptop from HH to II through system update, completed all download process, started instalation and then had to go out for a few hours. When i came back, some body stumbled upon my power cord and, as far as i could notice, the power went off while restarting after the upgrade. I tried to turn the laptop on and it after GRUB it gave a kernel panic error. Then i booted through recovery trying to fix the packages, it took a few minutes, reached normally the logon screen and after entering username and password it just gives me a black screen (with control over the mouse, though) and then the system restarts. Right now i'm logged on console failsafe mode, so i could open my browser and access the network. 

Any ideas about how can i solve this problem? Any help will be very appreciated, thanks in advance.

Thank you guys, not necessary anymore, problem solved, i runned dpkg --configure -a and i could log in again.

---

