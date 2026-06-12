---
title: "Kubuntu 16.04 LTS: How to boot to text console?"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by Nigel_Pain on 2019-09-11
I've just upgraded from 14.04 to 16.04. I'd edited /etc/default/grub to add the word "text" to GRUB_CMDLINE_LINUX_DEFAULT and un-commented GRUB_TERMINAL=console (not sure if this makes a difference). Then ran update-grub. This caused the console to reboot to the command line in 14.04. But after upgrading it boots to the graphical terminal. I need a command line to reconfigure network settings before I can get an ssh session. This is a VMWare virtual machine and the graphical console doesn't respond to the mouse.

---

### Post by dino99 on 2019-09-11
An old answer: [https://askubuntu.com/questions/215089/starting-linux-in-text-mode-using-grub2](https://askubuntu.com/questions/215089/starting-linux-in-text-mode-using-grub2)
Help: [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Nigel_Pain on 2019-09-11
Found the answer:

To boot Ubuntu 16.04 Desktop without X one time, add ```
systemd.unit=multi-user.target
``` to the linux command line in GRUB.
To make this the default, use ```
sudo systemctl set-default multi-user.target
```
To return to default booting into X, use ```
sudo systemctl set-default graphical.target
```
To see the current default target, ```
sudo systemctl get-default
```

---

