---
title: "Ubuntu not starting after uninstalling packages"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by ravisghosh on 2006-09-19
Hi,

I was going through installed packages in synaptic and found many packages (related bluetooth, print support, etc) which I felt were useless for my desktop. Hence, I completely removed them using synaptic. Now, on rebooting, I'm unable to start ubuntu. On selecting "recovery mode," it stops at "network configuration." Could not find anything relevant on forum.

1. Is there a way by using ubuntu liveCD to install those packages which i have uninstalled? Also, I do not remember the packages which I uninstalled!!!
2. In case, I need to reinstall ubuntu from liveCD, how can i save the packages (upgrades, etc) which were downloaded by synaptic. I had selected the option to keep packages in cache and hence the should be there in the hard disk. Could you please tell me where are they saved so that I can move them to some other location and then after installation put them back and upgrade (I dont have internet at the present time).
3. If I need to reinstall, then how can i make grub not to be installed in mbr (I dont have alternate cd but a live cd) since I boot from windows boot menu using bootpart and if mbr is written, then i have to do all the stuff to recover windows' mbr, etc.

Thanks in advance.

Ravi S Ghosh
ravisghosh at gmail dot com
PS: I'm kinda newB.

---

### Post by linear on 2006-09-19
Get a copy of the alternate install CD and boot from that. There is a "Rescue" option that will allow you to chroot to your broken install, then you should be able to use apt-get to reinstall missing pieces.

(There are some good troubleshooting threads in the sticky section of this forum that may help with specific issues.)

---

### Post by happy-and-lost on 2006-09-19
You probably unintentionally uninstalled the "ubuntu-desktop" package.

I'm assuming you can boot into a CLUI (Black screen, white writing) version of Ubuntu? It'll ask you for your default username/password. Enter them.

Right, you've now basically got the terminal.

```
sudo apt-get install ubuntu-desktop
```

Once that's all installed OK, "sudo reboot".

It should now boot back into the Ubuntu you're used to!

---

### Post by ravisghosh on 2006-09-19
No it does not even reach clui stage also. Its just black screen. Actually, i messed up with splash by configuring kernel but earlier it would go to the login screen, but after uninstalling packages, it would keep showing black screenig, no text line, nothing.

---

### Post by randell6564 on 2006-09-19
Just install it and use it until you are more familiar with how to Tweek it!

This should solve your problem.

---

