---
title: "Package manager performance problems since Feisty upgrade"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by axe87 on 2007-04-30
Hi,

Just upgraded to Feisty and am now experiencing severe performance problems when running any of the package managers (Adept, Add/Remove Applications, Synaptic, etc). Everything seems OK when I launch the package manager of choice and do an search for package. However, if I then do another search or try and install a package my system grinds to a halt and the disk thrashes without seeming to finish (I've let it run for up to an hour to see if it stops).

I've tried both the GNOME and Kubuntu desktops and have the same result. I'm running Ubuntu on a Compaq n610c laptop.

Everything else seems to work OK.

---

### Post by bulldog on 2007-04-30
Can you perform in a terminal```
sudo aptitude update && sudo aptitude upgrade
```
Look carefully for any error.

---

### Post by axe87 on 2007-04-30
Thanks, this seemed to work fine with no obvious errors, just four unused packages for removal.

I'm trying to isolate the process that is hammering the disk. I'm not sure but dpkg-preconfigure is the only 'running process'. Having said that gnome-app-install is occupying about 70M of memory!

---

### Post by axe87 on 2007-05-01
I'm not much further forward with this. I tried killing gnome-app-install and this allowed the install to complete, but with the following errors displayed:

X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device

I also discovered errors relating to wacom in the xorg log. However having checked around the forums etc, I'm wondering whether this is a blind alley or not:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42553/comments/21](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42553/comments/21)

Anyway I tried commenting out the wacom entries in my xorg.conf. The result was that the x environment didn't boot, I got a shell login instead.

---

### Post by axe87 on 2007-05-01
Problem solved.

It seems I was looking in the wrong place. My swap partition wasn't enabled. This appears to be because the UUID for the device had changed and therefore it failed to be mounted at boot time. I assume this happened when upgrading to Feisty - not sure if this is a bug or not.

---

