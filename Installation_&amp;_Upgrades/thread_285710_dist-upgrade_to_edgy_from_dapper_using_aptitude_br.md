---
title: "dist-upgrade to edgy from dapper using aptitude: broken python packages"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by 5-HT on 2006-10-27
I'm getting some broken python packages when simulating a dist-upgrade from Dapper to Edgy using Aptitude and was wondering if anyone has experienced this or know if I should be concerned about removing them as Aptitude is suggesting?

Looks like the issues relating to upstart (including ubuntu-minimal, system services, and startup-tasks) should be resolved with a second dist-upgrade, but I'm not really sure what may be happening with those python packages. Anyone have any ideas? Thanks for any input!

[quote= pertinent bits from aptitude -s dist-upgrade]The following packages have unmet dependencies:
  python-gnome2: Conflicts: python2.4-gnome2 but 2.12.4-0ubuntu1 is installed.
  python-numeric: Conflicts: python2.4-numeric but 24.2-1ubuntu2 is installed.
  python-pyorbit: Conflicts: python2.4-pyorbit but 2.14.1-0ubuntu1 is installed.
  upstart: Conflicts: sysvinit but 2.86.ds1-14.1ubuntu16 is to be installed.
  python-gtk2: Conflicts: python2.4-gtk2 but 2.8.6-0ubuntu1 is installed.
  python-cairo: Conflicts: python2.4-cairo but 1.0.2-1ubuntu1 is installed.
  python-gobject: Conflicts: python2.4-gobject but 2.10.1-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
python2.4-cairo
python2.4-gnome2
python2.4-gobject
python2.4-gtk2
python2.4-numeric

Keep the following packages at their current version:
python-pyorbit [2.14.1-0ubuntu1 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed][/quote]

---

### Post by 5-HT on 2006-10-27
After searching packages.ubuntu.com, looks like this might be resulting from a naming change in the python packages and the ones Aptitude wants to remove don't appear to be in the Edgy repos at all.

Can anyone confirm this at all? Or am I way off? Thanks.

---

### Post by ivomans on 2006-10-27
After my upgrade from Dapper to Edgy last night I had a similar range of  remaining upgrade conflicts with a series of python packages. Now the command [FONT=Fixedsys]**aptitude dist-upgrade**[/FONT] solved the issue for me.
Now my installation is fully updated.

---

### Post by jabudia on 2006-10-29
exactly the same happens to, just that I'm unable to fixit. No matter what I do, I always endup by having something like this:

# apt-get dist-upgrade
...
Errors were encountered while processing:
 python-cairo
 python-gtk2
 python-numeric
 python-apt
 update-manager
 python2.4-minimal
 language-selector
 gnome-app-install
 python-gtkhtml2
 python-vte
 python-glade2
 unattended-upgrades

or, for example, either of those packages goes like:

# dpkg --configure python-cairo
Setting up python-cairo (1.2.0-1build1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/cairo/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/cairo/__init__.py
dpkg: error processing python-cairo (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-cairo

... and no clues at the momento how to fix it :-((

---

### Post by khedron on 2006-10-29
I used aptitude as well, and I think I uninstalled a lot of python packages. They aren't necessary system files; you can always install them later if you are worried. I just ran aptitude dist-upgrade repeatedly, fixing each problem as it came up by uninstalling the problem package or accepting aptitude's solutions.

It's a dist-upgrade, after all - some packages are supposed to be uninstalled.

Obviously, don't uninstall necessary packages, but I think you'll be fine uninstalling Python.

---

### Post by ivomans on 2006-10-29
> **jabudia said:**
> exactly the same happens to, just that I'm unable to fixit. 
... and no clues at the momento how to fix it :-((

Could you try **sudo aptitude dist-upgrade**, this command usually gives at least a bit more explanation why the upgrade is not working.

---

