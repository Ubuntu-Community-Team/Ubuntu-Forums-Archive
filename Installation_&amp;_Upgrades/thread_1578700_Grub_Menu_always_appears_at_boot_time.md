---
title: "Grub Menu always appears at boot time"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Tipo on 2010-09-20
Hello,

Ubuntu (10.04.1) used to boot without showing the grub menu. I just updated the kernel, and now it stops at the grub menu for several seconds before selecting the default (newest) kernel and booting. Any ideas as to why this suddenly changed?

here's the active contents of my /etc/default/grub file:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Nothing in there suggests to me that the grub  menu should NOT be hidden. Looking at the logs, Apt appears to have correctly run update-grub at the time of the install, and I've also run update-grub by hand to no effect.

---

### Post by Tipo on 2010-09-20
Ah, from reading this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It appears that the ```
GRUB_HIDDEN_TIMEOUT=0
``` option only hides the grub menu if only one OS is installed. I've got a second hard drive with Fedora that wasn't around when I did the last kernel update, and it appears that Grub has found that OS and placed it in the list.

Nevermind, then :)

---

