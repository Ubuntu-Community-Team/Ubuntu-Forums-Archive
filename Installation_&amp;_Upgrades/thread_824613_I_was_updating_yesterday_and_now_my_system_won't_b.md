---
title: "I was updating yesterday and now my system won't boot."
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by whatever69 on 2008-06-10
kernel panic not syncing vfs unable to mount root fs on unknown wn-block(0,0)

That's error message I get.

I eventually went into grub and was able to make it into initramfs, but what do I do from there?  The system was running fine.  It was just freezing when I updating (yelp) to be precise, so I rebooted and them blam.  The kernel panic appeared.

Any help would be appreciated.

---

### Post by dstew on 2008-06-10
Do you get the grub menu? If so, try booting an older kernel if you have one.

---

### Post by whatever69 on 2008-06-10
Yes, I can get into the grub menu.  As soon as I finish work, I'll go home and try. I have 3 kernels.  The default one with 8.04 and then next 2 that they upgraded.

---

### Post by whatever69 on 2008-06-10
Hi,

I was able to go into grub, and boot into my last working kernel.

I tried the upgrade again and it froze my PC.  It was complaining about:

Yelp
Xulrunner 1.9
Firefox 

I tried:

dpkg --configure -a

nothing...

apt-get -f install

froze my computer


I think yelp is the problem here :S  Not sure what to do about it.

---

### Post by Pumalite on 2008-06-10
What about:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by whatever69 on 2008-06-10
dpkg --configure -a [result = fail]
apt-get update [result = good]
apt-get dist-upgrade [result = complains]
apt-get -f install [result = YAY!]

I then ran the update manager in gnome and everything upgraded just fine.  I was able to reboot after that and all the errors are gone.

Thanks for leading me down the right path everyone!  Very much appreciated.

I'm including what the output of the commands yielded in case anybody else wants to examine them.


root@ubuntuserver:/home/roy# dpkg --configure -a
dpkg: error processing yelp (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9~rc1+nobinonly-0ubuntu1~8.04.2); however:
  Version of xulrunner-1.9 on system is 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9~rc); however:
  Version of xulrunner-1.9 on system is 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0~rc1+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 yelp
 xulrunner-1.9-gnome-support
 firefox-3.0
 firefox-3.0-gnome-support
root@ubuntuserver:/home/roy# 



root@ubuntuserver:/home/roy# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9~rc) but 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 is installed
  xulrunner-1.9-gnome-support: Depends: xulrunner-1.9 (= 1.9~rc1+nobinonly-0ubuntu1~8.04.2) but 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 is installed
E: Unmet dependencies. Try using -f.
root@ubuntuserver:/home/roy# 


root@ubuntuserver:/home/roy# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xulrunner-1.9 yelp
The following packages will be upgraded:
  xulrunner-1.9 yelp
2 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
4 not fully installed or removed.
Need to get 0B/8087kB of archives.
After this operation, 168kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 120602 files and directories currently installed.)
Preparing to replace yelp 2.22.1-0ubuntu2 (using .../yelp_2.22.1-0ubuntu2.8.04.1_i386.deb) ...
Unpacking replacement yelp ...
Preparing to replace xulrunner-1.9 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 (using .../xulrunner-1.9_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb) ...
Unpacking replacement xulrunner-1.9 ...
Setting up xulrunner-1.9 (1.9~rc1+nobinonly-0ubuntu1~8.04.2) ...

Setting up yelp (2.22.1-0ubuntu2.8.04.1) ...

Setting up firefox-3.0 (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...
Installing new version of config file /etc/firefox-3.0/pref/firefox.js ...
Please restart all running instances of Firefox-3.0, or you will experience problems.

Setting up xulrunner-1.9-gnome-support (1.9~rc1+nobinonly-0ubuntu1~8.04.2) ...

Setting up firefox-3.0-gnome-support (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...

root@ubuntuserver:/home/roy#

---

