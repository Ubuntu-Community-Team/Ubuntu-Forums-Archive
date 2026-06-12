---
title: "TTY1 page after ssh upgrades"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by Daniel_George on 2015-11-18
I foolishly decided to install upgrades over ssh. My connection dropped, and when i came home i saw the desktop had no toolbar or sidepanel, only the file explorer was open. Since i could not access any restart buttons, i did a power cycle and when my screen came back up, it loaded into TTY1. The system is now "read only" and since i have an admin user (therefore no longer the default root password) that it does not recognize, i can "login", but cannot do any sudo operations.

Things i've tried
[LIST]
[*]I have tried running startx, but that doesn't work since i'm not root.
[*]I've tried running the boot-repair tool from a live boot cd. This does seem to have some effect. After running it the first time, i no longer boot into TTY1, but rather the Grub menu and after choosing ubuntu, the screen goes black. If i choose advanced, it hangs at "Loading initial Ramdisk". I tried running the boot-repair once more and now i'm back to TTY1.
[*]
[/LIST]
Here are the boot info links from the two times i ran the boot-repair tool
[http://paste.ubuntu.com/13322721](http://paste.ubuntu.com/13322721)
[http://paste.ubuntu.com/13324544](http://paste.ubuntu.com/13324544)
The volume of note here is sdd (160GB). all other mounts are media disks and flash drives.

I would love not to have to wipe the OS, because i have a lot of web server and other configurations that i don't want to restore, but if that's my only option....

---

### Post by Lars Noodén on 2015-11-18
The matter is not so much ssh as was interrupting the machine with a powercycle while it was working.  

If you boot into recovery mode, one of the options should be to check all file systems with [fsck](http://manpages.ubuntu.com/manpages/trusty/en/man8/fsck.8.html).  That should allow you to get back to a read-write system when you reboot.  Then you should be able to log back in and do "sudo apt-get -f install" to fix broken packages.  

In the future, if you have any risk at all of broken connections, consider doing your work inside a screen or tmux session.  That way if the connection breaks you can reconnect and rejoin the session in progress, uninterrupted.

---

