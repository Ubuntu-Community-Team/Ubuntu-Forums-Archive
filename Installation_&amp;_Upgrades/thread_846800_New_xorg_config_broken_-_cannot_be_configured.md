---
title: "New xorg config broken - cannot be configured"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by fudoki on 2008-07-01
After "upgrading" to Hardy, and losing the ability to control my display and get a usable video mode; i.e. higher than 800x600, and reading the happy talk at [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) one must wonder why anyone thought it a good idea to turn Ubuntu into "you WILL do it OUR way" Windows??

After happily running at 1024x768 for YEARS, I am now faced with an "OS" that is going to cram a low, unusable, resolution down my throat - regardless of how I want MY computer to function.

Anybody want to explain how this is "progress"?

It's EXACTLY LIKE DEALING WITH WINBLOWS, WITH VALID CHOICES BEING IGNORED AND SELECTIONS BEING RE-WRITTEN AND OVER-WRITTEN.

Is there any way to override the override, short of installing a different Linux distro?

If this is the future of Ubuntu, then this is where my clients and I must part ways with Ubuntu.  The main advantage of Linux is the respect of USER CHOICE.

What has happened to these most basic USER CHOICES in Ubuntu?

Who thinks making Ubuntu shove settings, WRONG SETTINGS, down user's throats is good for anyone?

---

### Post by Pumalite on 2008-07-01
Install the appropriate driver for your card and you'll get a choice of resolutions.

---

### Post by sdennie on 2008-07-01
You didn't specify what graphics card you are using but, you might be able to fix your problem by reboot and choosing a recovery mode kernel.  When the menu comes up, choose xfix.

---

### Post by Partyboi2 on 2008-07-01
Did you try from a terminal ```
sudo displayconfig-gtk
``` and changing the resolution from there?

---

### Post by Pumalite on 2008-07-01
xfix gives you a basic xserver. The command in Hardy is:
sudo displayconfig-gtk

---

### Post by LaRoza on 2008-07-01
Try again ;)

Post the problems and technical details and what happened without the part trying to make people defensive. That is not the way to get help on this forum.

Upgrading is always a risk, for anything.

---

