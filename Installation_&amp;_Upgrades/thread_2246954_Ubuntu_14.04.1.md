---
title: "Ubuntu 14.04.1?"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by wolfen10862 on 2014-10-04
I just finished downloading Ubuntu 14.04.1, its an LTS, is this simply an upgrade or when I burn it and boot will it wipe everything and start over again?
Sorry about asking without looking around first but I'm currently taking a break from splitting 3 ton of wood for winter

---

### Post by fly-by-night on 2014-10-04
Your choice. 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Upgrade is available from within an already running Ubuntu.

---

### Post by Topsiho on 2014-10-04
A howto install Ubuntu can be found here:
[http://www.wikihow.com/Install-Ubuntu-Linux](http://www.wikihow.com/Install-Ubuntu-Linux)
It sounds intimidating, but once you have done it once, you'll find it is not.
You can upgrade from one version to the next version; if it is an LTS you can update from one LTS to the next LTS.
So you can upgrade from 13.10 to 14.04 LTS, or ftom 12.04 to 14.04 LTS.
The versions such as 14.04.1 (point releases, the next one will be 14.04.2) are just to prevent having to do to many updates after an install.

Hope this helps you splitting your wood :)

Topsiho

---

### Post by wolfen10862 on 2014-10-04
Ok guys I know I might have sounded stupid, but I am already on Ubuntu, its the only operating system I have any more since windows heft me hi, dry and mad as hell, XP was my last windows O/S I have 14.04.1 on a dvd just in case, but if it will automatically update,.......when? I'm patiently waiting, and so far theres been one update today, and the overview in settings says 14.04LTS
I'm just wondering if I'll lose everything I have if I boot or will it simply upgrade me.

when I first started with Ubuntu it did seem intimidating, but I did a duel boot with XP for a while so I could play a few windows games, now I simply run them through wine 
Last time I put the Ubuntu 14.04 disk in I wiped everything windows and put Ubuntu on a 500 gig hdd

---

### Post by Vladlenin5000 on 2014-10-04
If you're already running 14.04 the updates will take you to the next point automatically. No further actions needed.
It won't show differently in settings.

---

### Post by deadflowr on 2014-10-04
14.04.1 has already been available for at least a month.
Look at the command
```
lsb_release -a
```
should look like
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

```
**Description:    Ubuntu 14.04.1 LTS**

---

### Post by gordintoronto on 2014-10-05
Let me restate Vlad's point: if you are already running 14.04, you should ignore 14.04.1, since it just includes the updates you have already applied.

---

### Post by grahammechanical on 2014-10-05
When we boot a Ubuntu ISO image that we have burned to a DVD disc or USB memory stick we get 2 options - Try Ubuntu and Install Ubuntu. If we select Install Ubuntu we start a process that can lead if we are not careful to re-installing the OS and wiping out everything. But it does not happen automatically. 

If you already have 14.04 installed then just rely on the Update Manager to take care of things. We do not need to update/upgrade from the latest ISO image.

Regards.

---

