---
title: "Intrepid Installation Interrupted - Help"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Umenzi on 2008-11-16
Yesterday I decided to upgrade to Intrepid. I used the update manager, figuring it would be the easiest way. When it came time to decide whether to replace my old menu.lst file (since I've modified it to include WinXP on my other partition, which I'm currently using). I clicked 'launch another shell' and the dialog box crashed. Then the installation wouldn't resume, so I quit and reopened the update manager, which didn't give me the option to try the upgrade again. I don't want half of Ibex. I restarted my box just to see if that would help, and up popped a friendly message saying that I would have to run in low graphics mode.(I knew the message would come, having an Nvidia GeForce4 MX). I could have clicked through it, but ubuntu wasn't recognizing my mouse nor my keyboard, so I came here.

The question is twofold -- how do I reaccess my desktop, and how do I install the rest of Intrepid:?:

---

### Post by Partyboi2 on 2008-11-16
Can you boot into recovery mode? If you can get to a terminal and your keyboard works try 
 ```
dpkg --configure -a
apt-get -f install
apt-get update
apt-get upgrade
apt-get dist-upgrade
```Hopefully this will continue finishing the upgrade.

---

