---
title: "can't intall and update anything"
date: 2017-07-15
forum: Installation &amp; Upgrades
---

### Post by virat18 on 2017-07-15
Every time i try to install or update, the below error occurred.

viratkarthi@ViratKarthi-HP-Notebook:~$ sudo apt-get upgrade
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

kindly suggest me how to install, Thanks:)

---

### Post by ajgreeny on 2017-07-15
You can ignore the first line in those errors as it is a known bug; you can continue to ignore the error or remove the file as it is a relic from previous systems and does nothing anymore. Try ```
sudo rm /etc/apt/apt.conf.d/20auto-upgrades.ucf-dist
```
The other errors are usually the result of having another application using apt open when trying to update or install a package.
Have you got update-manager open or is the auto-upgrade process in action?
Either shut the update-manager or just wait a few minutes and the manual installation or upgrade may work.

---

### Post by virat18 on 2017-07-17
yes, it works now:p..

Thanks for your kind reply:)

---

### Post by ajgreeny on 2017-07-17
Great news!

Please mark as Solved in Thread Tools at TP of thread.

---

