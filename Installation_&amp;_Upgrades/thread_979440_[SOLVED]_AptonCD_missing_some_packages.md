---
title: "[SOLVED] AptonCD missing some packages"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-11-11
I was going to use AptonCD , to transfer Ubuntu to another computer, however when I tried the 'create', I noticed kmymoney was missing from the package list, and I'm sure there are other packages that I have installed, that were not shown.

Any definitive method to ensure that everything gets put on the CD ?

---

### Post by oygle on 2008-11-13
APTonCD only showed 118 packages, whereas when I go into Synaptic Package Manager, it shows 1299 packages installed.

Any clues about why APTonCD would be missing packages please ?

---

### Post by cypherbios on 2008-11-13
Hi there,

APTonCD only lists packages that were installed using APT (such as apt-get, aptitude, synaptic, update-manager, adept). If you installed any packages using gdebi or dpkg -i, those packages will not show up in the APTonCD's list.

To sum up, aptoncd lists every package in /var/cache/apt/archives/, can you check if your missing packages are there?
If it is not and you are sure your package were installed using APT, then you cache was cleaned.

But, if you want to ensure that every package you have installed via APT is going to be in the aptoncd disc, even though they were removed from the cache (apt-get clean), you can use the following command to redownload to your cache all the installed packages:

$ dpkg --get-selections | grep install | cut -f1 > packages.dpkg
$ sudo apt-get install --reinstall --download-only `cat packages.dpkg`

But if you are greed ;) and want to have it all, including the packages that were installed using dpkg and is not available through APT, you always can rebuild the .debs from the files you have in your system:

$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

[*] [https://answers.launchpad.net/aptoncd/+question/15592](https://answers.launchpad.net/aptoncd/+question/15592)

I hope that helps.
Regards.

---

### Post by oygle on 2008-11-14
> **cypherbios said:**
> 
APTonCD only lists packages that were installed using APT (such as apt-get, aptitude, synaptic, update-manager, adept). If you installed any packages using gdebi or dpkg -i, those packages will not show up in the APTonCD's list.


Okay, everything has been installed via those methods (above) that you have described, except for these:

BCompareLinux-3.0.9.9222_i386.deb
iscan_2.3.0-2_i386.deb
iscan-plugin-gt-s600_2.0.0-2_i386.deb
setserial_2.17-44_i386.deb

> **cypherbios said:**
> 
To sum up, aptoncd lists every package in /var/cache/apt/archives/, can you check if your missing packages are there?

KMyMoney' definitely not there, and possibly others not there also.

> **cypherbios said:**
> 
If it is not and you are sure your package were installed using APT, then you cache was cleaned.

That is not something I would do, simply because I don't know how. That said, I was trying to do some list of all the packages some weeks back, I'd have to hunt around for the command though ??

> **cypherbios said:**
> 
But, if you want to ensure that every package you have installed via APT is going to be in the aptoncd disc, even though they were removed from the cache (apt-get clean), you can use the following command to redownload to your cache all the installed packages:

$ dpkg --get-selections | grep install | cut -f1 > packages.dpkg
$ sudo apt-get install --reinstall --download-only `cat packages.dpkg`


Here is the output from that:

> $ dpkg --get-selections | grep install | cut -f1 > packages.dpkg
$ sudo apt-get install --reinstall --download-only `cat packages.dpkg`

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of bcompare is not possible, it cannot be downloaded.
Reinstallation of iscan is not possible, it cannot be downloaded.
Reinstallation of iscan-plugin-gt-s600 is not possible, it cannot be downloaded.
The following extra packages will be installed:
  libcompfaceg1 linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic
Suggested packages:
  claws-mail-doc claws-mail-tools psutils linux-doc-2.6.24 linux-source-2.6.24 avm-fritz-firmware-2.6.24-21 nvidia-glx
  nvidia-glx-legacy nvidia-glx-new openbsd-inetd inet-superserver smbldap-tools
Recommended packages:
  amaya-doc claws-mail-i18n
The following NEW packages will be installed:
  amaya claws-mail libcompfaceg1 libetpan11 linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic
The following packages will be upgraded:
  alacarte base-files dbus dbus-x11 foo2zjs libdbus-1-3 libsmbclient linux-generic linux-image-generic
  linux-restricted-modules-generic module-init-tools samba samba-common smbclient smbfs update-notifier
  update-notifier-common winbind
18 upgraded, 7 newly installed, 1276 reinstalled, 0 to remove and 0 not upgraded.
Need to get 855MB/984MB of archives.
After this operation, 140MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.


I had to say 'no' , as I'm on dialup, it wanted to download a bit less than 1 Gb (yikes).

> **cypherbios said:**
> 
But if you are greed ;) and want to have it all, including the packages that were installed using dpkg and is not available through APT, you always can rebuild the .debs from the files you have in your system:

$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

[*] [https://answers.launchpad.net/aptoncd/+question/15592](https://answers.launchpad.net/aptoncd/+question/15592)


Okay thanks. I don't think I'll worry about those few .DEB files, it seems I didn't even install 'setserial' at all.

If I open the file 'packages.dpkg' , there are 1301 lines in it, which is the exact number of packages shown in Synaptic Package manger. Also, KMyMoney2 is showing in that file.

Although claws-mail is showing, but I just removed that today via the 'add/remove' function ?


Now, it would be good if I could 'trick' APTonCD' into looking at the file 'packages.dpkg' , instead of having to d/load them. :D

Thanks a lot for your help.  :)

---

### Post by oygle on 2008-11-16
I'll consider this solved, as my /var/cache/apt/archives path was apparently not up to date, which caused APTonCD to only list the packages/apps that were in that path. It is a matter of me following those 2 commands supplied by the author of APTonCD, to bring it up to date.

---

