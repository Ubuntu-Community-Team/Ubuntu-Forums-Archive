---
title: "Upgrade froze, now system won't boot (even with Live CD)"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by cwgosling on 2011-02-21
Yesterday my wife was using our laptop and an upgrade manager dialogue box came up. She clicked yes to install upgrades, but at some point during this process the machine froze. She restarted, and I haven't been able to successfully boot since then.

the final screen when trying to boot from the hard drive reads:

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1uuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    2.780389] ieee1394: Host added:  ID:BUS[0-00:1023]  GUID[474fc0001c9f2881]


I'm slowly getting the hang of Ubuntu. By now I know enough that a Live CD can fix most problems. So that's where I went after doing several searches about the error messages that were appearing. The menu screen works, but I can't get it to boot into the "Try ubuntu" mode. I tried changing the boot parameters to no avail. As the boot tries to load I can see a line by line report of errors- some are I/O errors and are in white, but many were in red, which seems bad from my mostly ignorant perspective. 

I saw lots of SQUASHFS errors among other things. I took a snapshot of the screen that was displayed when the boot failed- it's attached to this post (lots and lots of text to be typed otherwise). The reason I know it failed is because I've tried a half dozen times with the same exact result- once I let it sit for an hour+ just to make sure it was really frozen (a bit optimistic).

Relevant info: 
Ubuntu is running on a Dell Inspiron 8600 laptop. I think it's version 9, but could be 10. The Live CD I'm using is version 10 burned 1/4/2011. 

I'd be thrilled to hear any suggestions that folks might have. Thanks for the help!

---

### Post by TimEnid on 2011-02-21
try the suggestions in this thread. i had a similar issue yesterday
[http://ubuntuforums.org/showthread.php?t=1691949](http://ubuntuforums.org/showthread.php?t=1691949)

---

### Post by cwgosling on 2011-02-21
Thanks for the advice. It didn't work though... here's what I tried and what I got.

(initramfs) sudo reboot
/bin/sh: sudo: not found

apt-get: not found

and the list goes on (gnome-session: not found, sudo dpkg, startx, etc....)

rm ~/.Xauthority also failed- no such file or directory.

Any other ideas?

Thanks!

---

### Post by cwgosling on 2011-02-21
Is there a good reason why I can't boot from the Live CD? I feel like I'd have a fighting chance if I could get that far...

---

