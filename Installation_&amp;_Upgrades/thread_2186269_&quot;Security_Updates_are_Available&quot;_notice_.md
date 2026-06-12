---
title: "&quot;Security Updates are Available&quot; notice will not go away"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by qajaq on 2013-11-06
I've run ```
$ apt-get update
``` followed by ```
$ apt-get upgrade
```. . . but when I re-boot I still get the pop-up telling me that "Security Updates are Available."

I looked at the Muon Package Manager, filtering for installed software, and all items show "No Change."

I'm running Kubuntu 12.04, and this problem has persisted since I installed the OS, a little over a year ago. Any ideas why this pop-up keeps hanging around?

---

### Post by Old_Grey_Wolf on 2013-11-06
sudo apt-get upgrade does not install all security updates; such as, kernel upgrades.

Have you tried ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Edit: if it has been a year since you did a kernel upgrade, I would recommend a backup of important files before you do it.

---

### Post by qajaq on 2013-11-08
That did it -- Thank you! (And yes, my files are backed-up daily.)

---

