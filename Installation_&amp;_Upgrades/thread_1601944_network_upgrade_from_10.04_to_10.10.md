---
title: "network upgrade from 10.04 to 10.10"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by jfbooth on 2010-10-20
I think I have a big problem.  Doing a network upgrade from Xubuntu 10.4 to 10.10.  It is quite a bit more than 1/2 done .. shows 1 hr, 9 min remaining.

It seems to be stuck .. been sitting at the same spot for at least an hour ... maybe 2.

Terminal window in the upgrade window .. last few lines:

Removing update-grub hooks from /etc/kernel-img.conf in favour of /etc/kernel/ hooks.
Replacing config file /etc/default/grub with new version
Installation finished.  No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
           [B]THEN 10 MORE FINDS
AND IT SEEMS TO BE STUCK ON THE 11TH FIND[/B]
found memtest86+ image: /boot/memtest86+.bin

and it is just sitting there.  Am at a total loss as to what to do.  Any advice is appreciated in advance.

---

### Post by jfbooth on 2010-10-20
I think I lunched it.  After waiting, I decided to 'do something' and hit Ctrl C to terminate the update.  Things went downhill from there.  Rebooted .. got a 'recovery screen'.  It listed some choices and I tried a few that did not work.  I then tried the second one from the top .. something about a version RECOVERY.  It LOOKED to me like it might be doing something LIKE Windows System Restore ..sort of.  Looked to me like it was installing everything.  After a long time, it finished.  Now, on a boot, I see Ubuntu 10.10 .. but it boots to what I think is called a shell .. no GUI.

Unless someone can reply to this with some advice, I will probably have to install 10.10 from scratch ..to an empty drive.

Anyone have any?  Thanks in advance.

---

### Post by jfbooth on 2010-10-22
Never did succeed with a network upgrade.  Tried it several times and it never would boot to a GUI.  Ended up burning a Live CD and installing from that with little to no problem.

---

