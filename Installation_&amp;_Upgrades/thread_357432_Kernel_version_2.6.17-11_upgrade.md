---
title: "Kernel version 2.6.17-11 upgrade"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by phenest on 2007-02-09
It looks like the upgrades to the new kernel version 2.6.17-11 had appeared before the actual kernel installation itself. I suddenly had 8 new items. 4 were the new kernel installations and 4 are the upgrades. I switched the upgrades to "no change" and installed the rest. Then restarted my machine (seemed a good idea).

I write all this because I then stumbled on a problem. I could only get a terminal login screen. Nothing graphical. I tried
```
sudo /etc/init.d/kdm start
```
to find out kdm was already running (I'm using Kubuntu BTW).

I realised that, because of the new kernel, I needed to re-install my nVidia driver.

Method:
```
sudo /etc/init.d/kdm stop
/sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
Once that finished, I rebooted:
```
sudo reboot
```
Et voila! All is well.

Then installed the upgrades as all is fine.

---

