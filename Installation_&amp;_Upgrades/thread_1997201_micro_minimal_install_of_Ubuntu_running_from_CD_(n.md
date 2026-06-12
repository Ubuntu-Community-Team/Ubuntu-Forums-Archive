---
title: "micro minimal install of Ubuntu running from CD (not Live CD)"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by The Rogue on 2012-06-04
The goal:  an installation of Ubuntu, inadyn and OpenVPN which will boot, log in, and run on a headless box from CD/DVD, updating the IP address via DnyDNS and allowing an encrypted VPN connection.

Ubuntu, inadyn and OpenBPN because I an at least somewhat familiar with them, I am open to other suggestions.

So basically the question is, starting from a normal install to configure the apps, what can I then safely remove to bring it down to a machine which only has those five tasks: boot from CD/DVD . log in. update via DynNS.  Run OpenVPN.  Don't need a desktop, don't need further configuration, don't need to update any of the installs:  power up and walk away and be able to remotely connect.

---

### Post by Bucky Ball on 2012-06-04
Why not go the other way??? Just do a minimal install and only install the packages you want. If you want to cut the fluff away from a regular install you would be there for ages (you might get rid of apps but that is only the beginning) and would be a waste of time.

You can find the minimal install ISO and some instructions here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The minimal installs the things you need to get the machine running. You then give a list of what you want to install as far as apps goes (this can take some planning) and the apps are then downloaded/installed via the internet. 

You end up with the sleekest, fastest Ubuntu install you've ever had. This depends, of course, on what you decide to install. If you are looking for the ubuntu-desktop and all bells and whistles, don't bother with this method.

I always use Xfce as desktop environment (faster than Gnome), but you might have other preferences, . Just add 'xfce4' to the list of things you want to install if you want to use it. You could also include:

synaptics
gcc

Sit with a beverage of your choice, a piece of paper and pen, and plan what you are going to install so when you get there you know what you are doing. Good luck.

;)

---

