---
title: "How to download debs on another computer?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by polka on 2006-06-23
I am on a dialup  and have access to high speed connection at a friend's house.

How can I get a list of the .debs that I need and the correct mirror to use to complete an upgrade or dist-upgrade? Apt-get upgrade only lists the names of the packages; not really the same as the name of the debs, and how   do I know which mirror to use; universe, restricted, security etc.?

thanks for any leads
Jerry

---

### Post by aysiu on 2006-06-23
You're trying to do a dist-upgrade? Just download the .ISO for the alternate CD of your choice (not the desktop CD)--Xubuntu, Ubuntu, or Kubuntu.

Burn it as a disk image.

Pop it in your Ubuntu and ```
sudo apt-cdrom add
sudo cp /etc/apt/sources.list /etc/apt/breezy.list
sudo nano /etc/apt/sources.list
``` Delete all the sources except the CD one you just added. Then save (control-x), confirm (y), and exit (Enter).
```
sudo aptitude update
sudo aptitude dist-upgrade
``` If you want additional software, consider using [UbuntuPlus](https://ubuntuplus.bountysource.com/). Downloading individual .deb files and their dependencies on another computer is a pain.

**Edit**: Actually, your best bet is to bring a Ubuntu live CD to your friend's house, clean out /var/cache/apt/archives and then ```
sudo aptitude update
sudo aptitude install whateverpackageyouwant
``` and then copy the /var/cache/apt/archives to your computer's desktop and ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by polka on 2006-06-24
You're right it looks like a pain to download to another computer.

Ubuntu plus looks like it might be helpful. I will try that.
Thanks
Jerry

---

