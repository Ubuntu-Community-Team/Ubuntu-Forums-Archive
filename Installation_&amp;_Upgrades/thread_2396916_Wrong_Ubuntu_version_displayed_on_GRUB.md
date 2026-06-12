---
title: "Wrong Ubuntu version displayed on GRUB"
date: 2018-07-23
forum: Installation &amp; Upgrades
---

### Post by satimis on 2018-07-23
Hi all,

At booting GRUB menu shows```

GNU GRUB Version 2.02
ubuntu
Advanced options for ubuntu 16.04.4 LTS (16.04) (on /dev/sda1)
+System setup

```

On terminal after bootup
$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic

```

This is a new Ubuntu 18.04 gnome desktop and its ISO was recently download on Ubuntu website.  It was installed on a new 2TB SSD from an USB stick.

Is there any way to fix this problem.  OR I have to reinstall Ubuntu 18.04?

In the later case do I need to re-download its ISO on Ubuntu website?

Please advise.  Thanks

Regards
satimis

---

### Post by westie457 on 2018-07-23
Purge and reinstall Grub using this old and still relevant guide. [https://ubuntuforums.org/showthread.php?t=1581099](https://ubuntuforums.org/showthread.php?t=1581099)

Or purge and reinstall Grub using BootRepair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have to do a fresh installation you can use the ISO you already have on a USB stick.

---

### Post by satimis on 2018-07-23
> **westie457 said:**
> Purge and reinstall Grub using this old and still relevant guide. [https://ubuntuforums.org/showthread.php?t=1581099](https://ubuntuforums.org/showthread.php?t=1581099)

Or purge and reinstall Grub using BootRepair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have to do a fresh installation you can use the ISO you already have on a USB stick.
Hi,

Thanks for your advice and links.

Something strange has happened here.  After having installed Ubuntu 18.04, on booting no GRUB menu showed up.

Then I edited /etc/default/grub and comment out the line "GRUB_HIDDEN_TIMEOUT=0"

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

ran;
$ sudo update-grub
$ sudo reboot

Then it came to the situation as mentioned on my original posting.

Just a moment ago I re-edited /etc/default/grub deleting '#' and ran;
$ sudo update-grub
$ sudo reboot

At booting the GRUB menu didn't show up.

Again I edited /etc/default/grub, commenting out that line and ran;
$ sudo update-grub
$ sudo reboot

This time at booting the GRUB menu shows differently as follow;```

Ubuntu
Advcanced options for Ubuntu
* System setup

```
only 3 lines

It surprises me.

Start an Ubuntu 18.04 VM (This is a virtualization PC, running Oracle VirtualBox)

GRUB menu
```

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

```


I'll add back all other drives which have been disconnected during installing Ubuntu 18.04 and see what will happen before re-installing it.

Ah, one further question would it be possible to re-install Ubuntu 18.04 without touching other files/data on this SSD?

Thanks

Regards
satimis

---

