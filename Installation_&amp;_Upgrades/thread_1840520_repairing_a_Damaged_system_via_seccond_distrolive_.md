---
title: "repairing a Damaged system via seccond distro/live disc"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by Fenderian_Mayhew on 2011-09-07
recently I updated to ubuntu 11.04. i will save my judgements ,however i decided to install an alternate desktop system. I installed gnome3, found it to be cumbersome, and uninstalled it. upon reboot I was unable to log in because unity and gnome classic had both been damaged beyond use. 

Lucky I had installed ubuntu 10.10 on a extra partition so i decided to use that partition like a live disc

**replace "drive-number-or-name" with the name or number of the drive to be fixed you can use ctrl-L to show the location in nautilus**

once logged in I set-up a chroot to the root of my damaged system (directions are in the appropriate order, I did things different because I didn't know what was needed.)

```
mount -t proc proc /proc
mount -t devtmpfs none /dev
chroot /media/drive-number-or-name/ 
```and transferred network connectivity to it 
```
cp /etc/resolv.conf /media/drive-number-or-name/etc/resolv.conf
```I than did my updates, 

```
sudo apt-get remove libgtk-3-common 
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get install gnome-panel
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install ubuntu-desktop
```closed my chroot terminal 
and unmounted the previous mounts
```
umount /proc
umount /dev
```the process took roughly 2 hours because i had to dig through the web for info so i hope my post will save some people a few hours.

peace and good computing to all 

Fen Mayhew

---

