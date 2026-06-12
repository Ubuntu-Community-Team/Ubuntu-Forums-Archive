---
title: "Possible Issue with HAL"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by kportertx on 2007-05-12
Running on an HP Pavilion ze2000  OS:Ubuntu Fiesty Fawn

Update manager updated HAL today.  Now when I log off the laptop locks up.

Also added desktop manager Enlightenment.  These are the only Items changed on the Laptop when the issue started happening.

Sorry for being so brief but gotta go to work :(.  

V/R
Kevin

---

### Post by KevinCLovesU on 2007-05-13
Ever since I updated HAL, my laptop takes several tries to boot up, often locking up during the boot process. I can tell not only because nothing works, but also because caps lock blinks. Does anyone know what that blinking specifically means?

---

### Post by kportertx on 2007-05-13
My laptop cannot hold a connection well through wireless.  The signal strength is jumping from 0 to 60% and anywhere in between, also occasionally disconnects.  I using a Compaq wl110 wireless card.  This also did not occur till I updated HAL.  I couldn't see how Enlightenment could cause the problem but I removed it through Synaptic, still having the same troubles as before.

V/R,
Kevin

---

### Post by mlind on 2007-05-13
Revert the updates and pin working hal?
Was this update from backports repository?

---

### Post by kportertx on 2007-05-13
> **mlind said:**
> Revert the updates and pin working hal?
Through Synaptic I tell it to force from HAL version 0.5.9 to 0.5.8, says it must remove hal-info, I pressed ok and apply updates and it fails to downgrade.

> Was this update from backports repository?
Yes it is from backports repository.

V/R
Kevin

---

### Post by mlind on 2007-05-14
This should work. Remember to pin the working hal package after the downgrade
```

sudo aptitude install hal/feisty libhal1/feisty libhal-storage1/feisty hal-device-manager/feisty

```

---

### Post by kportertx on 2007-05-14
When I do as you said I get an error.

laptop@laptop-laptop:~$ sudo aptitude install hal/feisty libhal1/feisty libhal-storage1/feisty hal-device-manager/feisty
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  hal-info
The following packages will be DOWNGRADED:
  hal hal-device-manager libhal-storage1 libhal1
0 packages upgraded, 0 newly installed, 4 downgraded, 0 to remove and 0 not upgraded.
Need to get 575kB/1462kB of archives. After unpacking 324kB will be freed.
The following packages have unmet dependencies:
  hal-info: Conflicts: hal (< 0.5.9) but 0.5.8.1-4ubuntu12 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
hal-info

Score is -301

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  hal-info
The following packages will be DOWNGRADED:
  hal hal-device-manager libhal-storage1 libhal1
The following packages will be REMOVED:
  hal-info
0 packages upgraded, 0 newly installed, 4 downgraded, 1 to remove and 0 not upgraded.
Need to get 575kB/1462kB of archives. After unpacking 659kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libhal1 0.5.8.1-4ubuntu12 [287kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libhal-storage1 0.5.8.1-4ubuntu12 [287kB]
Fetched 575kB in 4s (132kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
[COLOR="DarkRed"]debconf: falling back to frontend: Readline
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `07]' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `07]' must be followed by colon[/COLOR]
laptop@laptop-laptop:~$

---

### Post by mlind on 2007-05-14
I think you were just hit by a dpkg bug [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012) or similar.

Could you gzip your /var/lib/available file and attach it?

---

### Post by kportertx on 2007-05-14
Requested file.

---

### Post by kportertx on 2007-05-15
Thank you for your assistance in directing me to the source of the problem.  In the same folder there was a available-old.  I moved available to available-corrupt and copyed available-old to available.  Seems to be working now.  I am not sure what had caused the issue, but the very last items I installed were enlightenment, I also later removed the enlightenment packages just incase they were causing the original problems I posted about.  So the new issue w/ available didn't occur till I removed those packages.  I am now going to attempt to downgrade hal.  I will reply as to how that goes.

V/R
Kevin

---

### Post by kportertx on 2007-05-15
Worked!! No longer locks up when I log off and the internet signal is not all over the place.  Great thanks a lot

Kevin

---

### Post by mlind on 2007-05-15
Good you got it sorted out. Are you using preloading btw? By looking your attachment it seems that preload wrote in the wrong file while rotating the logs. If this happens again, you should file a bug report. Seems like a grave issue to me.

---

### Post by kportertx on 2007-05-15
Yes I am running prelink and I will keep that in mind if it happens again.

Thank again,
Kevin

---

### Post by kportertx on 2007-05-15
fsck detected a lot of errors on my system.  I removed preload hoping that may have caused the problem.  I hope my hardrive isn't going out :(

---

