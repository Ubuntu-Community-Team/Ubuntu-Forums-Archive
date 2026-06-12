---
title: "update-app-install - broken"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by rotten on 2006-11-29
So today I decided to upgrade from Dapper to Edgy.   Unfortunately after upgrading I am unable to startx.  I get a missing 'fixed' font error.

I tried reinstalling the fonts, but I get an error.

After some research, I've observed that the update-app-install python script is unable to find several modules (xdb.DesktopEntry, gdbm, and AppInstall.CoreMenu).

I _think_ this broken python script is in turn breaking some post install configuration for the fonts package.

I've tried doing an:
apt-get --reinstall install gnome-app-install

Unfortunately that package install is dependent on itself.  If it is broken it can't reinstall itself.

I've tried reinstalling python, to no avail.

I should probably fix the install routines, but I'd be willing to just fix X instead and worry about the install routines some other day.  I'm open to suggestions for things to try. 

Thanks.

---

### Post by rotten on 2006-11-29
reinstalling the xserver-xorg package seemed to help.  I got past the broken 'fixed' font error.

I'm still getting the broke update-app-install, but that is less worrisome now that I have a desktop back.

---

