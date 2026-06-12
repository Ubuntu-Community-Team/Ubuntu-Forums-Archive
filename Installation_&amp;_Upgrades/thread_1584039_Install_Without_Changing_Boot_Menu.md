---
title: "Install Without Changing Boot Menu"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-09-28
Maybe a stupid question but i do like to checkout other distros from time to time and then mostly chunk them.So i was wondering if there was a way to install a distro without taking over the previous os boot menu? I have Ubuntu and Mint installed and Ubuntu has control over the boot menu right now.

Thanks,

---

### Post by oldfred on 2010-09-28
Most installs except windows let you choose where or whether to install a boot loader. Just choose not to install the boot loader. Running sudo update-grub from Ubuntu should then find the new install.

If you do end up overwriting the MBR just reinstall grub2 to the MBR. 

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

If you can boot into any install then you do not have to install from the liveCD but from whatevery install you have booted.

---

### Post by dontgetshocked on 2010-09-28
Thanks so much

---

### Post by plucky on 2010-09-29
> **dontgetshocked said:**
> Maybe a stupid question but i do like to checkout other distros from time to time and then mostly chunk them.So i was wondering if there was a way to install a distro without taking over the previous os boot menu? I have Ubuntu and Mint installed and Ubuntu has control over the boot menu right now.

Thanks,

Try [Virtualbox](http://www.virtualbox.org/wiki/VirtualBox) if your computer has enough memory.

Good luck

---

