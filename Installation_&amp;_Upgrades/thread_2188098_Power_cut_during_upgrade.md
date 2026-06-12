---
title: "Power cut during upgrade"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by pauldsmith22 on 2013-11-15
My computer was downloading and installing packages from the latest upgrade when the computer suffered a loss of power. Now, when the computer boots, Ubuntu reports that it is the latest version, but once it displays my wallpaper it doesn't continue to display the remainder of the desktop. My computer was originally a Windows 7 machine and I opted to dual boot when I installed Ubuntu. How do I recover from this problem?

---

### Post by oldfred on 2013-11-15
Can you get to terminal. 
I normally post these as part of a chroot where sudo is not required. # is comment do not copy comments.

 #Commands once in chroot:
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
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

Post back any error messages.

---

