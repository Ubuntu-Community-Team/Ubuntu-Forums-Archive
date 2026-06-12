---
title: "Install Linux Mint KDE over Ubuntu and losing as little data as possible?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by deusdies on 2011-02-27
Luckily I have /home and / partitions separated.

So is it enough simply not to reformat /home ? Will I encounter any issues being as that I used GNOME and now KDE?

At first I thought I should use synaptic to save all the applications installed and then restore them with the new installation, but that sounds like a terrible idea because of all the GTK apps in Ubuntu.

Most of my stuff is on my external drive anyway. I installed Kubuntu-desktop package in Ubuntu to use KDE, but it's all messed up, feels like a clean install would save me a lot of trouble.

---

### Post by jeremyjjbrown on 2011-02-27
If you manual specify the installation partitions and leave home alone you will not loose your data. You do need to delete the hidden folders in /home that hold config data for your installed programs or you will likely have problems.  sudo nautilus will give you a window with permission to edit the hidden files.

Make sure you backup your data anyway.

---

