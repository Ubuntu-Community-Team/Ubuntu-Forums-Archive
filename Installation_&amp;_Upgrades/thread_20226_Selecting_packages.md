---
title: "Selecting packages"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by HamRadio on 2005-03-15
Hi there,
I'm going to install Ubuntu on a notebook which is short in disk space: less than 900 MB. Can I select which packages to install?
I have already installed Ubuntu on my home pc but I don't remember any step, neither in 'expert' mode, where I could select packages individually...
Thanks for answering.

---

### Post by arctic on 2005-03-15
i think i remember that it is possible. you will need to do an expert install for this. but with 900 mb, i would suggest buying a bigger harddisk or installing a different distro, like dsl or a stripped down slackware.

---

### Post by az on 2005-03-15
Not expert.  Custom.

Type custom at the prompt.


Afterwards, log in at the boot prompt and do something like:

sudo apt-get install gdm x-window-system-core xterm icewm xfe mozilla-firefox.

That is if you have a slow (less than 300 MHz processor)  If you want the real gnome desktop, do
sudo aptitude

select the package names ubuntu-desktop.  Then go through the files (in green) that are flagged to be installed.  Press minus (-) to unflag them.  You will see how much disk space would be consumed by the packages that will be installed.  Bring that down to about 500 megs (remove a lot of stuff!) Press g to make it go.

There are many many other options.

---

