---
title: "grub-install: error: failed to get canonical path of `aufs'."
date: 2018-07-05
forum: Installation &amp; Upgrades
---

### Post by naruto.itachi on 2018-07-05
When I do boot-repair.
[http://paste.ubuntu.com/p/yDPkGztWNB/](http://paste.ubuntu.com/p/yDPkGztWNB/)

[https://community.linuxmint.com/tutorial/view/176](https://community.linuxmint.com/tutorial/view/176)
I tried to follow this tutorial but I am getting /usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.

---

### Post by deadflowr on 2018-07-05
Post moved to it's own thread.

---

### Post by oldfred on 2018-07-06
You need to turn off Windows fast start up.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Generally better to not use a separate /boot partition with most desktop installs. 
If a server install or full drive (erase Windows) LVM advanced volume management with encryption, you may then need a /boot partition.

---

### Post by yancek on 2018-07-06
> Re: grub-install: error: failed to get canonical path of `aufs'

The above would indicate that you are using a Live system from a DVD/usb and are trying to install Grub to it which won't work.  See the link below and take a look at the link down the page a bit on using chroot for this purpose.

[https://askubuntu.com/questions/921932/grub-install-error-failed-to-get-canonical-path-of-aufs](https://askubuntu.com/questions/921932/grub-install-error-failed-to-get-canonical-path-of-aufs)

---

