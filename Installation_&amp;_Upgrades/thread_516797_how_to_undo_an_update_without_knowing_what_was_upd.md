---
title: "how to undo an update without knowing what was updated?"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by rohan000 on 2007-08-03
Update Manager installed 22 updates and told me to restart the computer. After that my wired network connection stopped working.
I want to undo the update. But I don't know exactly what packages were updated. Synaptic's history has no record of this update at all, although it lists all past updates before today.

---

### Post by Pumalite on 2007-08-03
How many kernels appear in your grub? You can always boot the the anterior kernel. Do the update again, but this time untick the kernel update.

---

### Post by rohan000 on 2007-08-03
There are two kernels in grub, but they are the same ones that were there before. Booting into an old kernel doesn't help.

---

### Post by floke on 2007-08-03
Look for the 'history' option in synaptic - it will give you a complete record of what has been updated.

---

### Post by Pumalite on 2007-08-03
If you had to reboot is probably because you updated your kernel. Usually the old kernels are left to be deleted by the user if wanted.

---

### Post by rohan000 on 2007-08-03
Synaptic does not list anything about this update in its history.

---

### Post by rohan000 on 2007-08-03
How can I return to an old kernel? I've tried all the kernels listed in grub. All of them are the same kernels that were listed there before.

---

### Post by Pumalite on 2007-08-03
That I know of, Ubuntu does not require a reboot after an update, unless the kernel has been updated. When the kernel has been updated, the next time that Grubs show up, it gives several choices, among which is the old kernel. If that is not the case, I don't know what happened.

---

### Post by rohan000 on 2007-08-03
thanks for helping... the internet problem suddenly fixed itself somehow although I don't understand why the update is missing from synaptic. I think a dbus update made it require a restart.

---

### Post by mikewhatever on 2007-08-03
Here's what's been upgraded on my system yesterday.
> Commit Log for Fri Aug  3 17:24:33 2007


Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
firefox (2.0.0.5+1-0ubuntu1) to 2.0.0.6+1-0ubuntu1
firefox-gnome-support (2.0.0.5+1-0ubuntu1) to 2.0.0.6+1-0ubuntu1
gimp (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-data (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-python (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libgimp2.0 (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libgl1-mesa-dri (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgl1-mesa-glx (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libglu1-mesa (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libnspr4 (2:1.firefox2.0.0.5+1-0ubuntu1) to 2:1.firefox2.0.0.6+1-0ubuntu1
libnss3 (2:1.firefox2.0.0.5+1-0ubuntu1) to 2:1.firefox2.0.0.6+1-0ubuntu1
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
mesa-utils (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
python-launchpad-bugs (0.1.13) to 0.1.13.2
tcpdump (3.9.5-2) to 3.9.5-2ubuntu1

Even if you figure out what was upgraded, there is no roll back feature in synaptic.

---

### Post by kpictjl on 2007-08-03
Your problem magically fixed itself, but I have the same issue. 

> **rohan000 said:**
> Update Manager installed 22 updates and told me to restart the computer. After that my wired network connection stopped working.
I want to undo the update. 

I'm running Feisty and accepsted the latest automatic update this evening.  It had me reboot after the update.  Now all 3 of the PCs on my network are flaky.  All are DHCP and think my feisty box i the dhcp server instead of my router.  Then my feisty box and 1 windows box thinks the windows box is the DNS instead of my router.  

When I power off my Feisty box then and restart the network then my other 2 PCs work fine.

I can also configure static IPs and all is well...I just don't want to do that!

Below are the updates I took this evening.  On the surface none of these look like networking relating updates but obviously something if screwy.

```
Commit Log for Fri Aug  3 21:02:37 2007

Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4

```

Any help is appreciated.

---

