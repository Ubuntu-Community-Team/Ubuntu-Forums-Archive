---
title: "[SOLVED] Cannot Install Grub  - SOS"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by almos.dinnyes on 2008-08-26
Dear All,

my mother's laptop had XP and Xubuntu, now she decided to use Linux only.
First I tried to install an other linux distro - UHU Linux - due to some HW problems, but I decided to reinstall Ubuntu or Xubuntu. But I cannot!!! It is not able to install neither grub nor lilo. :(

I tried Ubuntu 7.04, 8.04.1 Xubuntu 8.04.1 alternate. But it doesn't work. Other linux distros - e.g. ZenWalk - or even XP can be installed, but not the Ubuntu. Why? What could be the problem?

I tried to install grub from the live cd, but doesn't install correctly: the menu.lst is missing.

Please, help me!

---

### Post by Pumalite on 2008-08-26
Post your specs.

---

### Post by jigsaws on 2008-08-26
Is your system installed? You should have menu.lst at /boot/grub/ but not at live cd. So you have to boot system (for example from live cd), then chroot to you hard drive installation. Then check your menu.lst and install grub.

---

### Post by almos.dinnyes on 2008-08-26
> **jigsaws said:**
> Is your system installed? You should have menu.lst at /boot/grub/ but not at live cd. So you have to boot system (for example from live cd), then chroot to you hard drive installation. Then check your menu.lst and install grub.

I don't have menu.lst on the mounted drive. After the installation I don't have grub under /boot, this is why I tried to install grub using the Live CD. It works, but doesn't create the menu.lst. :(


It seems, that this is a bug :( I found here a description, but the suggested solution doesn't work
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/63869](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/63869)

---

### Post by almos.dinnyes on 2008-08-26
What specs do you mean?

---

### Post by Pumalite on 2008-08-26
Memory, graphics, number and type of hard drives.

---

### Post by caljohnsmith on 2008-08-26
> **almos.dinnyes said:**
> I don't have menu.lst on the mounted drive. After the installation I don't have grub under /boot, this is why I tried to install grub using the Live CD. It works, but doesn't create the menu.lst. :(


It seems, that this is a bug :( I found here a description, but the suggested solution doesn't work
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/63869](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/63869)
Let's say "sdaX" is your Ubuntu partition; to install Grub to it from the Live CD, you can do the following:
```
sudo mount /dev/sdaX /mnt   [COLOR="Blue"][assumes you don't have sdaX mounted anywhere else, if so, "umount" it first][/COLOR]
sudo grub-install --root-directory=/mnt /dev/sda
```
That installs Grub to the MBR, and configures Grub to point to your sdaX partition for its system files, including menu.lst. "grub-install" does everything to install Grub except create a menu.lst, so you'll then need to do:
```
sudo chroot /mnt
sudo apt-get install grub  [COLOR="Blue"][this makes sure you at least have the Grub package installed][/COLOR]
sudo update-grub
cat /boot/grub/menu.lst
```
And post your menu.lst back here so we can make sure it is OK.

---

### Post by almos.dinnyes on 2008-08-26
> **Pumalite said:**
> Memory, graphics, number and type of hard drives.

128 MB ram, 40 GB harddisk, graphics - don't know integrated

---

### Post by almos.dinnyes on 2008-08-26
SOLVED:
I installed XP, and during the installation I created two partitions. After I installed xubuntu alternative, and removed the empty NTFS partition. Now it works. :)
So it was not enough to install XP, or using fixmbr.

Thanks for your help!

---

