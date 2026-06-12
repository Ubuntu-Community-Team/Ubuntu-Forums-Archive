---
title: "acrobat broke apt-get"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by skunkwerk on 2008-03-10
I had acrobat reader 8 installed manually, but then i wasn't getting the plugin working in firefox so i tried to install from apt-get

it didn't install properly, so i tried fixing the broken packages in synaptic, but that gave me the same effect as running 'sudo apt-get -f install' which is below:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 194 not upgraded.
3 not fully installed or removed.
Need to get 29.5MB of archives.
After unpacking 73.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free acroread 8.1.2-0medibuntu1 [29.5MB]
Fetched 29.5MB in 1m37s (303kB/s)                                              
(Reading database ... 178489 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.2-0medibuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i tried manually removing /usr/bin/acroread but that didn't do anything either

i've tried running apt-get update, clean, and check:
sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  acroread-escript: Depends: acroread but it is not installed
  acroread-plugins: Depends: acroread (= 8.1.2-0medibuntu1) but it is not installed
  mozilla-acroread: Depends: acroread (>= 7.0) but it is not installed
E: Unmet dependencies. Try using -f.

suggestions?
thanks

---

### Post by Bubba64 on 2008-03-11
I think your still trying to get acroread installed if that is so here is the link from Firefox add ons extensions and clicking on plugins on the Mozilla page.
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)
The rest of the plugins listed on this page I have installed as well good stuff for media. if you look in synaptic what you have been trying to install is probably in status. local or obsolete. You probably want to remove these first before you install from Mozilla.

---

### Post by skunkwerk on 2008-03-11
thanks, but how do i fix my apt-get?

---

### Post by taurus on 2008-03-11
Try

```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by rillip on 2008-03-11
worse case scenario, try installing the packages it's asking for individually, then trying the install.

---

### Post by skunkwerk on 2008-03-11
thanks Taurus,
   i already tried that, but i did it again and this is what I got after checking (as the install -f failed):

acroread-escript: Depends: acroread but it is not installed
acroread-plugins: Depends: acroread (= 8.1.2-0medibuntu1) but it is not installed
mozilla-acroread: Depends: acroread (>= 7.0) but it is not installed

rillip, the packages it wants installed seem to be acroread, which i can't install as it fails:
Unpacking acroread (from .../acroread_8.1.2-0medibuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

thanks

---

### Post by skunkwerk on 2008-03-12
problem solved: i had to remove adobereader-enu, and then ran the -f install

---

### Post by andtsoreyu on 2008-04-23
I am having this same problem but cannot seem to get adobereader-enu to remove.  I have tried the following:

[LIST]
[*]sudo apt-get remove adobereader-enu
[*]Removing from Synaptic Package Manager
[/LIST]

Both of these do not work.... what should I do!

---

### Post by spanhead on 2008-06-25
skunkwerk you dancer - that little problem had me going round in circles for a couple hours.  Now, lets see what I can break next!!!!!!!!

---

