---
title: "Lucid installer has graphical error and doesn't work in my HP dv6000"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by hamotahari on 2010-11-30
Hi,
I have an HP pavilion dv6000 laptop. It has AMD Turion 64x2 with 4 GB of RAM and nvidia chip-set. It had a kubuntu 9.x and worked fine. Recently i decided to upgrade to Lucid amd64. But unfortunately the installer doesn't work correctly and has a graphical error. I tried server installer and its textual installer did OK but after it finished, again the login screen went problematic. I also tried 10.10 but there is no success. The problem bans me to complete the installation.
I attached a screen shot of the problem.
Any help is appreciated.

Regards,
HM

---

### Post by hamotahari on 2010-12-04
Hi again.
One of my friends suggested a magic(!) way and it has worked. It's been done through these steps:

[LIST=1]
[*]Install Lucid server edition by its textual installer.
[*]Redirect output of the laptop to another regular LCD monitor (because the laptop's monitor is unreadable now).
[*]sudo apt-get install ubuntu-desktop
[*]Install the proper nvidia driver (Systems->Administration->Hardware Drivers)
[/LIST]
That's it!

---

