---
title: "Installing 10.04 Beta2 went OK except for these 8 files"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2010-04-25
I did an install from the CD, rebooted from the Hard Drive (GRUB menu sees my new and old versions of Ubuntu as well as WinXP) but right after install Update Manager wanted to download 300Megs of files. Of course.

Some,, it failed on, and again on subsequent reties.

I'll wait a bit, and try again, perhaps tomorrow.

It doesn't seem to be catastrophic (yet) so I'm going ahead and take 10.x out for a spin and see how it behaves.

What follows is the apt-get dialog for anyone's curiosity.

berk


gedit-common 
gtk2-engines-pixbuf 
libgail-common 
libgail18 
libgtk2.0-0
libgtk2.0-bin 
pm-utils 
xserver-xorg-core


> xxx@xxx-desktop:~$ sudo apt-get upgrade
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gedit-common gtk2-engines-pixbuf libgail-common libgail18 libgtk2.0-0
  libgtk2.0-bin pm-utils xserver-xorg-core
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,053kB/7,663kB of archives.
After this operation, 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main gedit-common 2.30.0git20100413-0ubuntu1
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main gtk2-engines-pixbuf 2.20.0-0ubuntu4
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main pm-utils 1.3.0-1ubuntu1
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xserver-xorg-core 2:1.7.6-2ubuntu7
  Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.30.0git20100413-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.30.0git20100413-0ubuntu1_all.deb)  Connection failed [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.20.0-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.20.0-0ubuntu4_i386.deb)  Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb)  Connection failed [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7_i386.deb)  Connection failed [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

end

---

