---
title: "Package installation makes screen go blank"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by Dunadan on 2006-09-17
When I installed Ubuntu on my computer, it said to restart, then type "sudo -oem-config-prepare" to install the packages. So I followed the directions and the screen went blank, flashed a cursor, went blank, etc. for a while. When it finally came back on, it gave me an error message & told me to create a new user an reboot, after which it would finish installing. Well, I created the new user, rebooted, but nothing happend. Now I'm stuck at the command prompt, and I don't know how to install the packages.

---

### Post by Dunadan on 2006-09-22
Does anyone have any suggestions?

---

### Post by wpshooter on 2006-09-22
What version of the CD download are your using, DESKTOP, ALTERNATE, or SERVER ?

Sounds like to me that maybe you are using the **server** version.  If so, is that what you really want to be using.

You probably need to download, burn and use the **DESKTOP** CD.

---

### Post by dlehman on 2006-09-23
```
aptituide install ubuntu-desktop
```

this will get you a desktop enviroment.

I also have a similar problem, I have installed ubuntu on three comps so far two of them very old. now I am trying to install on a newer emachines but it has a old monitor every time the installer gets to configre xserver the screen goes blank I have tried with different monitors also.  when I reboot it says no operating system found.  this computer is shareing a hard drive with windows, windows is on the first half and linux on the last half will that cause a problem with booting, and it should not cause a problem with X.  thanks for any help I will continue serching

---

