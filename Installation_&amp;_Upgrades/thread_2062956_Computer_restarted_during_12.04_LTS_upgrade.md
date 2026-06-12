---
title: "Computer restarted during 12.04 LTS upgrade"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by Ketsundere on 2012-09-26
I was upgrading from 11.10 to 12.04 and the upgrade froze,  and then booted me out to the login screen. From there I can't do  anything, trying to log in just returns me to the login screen. What do I  do?

---

### Post by darkod on 2012-09-26
Depending at which stage it froze, try this:
Boot into the recovery mode, not the normal mode (if you don't get the grub menu at boot hold Shift to show it).

Once you are presented with the recovery menu, select Network first so that it connects you to internet and mounts root read/write.
After that select Drop to root shell from the menu.

At the root shell, try:
```
dpkg --configure -a
apt-get install -f
```

That should try to finish configuring all packages pending configuration, and try to fix all broken packages in apt-get.

If it appears to finish without errors, reboot and see if you can boot normally.

---

### Post by Ketsundere on 2012-09-26
I was able to boot up in recovery mode, but it didn't present me with any sort of menu. It went to a recovery version of the regular login screen. Also, my mouse (I have a touchpad and one of those Thinkpad nipple mice) didn't work.

---

### Post by darkod on 2012-09-26
Hmm, I have never heard of that. The recovery menu is different to the standard login screen, and you can use only the keyboard for it, no need for a mouse. It's text based, not GUI based. Sort of like the alternate installer or the XP installer.

What if you try to select Previous Versions from the grub boot menu, and in there select the recovery entry for a previous kernel version, for example the one before the latest one.

The older kernels are joined under the Previous Versions title so that they don't create huge grub menu.

---

### Post by Ketsundere on 2012-09-26
Yeah, selecting a recovery mode from a previous version worked. But when I tried to turn networking on, I got this message:

modem-manager [948]: <info> Caught signal 15, shutting down

And it didn't even go back to the menu or anything, it just sat there and I had to shut down by holding down the power button which I really don't want to do again. I'm considering just backing up my files using a Live CD and completely reinstalling Ubuntu.

---

### Post by darkod on 2012-09-26
Hold on, there is chance yet. The main thing to activate the network was to mount as RW and to have internet if needed. If you use cable connection it should have worked in most cases. If you are trying this on wi-fi, it might not be able to connect in recovery mode.

In any case, you can try this:
Select the Drop to root shell in the menu (without selecting Network first), and then remount as RW with:
```
mount -o remount,rw /
```

That should remount it RW. After that run the commands suggested above.

---

### Post by Ketsundere on 2012-09-26
OH nevermind I just figured it out. Okay going to try that now.

EDIT: That solved it! Thank you so much for all of the help.

---

