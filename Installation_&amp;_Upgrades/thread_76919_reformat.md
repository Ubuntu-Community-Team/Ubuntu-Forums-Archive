---
title: "reformat?"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by fractalvibes on 2005-10-15
Trying to upgrade from 5.04 to 5.10 - the install disk insists that I essentially reformat the disk by going through some sort of partition manager.  I just want to upgrade the base OS, not spend a month downloading installing and configuring other software besides losing all data....what gives?  I'll go back to Windows or even DOS before I'll do that!

fv

---

### Post by aysiu on 2005-10-15
If you want to upgrade without reinstalling, you don't use a disk. Just change your *hoary* sources to *breezy* sources ```
sudo gedit /etc/apt/sources.list
``` Every time you see the word *hoary*, replace it with *breezy* and save /etc/apt/sources.list, and then type this in a terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
``` This assumes, of course, that you have an internet connection.

---

### Post by az on 2005-10-15
An easier way is to just insert the cd while you are running ubuntu.  It will ask you if you want to upgrade using it.

Do not boot the cd, since it is an installer.  It will not upgrade your system that way, but install it fresh.

---

### Post by dtfinch on 2005-10-16
[QUOTE=azz]just insert the cd while you are running ubuntu.  It will ask you if you want to upgrade using it.[/QUOTE]
Good thing to know. All my upgrades have involved either apt-get over the internet or blowing it all away and reinstalling from CD.

---

### Post by az on 2005-10-16
[QUOTE=dtfinch]Good thing to know. All my upgrades have involved either apt-get over the internet or blowing it all away and reinstalling from CD.[/QUOTE]

It will not change your sources.list, though.  Just install the packages from the newfound cd repository...

For it to change your repositories, the ability to do so must already be present.  I think this is the case for Breezy, as in Breezy-to-Dapper upgrades will happen like this.

---

### Post by fractalvibes on 2005-10-16
[QUOTE=aysiu]If you want to upgrade without reinstalling, you don't use a disk. Just change your *hoary* sources to *breezy* sources ```
sudo gedit /etc/apt/sources.list
``` Every time you see the word *hoary*, replace it with *breezy* and save /etc/apt/sources.list, and then type this in a terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
``` This assumes, of course, that you have an internet connection.[/QUOTE]

Ok did that.  System is still running (still thinks it is Ubuntu 5.04?)  Synaptic went ballistic when I tried to install updates - several packages are invalid and it wants to remove KDE!  Tiny machine here that found new life via a very minimal install of Hoary Hedgehog and KDE as the desktop.  Apt-get dist-upgrade was a 12 hour process on a cable modem connection and I think the damage has been done???  Luckily the only data of real value is emails.

What are my options?  This little 333 mhz box just breezes right along with Ubuntu and KDE, GNOME chokes it.  

fv

---

