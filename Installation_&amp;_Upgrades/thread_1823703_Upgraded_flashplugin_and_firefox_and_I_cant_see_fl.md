---
title: "Upgraded flashplugin and firefox and I cant see flash anymore"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by wbuntu on 2011-08-12
$ dpkg -l | egrep "flash|firefox"
ii  firefox                               5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla
ii  firefox-branding                      5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla - transitional package
ii  firefox-gnome-support                 5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla - GNOME support
iU  flashplugin-installer                 10.3.183.4ubuntu0.11.04.1                  Adobe Flash Player plugin installer
iU  flashplugin-nonfree                   10.3.183.4ubuntu0.11.04.1                  Adobe Flash Player plugin installer (transitional package)

---

### Post by wbuntu on 2011-08-14
help please

---

### Post by haqking on 2011-08-14
use flash aid

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

it will resolve conflicts and choose appropriate version for your system and keep updated

---

### Post by Actonix on 2011-08-14
> **wbuntu said:**
> $ dpkg -l | egrep "flash|firefox"
ii  firefox                               5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla
ii  firefox-branding                      5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla - transitional package
ii  firefox-gnome-support                 5.0+build1+nobinonly-0ubuntu0.11.04.2      Safe and easy web browser from Mozilla - GNOME support
iU  flashplugin-installer                 10.3.183.4ubuntu0.11.04.1                  Adobe Flash Player plugin installer
iU  flashplugin-nonfree                   10.3.183.4ubuntu0.11.04.1                  Adobe Flash Player plugin installer (transitional package)

If all Firefox related processes did not get completely knocked off by the install then you would need to ensure they did to be able to use flash, this would include Downloads and even the Preference editor

I have had problems with the Flash d/l from one of the sources, I think Natty-partner was the one that got me sorted out.

If your reason for Downloading both Firefox and Flash stem from problems due to prior usage then you might want to look at using something like Bleach

---

### Post by dino99 on 2011-08-14
open synaptic: sudo synaptic
search for: flashplugin
remove/purge the installed flash* package(s)

add this ppa (config -> repo -> 3d parties): ppa:brandonsnider/experimental-flash
(from [https://launchpad.net/~brandonsnider/+archive/experimental-flash](https://launchpad.net/~brandonsnider/+archive/experimental-flash))
update
install flashplugin-installer

---

