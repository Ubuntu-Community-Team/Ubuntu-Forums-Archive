---
title: "Don't want dual boot"
date: 2018-02-09
forum: Installation &amp; Upgrades
---

### Post by jmncrr on 2018-02-09
i have installed ubuntu 17.1 on one hard drive, and windows on another. The problem is shortly after installing ubuntu on the separate hardrive, and after some updates to ubuntu their is a dual boot with windows which is on a second hardrive. How do i change the boot loader so their is no dual boot, and prevent it from happening again. Sorry if this is a dumb question, but any detailed response to change this is appreciated.

---

### Post by Dennis N on 2018-02-09
You need to disable the os prober on Ubuntu so grub does not detect the OS on the 2nd drive. Easy to do from Ubuntu terminal with this command:
```
sudo chmod -x /etc/grub.d/30_os-prober
```
then run
```
sudo update-grub
```
and reboot.

---

### Post by jmncrr on 2018-02-09
Thanks a lot Dennis N. That sure was easy, and i appreciate your help.

---

### Post by 1clue on 2018-02-09
If you want access to that Windows install you can set it up as a VM, you'd get access to both operating systems at the same time.

IMO dual booting is useless, but having multiple operating systems available simultaneously is great.

But this won't work if you have an OEM Windows that came with your machine. It would only work with something you bought and installed from Microsoft.

---

