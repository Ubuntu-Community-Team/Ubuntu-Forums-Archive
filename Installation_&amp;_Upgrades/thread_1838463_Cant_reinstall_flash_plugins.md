---
title: "Cant reinstall flash plugins"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by snazzycazzy on 2011-09-03
Hi Everyone

I recently couldnt play any videos so i tried to uninstall/reinstall flashplugin10 on software centre. It uninstalled OK but I cant reinstall it. Ive tried 

sudo apt-get -f install 

but it comes up with

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libpostproc51 libboost-thread1.42.0 libavformat52
  libboost-date-time1.42.0 gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
  liboil0.3 libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 215 not upgraded.
1 not fully installed or removed.
Need to get 0 B/10.9 kB of archives.
After this operation, 69.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help! Also, Im pretty technophobic so please make things as easy as possible (copy and paste)

Thanks :)

---

### Post by Frogs Hair on 2011-09-03
Hi and Welcome

If you are using Firefox , check out this add on , which makes installing and updating flash easy . [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

