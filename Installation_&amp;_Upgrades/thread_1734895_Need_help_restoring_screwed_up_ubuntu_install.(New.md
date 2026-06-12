---
title: "Need help restoring screwed up ubuntu install.(Newbie)"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by viktor- on 2011-04-20
Hi.

I've been using ubuntu for a couple of weeks now and have finally got most stuff to work and have been really happy with the OS.

Today I screwed it all up though. I tried out KDE, but I didnt like it and wanted to uninstall it, since it flooded my gnome menus with a lot of applications I didnt use. So to get rid of it all, I used synaptic package manager, search for KDE, marked a whole bunch of packages for removal and clicked apply. Unfortunatly I uninstalled a whole lot more than I intended.

I can still log into ubuntu, but only using the prompt. When I type startx something loads and I'll get into another looking style prompt. No GUI whatsoever. I've tried sudo apt-get update/upgrade as well as dkpg repair broken packages from the recovery menu but it installs nothing.

My question is if there's an easy way to get my old install to work?

---

### Post by oldfred on 2011-04-21
If you can get to command line you will not have to chroot. Just reinstall the desktop. # are comments do not enter.

#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by viktor- on 2011-04-21
Thanks. That did the trick. 

I also found the log file of aptitude in /var/log/dpkg.log so I can look through which packages I need to reinstall.

---

### Post by oldfred on 2011-04-21
I added the K desktop one time and had some of the same issues. I will not do that again, but will do another install in a 20GB test partition next time. That avoids the issues. I actually like several k apps including k3b & kmymoney so I did not want to uninstall all of the k desktop.

Glad you got it working.

You can make a list of all installed apps. I do this as part of my rsync backup so I always have a saved list of installed apps.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

