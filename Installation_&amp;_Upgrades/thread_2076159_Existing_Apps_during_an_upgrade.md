---
title: "Existing Apps during an upgrade?"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2012-10-25
When you run an upgrade (say, 12.04 to 12.10) does it remove or touch your installed applications?  I know it disconnects the PPAs but does it take something installed from the repositories and upgrades them?

Or does it just overwrite everything in the root partition/portion with the new versions' and you have to re-install everything all over again?

Background:
I have a 12.04 installation on my laptop which requires a non-PAE kernel.  If I run an update from 12.04 to 12.10 will it overwrite everything with the 12.10 version including the kernel or is this a means I can get 12.10 on my laptop continuing with my currently working kernel?

---

### Post by dino99 on 2012-10-25
non pae kernel is a no go with 12.10, be aware  :mad:

either stay with 12.04 (not so huge diff with QQ, and maintained till 2017)
or dist-upgrade manually, avoiding the stock QQ kernel, meaning:
- open a cli (terminal)
- edit the sources.list, comment out all the non genuine repo, and change PP by QQ
- update
- and now install (with apt-get) the packages (more than 1500) starting with the tools (dpkg, apt, base-files, udev, ...), then the languages (gcc, cpp, python, ruby, ...) , and then the others (except kernels)
- then set kernel pinpoint into synaptic ( to not accept future kernels upgrades)
- voila, so might be better to stay with PP

and no, your data/settings inside your /home are not changed/tweaked while upgrading.

---

### Post by oldfred on 2012-10-25
I thought you should remove/disconnect any extra PPAs you have added before an upgrade to avoid issues.

Make backups first, so you know what you have:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key

It will upgrade to the newest version of all the software from repositories, if still available. I had upgraded for many versions and some stuff was so old that it was discontinued.   I now only do clean installs.

If doing a clean install you can export a list of installed applications. But some default do change so you may want to review.

I run the dpkg list as part of every rsync backup.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages


If system is so old as to not run with PAE, I thought full Ubuntu was too much system and Lubuntu or Xbuntu were better choices. 

My dual core systems are 6 years old, so your system must be very old?? And systems that old usually do not have lots of RAM memory.

---

### Post by Dragonbite on 2012-10-25
> **oldfred said:**
> If system is so old as to not run with PAE, I thought full Ubuntu was too much system and Lubuntu or Xbuntu were better choices. 

My dual core systems are 6 years old, so your system must be very old?? And systems that old usually do not have lots of RAM memory.

That's the funny thing, it doesn't seem too old but when I try 12.10 in a live session it fails due to "incompatible kernel".

I'm not sure how old it is, but it is an IBM (not Lenovo) Thinkpad T42 with an Intel Pentium M chip (at 1.8 GHz) and with 2 GB of Ram (the max).  Ubuntu 12.04 does stretch it a little mostly with the Dash and such but it does run Windows 7 at a reasonable (usable) speed as well as Fedora Gnome-shell and openSUSE KDE.

Xubuntu ran fairly nicely on it too and that one came with the non-PAE kernel but it looks like they too are going with the PAE kernel by default.

---

