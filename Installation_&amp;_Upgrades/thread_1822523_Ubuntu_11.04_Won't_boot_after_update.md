---
title: "Ubuntu 11.04 Won't boot after update"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by bigian on 2011-08-10
Hi - I'm new here so I apologize if I'm in the wrong area.

Yesterday I got installed Ubuntu 11.04. After I got updated with update manager everything was OK until I rebooted the system so that update can tack effect. When I rebooted It's stuck in the middle of something. (No GUI). I tried recovery mode but same thing. Then I tried Previous version and it worked fine. Now I can boot into system but each time I need to select previous version. I googled a lot but didn't find a fix for it. So guys pls help me.

---

### Post by oldfred on 2011-08-10
Welcome to the forums.

Did the update not complete/was only a partial update? Did you manually install video drivers that are incorporated into the old kernel but not the new kernel?

I often suggest these to clean up system from a chroot. If you can get into your system or to a command line you can run these to make sure updates are complete, you can copy & paste each line:

#if not chroot use: sudo -i
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

---

