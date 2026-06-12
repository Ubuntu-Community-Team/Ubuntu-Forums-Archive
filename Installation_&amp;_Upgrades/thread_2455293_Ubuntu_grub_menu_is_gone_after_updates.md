---
title: "Ubuntu grub menu is gone after updates"
date: 2020-12-16
forum: Installation &amp; Upgrades
---

### Post by xyschen4 on 2020-12-16
[https://paste.ubuntu.com/p/S8zGkDT62H/](https://paste.ubuntu.com/p/S8zGkDT62H/)

tried boot-repair from live Ubuntu18.04 usb key, asked to create a ESP partition, which exists already...

---

### Post by grahammechanical on 2020-12-16
Which operating system was updated? Windows updates are known to change the boot order so that Windows is the default operating system to load. The Windows boot menu does not recognise any operating systems except those from Microsoft.

You may need to open the UEFI settings utility to change the boot order.

Regards.

---

### Post by tea for one on 2020-12-17
I assume that you can still boot into Ubuntu and your Grub menu is not displayed after power on?

It looks like you may need to alter the Grub configuration:-
```
sudo nano /etc/default/grub
```

Change GRUB_TIMEOUT_STYLE=[COLOR="#FF0000"]hidden[/COLOR] to GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR]
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Ctrl o to save and Ctrl x to exit then run via a terminal:-
```
sudo update-grub
```

---

