---
title: "How do i get a gui?"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by jimmyt on 2006-06-12
Hi all.
I've tried searching. I have read a lot of the desktop guide - but the guide doesn't tell me how to get from the terminal to a desktop.

Any help appreciated.

---

### Post by xfile087 on 2006-06-12
[QUOTE=jimmyt]Hi all.
I've tried searching. I have read a lot of the desktop guide - but the guide doesn't tell me how to get from the terminal to a desktop.

Any help appreciated.[/QUOTE]

Gnome should load automatically? If all is setup then from the terminal if you type

> startx

It should load gnome, at least it does for me when i'm messing with my xorg config.

---

### Post by jimmyt on 2006-06-12
oops - just checked and I have installed the server not desktop
sorry

---

### Post by cotcot on 2006-06-12
Alt F7

---

### Post by mayostard on 2006-06-12
[QUOTE=jimmyt]oops - just checked and I have installed the server not desktop
sorry[/QUOTE]

Since you have server and not desktop, you don't have any xserver installed, so startx and alt-f7 aren't going to do anything. 

If you have the ubuntu-desktop CD, pop it in the drive and do a "sudo apt-cdrom add" then "sudo apt-get install ubuntu-desktop".

If you don't have the CD, you can just do the "sudo apt-get install ubuntu-desktop" but it's a lot of packages and will take a long time to pull over the network.

---

