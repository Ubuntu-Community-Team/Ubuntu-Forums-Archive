---
title: "transmageddon won't uninstall ubuntu 10.4"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by Irishbmx on 2010-11-15
So this all started I made a video in PiTiVi and wanted to upload it to youtube, that didn't go well so I looked around and found out that transmageddon is what I needed to convert the file into one acceptable for youtube and this is were it gets fun.

So the install gets stuck at 58% for like 6+hours so a restart the computer boot back in it says it's not install so I try again to install it and it says blah blah it never finnished installing so I try to sudo apt-get remove transmageddon says I need to sudo dpkg --configure -a so I do then I try again 
Oops@crap:~$ sudo apt-get remove transmageddon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  transmageddon
0 upgraded, 0 newly installed, 1 to remove and 48 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing transmageddon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 transmageddon
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now under ubuntu software center it says it's installed but It won't allow me to uninstall it and I cannot use it or install codecs for it so it's useless.

---

### Post by dino99 on 2010-11-15
you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

then do what you need with synaptic (system admin synaptic)

[http://blogs.gnome.org/uraeus/2009/04/28/transmageddon-and-arista/](http://blogs.gnome.org/uraeus/2009/04/28/transmageddon-and-arista/)

---

### Post by Irishbmx on 2010-11-15
> **dino99 said:**
> you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

then do what you need with synaptic (system admin synaptic)

[http://blogs.gnome.org/uraeus/2009/04/28/transmageddon-and-arista/](http://blogs.gnome.org/uraeus/2009/04/28/transmageddon-and-arista/)
Ty got it removed now, perfect timing on post I had just rebooted :)

---

