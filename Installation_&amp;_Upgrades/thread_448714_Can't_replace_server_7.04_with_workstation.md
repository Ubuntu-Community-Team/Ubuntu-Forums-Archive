---
title: "Can't replace server 7.04 with workstation"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by bwise-3rxU on 2007-05-19
I got the 7.04 i386 version of the ubuntu server installed and working, but now I want to switch it to the workstation version.

I have a known-good 7.04 workstation install CD, and when I boot with it the first option is 'start or install', as it should be.

But there appears to be no way to say whether I want to start from the live CD, or install. It just silently runs from the live CD.

How can I make it actually install the workstation version? Wiping out the old server installation is no problem.

---

### Post by taurus on 2007-05-19
Just install Gnome window manager and you are all set.  No need to reinstall anything.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by bwise-3rxU on 2007-05-19
Thanks, taurus.

As the server had no X setup, does this do some auto-config of X?

I've been using Debian for years, and Red Hat before that, since RH 4 - I dread spending hours fighting with X configuration!

---

### Post by taurus on 2007-05-19
You can configure X after you have installed Gnome with 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bwise-3rxU on 2007-05-19
Thanks, taurus.

As the server had no X setup, does this do some auto-config of X?

I've been using Debian for years, and Red Hat before that, since RH 4 - I dread spending hours fighting with X configuration!

(this may be a duplicate; I'm still learning this interface)

---

### Post by bwise-3rxU on 2007-05-19
That sort of works, but ultimately the ubuntu-desktop fails to install, because usplash-theme-ubuntu fails, because usplash fails.

The way usplash fails is to give an error like this:

update-initramfs: Generating /boot/initrd.img-2.6.20-150-server
gzip: stdout: no space left on device

I do have a separate /boot partition, as the machine is pretty old. So the above sounds like I should configure a larger /boot partition. How big should it be?

But if I have to repartition (and the only way I know to do this under Ubuntu is re-install), it would simplify everything if I could just install the workstation version to begin with, rather than install the server and then setup ubuntu-desktop. Is there a way to wipe out the server installation and then install the workstation?

---

### Post by taurus on 2007-05-19
Yipe.  You run out of disk space.  You can check it with this command.

```
df -h
```
If you decide to have a separate /boot, give it about 100MB.  And if you want to reinstall the desktop version, you can tell the installer to use the whole harddrive but if you want to partitions yourself, then use gparted from the LiveCD (System -> Administration) and delete all the partitions.  Then, resize them over the way you want it.

How old is your machine anyway because you might not want to run Gnome on it.  Instead, install Xubuntu since it's a lighter window manager than Gnome or KDE.

---

### Post by bwise-3rxU on 2007-05-19
Thanks, taurus. I'm new to Ubuntu, so I appreciate the help.

I found a kubuntu page which answers my original question:
[http://www.linuxloader.com/modules.php?name=Content&pa=showpage&pid=32](http://www.linuxloader.com/modules.php?name=Content&pa=showpage&pid=32)

"Start it live, then double click on the 'install' icon"

Xubuntu may be the way to go, as per your suggestion. The downloads keep getting the MD5 hash wrong, but that's a different question!

Thanks again.

---

### Post by taurus on 2007-05-19
Here's a guide on check sum, [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM).

---

