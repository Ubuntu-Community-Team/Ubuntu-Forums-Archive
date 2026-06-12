---
title: "Install 6.10 from Text to Full Graphical [Resolved]"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-02-22
I have a multiboot linux system with Solaris and FreeBSD. The Ubunti installer does not like my solaris or FreeBSD partitions. Durung install I choose custom partitions and try and assign hda11 as / and hda12 as /home,  /swap is partition 6 (shared amongst systems).

Gparted reports no root partition on setup ( I am assuming its the non linux OS that create the problems). If changing the file system types does not let me get around this install :(

The only way I can install Ubuntu is by choosing text mode, so I choose to install a command line system only. This worked, the text partitioner allowed me to select partitions and I have a working
command prompt system.
To upgrade to full graphical with gnome I did the following
apt-get upgrade
apt-get install xorg
apt-get install synaptic
apt-get install gnome

However all is not quite well as parts of the gnome 2.16.1 desktop dont work, a right click on the desktop does not bring up a context menu, and the desktop loading sequence starts with a terminal, then the gnome menues appear about 5 minutes later.

Previously I used to uninstall Solaris and FreeBSD, then Ubuntu would install.
Is there may be an easy way to get gnome working, or does anyone know how to install Ubuntu when a Solaris type "bf" partition and FreeBSD type "A5" file systems are present. ?
I only have one 160G hard disk.
Thanks in advance (sorry for long post)

---

### Post by aysiu on 2007-02-23
Instead of installing *gnome*, can you try this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by hal8000 on 2007-02-24
Hi Aysiu,

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

Works perfectly, took only about 25 minutes to complete, thank you very much!

I should mention that the start of my problem was when I tried to install 'upstart' to Ubuntu. I did not back up my init scripts, so rather stupidly ended up reinstalling.
:guitar:  :)

---

