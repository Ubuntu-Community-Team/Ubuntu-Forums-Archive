---
title: "Ubuntu freezes on purple screen when loading"
date: 2017-09-17
forum: Installation &amp; Upgrades
---

### Post by tho4 on 2017-09-17
I tried to reinstall java yesterday and after rebooting my computer freezes on purple screen. What i tried so far: 

1/ I did the following changes in /etc/default/grub: 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash nomodeset"
sudo update-grub
``` I also get a purple screen.

2/I set it to ```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
``` and got to the tty1 console.

---UPDATE---

3/ I read in other forums it might be related to a corrupted driver from my Nvidia graphic card, so I did the following:
```
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
```
I selected the recommended driver from all drivers listed under "ubuntu-drivers devices", and I installed it as follows:
```
sudo apt-get install nvidia-384
sudo apt-get update
```
I rebooted my computer but I am still stuck at the same point :roll:

I have a HP envy dv6 and I am on Ubuntu 16.04.3. Any help, suggestions?

---

