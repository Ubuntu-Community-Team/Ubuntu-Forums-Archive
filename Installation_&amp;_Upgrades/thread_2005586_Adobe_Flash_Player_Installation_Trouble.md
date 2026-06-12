---
title: "Adobe Flash Player Installation Trouble"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by vasko21 on 2012-06-17
Hi All,

Hope this is the right place to post this thread. I just had my laptop switched from Windows to Ubuntu and I am trying to install Adobe Flash Player and I am running into problems. I have typed in terminal 

sudo apt-get install flashplugin-installer and got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.32-38 dkms patch linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/20.8kB of archives.
After this operation, 119kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 20240 package 'python-central':
 junk after word in `priority' field
E: Sub-process /usr/bin/dpkg returned an error code (2)

Does anybody have any suggestion how to fix this problem? Any help is appreciated. Btw, I am running Ubuntu 10.04 and use Latitude D510. 

Thanks again.

Vasko

---

### Post by Curtis6767 on 2012-06-17
If you are using Firefox, then go over to Firefox plugins and download Flash Aid.

If you are using Chrome, then flash support is built in so if you are having the problem in Chrome, then it's something else.

Hope this helps.

---

### Post by vasko21 on 2012-06-20
Thanks for the reply!  Unfortunately, that doesn't fix it either. It turns out that when I do updates or install new programs (kile & octave) the installation can't be completed and it shows me the same error. Any other advices???

---

### Post by Frankebasta on 2012-07-01
I received the same error message when using dpkg, after I uninstalled clam-av.

To fix that, it needs to edit the file /var/lib/dpkg/statoverride and purge all line relating with clam.

Hope it helps...

---

