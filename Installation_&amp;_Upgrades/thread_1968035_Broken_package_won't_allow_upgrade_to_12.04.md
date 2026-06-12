---
title: "Broken package won't allow upgrade to 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by dspot on 2012-04-28
Would appreciate any help anyone can offer.

I have a broken package that i can't upgrade or completely remove through Synaptic.  And because of that, 12.04 upgrade won't happen and it only allows me to do a partial upgrade.

The package in question is laptop-detect, version 0.13.7ubuntu2.  I'm on a desktop and not sure why i even need it.  The description of error is this:

dpkg: error: parsing file '/var/lib/dpkg/status' near line 2843 package 'makedev':
 field name `Original' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 2843 package 'makedev':
 field name `Original' must be followed by colon

Thanks so much in advance.

---

### Post by josephmills on 2012-04-28
Try this open your terminal and paste this in 
```
sudo apt-get -f install && sudo apt-get update 
```


Let us know if it fixes it thanks

---

### Post by dspot on 2012-04-28
Thanks but already try that and I get the same error.


The following packages were automatically installed and are no longer required:
  python-pygame libevent-2.0-5 libsdl-ttf2.0-0 libmikmod2 libportmidi0
  libsdl-mixer1.2 libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  laptop-detect
The following packages will be upgraded:
  laptop-detect
1 upgraded, 0 newly installed, 0 to remove and 1713 not upgraded.
10 not fully installed or removed.
Need to get 0 B/5,614 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 2843 package 'makedev':
 field name `Original' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by LRBA1 on 2012-05-27
Similar here. After some time using 12.04, I got this error from the update-manager:

dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../../../../../share/pyshared/softwareproperties/gtk/utils.py' must be followed by colon 
Error in function:  

Now I can't update my system or install anything. It's a fresh installation and everything I've install came from the repositories.

joshepmills try didn't solve the problem.

EDIT: I found this => [http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed](http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed)
It solved my problem, hope it helps.
Thank you very much Florian Diesch from askubuntu.com

¿Any idea? Thank you

---

### Post by IPEX-731BA5DD06 on 2012-07-19
Yeah similar problem.

I had Rabbitvcs that wouldn't remove itself??? not actually on system.

Doing the suggested in the link worked.

---

