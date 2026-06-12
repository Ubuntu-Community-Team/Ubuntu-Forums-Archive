---
title: "Ubuntu 7.10 won't boot after vacations?"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by diegolaz on 2008-01-07
strange... a came back from a week of vacations and my Ubuntu 7.10 won't boot. It was up to date, on a AMD X2 3800 with an ATI 800, 2GB RAM.
I can get to recovery mode, and I made a apt-get update and apt-get upgrade, but when I try to boot normaly, nothing.....not even an error, and sometimes the keybord starts blinking.....
Is there a way (I'm sure there is but can't find where) to see from recovery mode the error log??

Thank you!
Diego

---

### Post by diegolaz on 2008-01-07
Sorry, maybe I frased the problem wrong. The thing is I can only boot in rescue mode but I don't know what the problem is so I don't know what to fix.... I had a graphical desktop with 3D effects working with a LAMP server..... what log should I look for?

Thanks again!

---

### Post by diegolaz on 2008-01-07
I just edited in GRUB the boot option removing ro quiet splash and it started to work ok....
Was that the reason or just coincidence... I'm not sure :D

---

