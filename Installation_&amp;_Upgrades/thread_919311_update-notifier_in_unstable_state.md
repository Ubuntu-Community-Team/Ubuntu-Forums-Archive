---
title: "update-notifier in unstable state"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by bryce4president on 2008-09-13
I was in the middle of upgrading from feisty to gutsy and my laptop over heated (didn't have it on the cooling pad, I know I know... it sucks, but its what I have to work with for now...), so that naturally interrupted the installation.  I ran the dpkg --configure -a, and then ran the  sudo apt-get install -f.   but it keeps failing out saying that update-notifier is in an unstable state and needs to be reinstalled.  But every time I try it errors out...
```

 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is to be removed.
dpkg: error processing update-notifier (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by Pumalite on 2008-09-13
Run:
sudo apt-get update
sudo apt-get dist-upgrade
Post the outputs.

---

### Post by bryce4president on 2008-09-13
```
bryce@laptop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [189B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done

```

```
bryce@laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz: Depends: compiz-fusion-plugins-main (>= 0.5.2+git20070917) but it is not installed
          Depends: compiz-fusion-plugins-extra (>= 0.5.2+git20070917) but it is not installed
          Depends: libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2) but it is not installed
  compiz-gnome: Depends: libwnck22 (>= 2.19.5) but it is not installed
                Depends: libcompizconfig-backend-gconf but it is not installed
E: Unmet dependencies. Try using -f.

```

I then ran the apt-get -f install and this is the output...
```
bryce@laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main libcompizconfig-backend-gconf libcompizconfig0 ubuntu-desktop
  update-notifier update-notifier-common xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
Recommended packages:
  bluez-gnome bogofilter cups-pdf discover1 displayconfig-gtk hal-cups-utils libdeskbar-tracker libpam-gnome-keyring pidgin
  pxljr splix tracker-search-tool ttf-indic-fonts-core ttf-unfonts-core ubufox xdg-utils xresprobe
The following packages will be REMOVED:
  compiz compiz-gnome desktop-effects
The following NEW packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main libcompizconfig-backend-gconf libcompizconfig0
  update-notifier-common xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
The following packages will be upgraded:
  ubuntu-desktop update-notifier
2 upgraded, 8 newly installed, 3 to remove and 730 not upgraded.
3 not fully installed or removed.
Need to get 0B/3028kB of archives.
After unpacking 7336kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: update-notifier: dependency problems, but removing anyway as you request:
 ubuntu-desktop depends on update-notifier.
dpkg: error processing update-notifier (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-09-13
Go to Synaptic and do Complete Removal and then reinstall

---

### Post by bryce4president on 2008-09-14
I tried to do a complete removal but it won't let me.

It gives me a dialog box that says Error Occured.  And then in the text box it says ```
E: update-notifier: Package is in a very bad inconsistent state - you should
```

That is it, the sentence doesn't complete, and I can't remove it.

When I expand the details it says the following...

dpkg: error processing update-notifier (--purge):
  Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.  

Thanks for your help... any suggestions would be appreciated.

I click Close and then the original update box behind it says that Not all changes and updates succeeded.

---

### Post by Pumalite on 2008-09-14
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by bryce4president on 2008-09-14
Very nice.  Thank you very much.  That did the trick.  I was able to remove it and then install it.  Now I'll try to get the rest of this upgrade finished.

---

### Post by bryce4president on 2008-09-14
That did the trick.  I was able to finish the upgrade to Gutsy and all is well :)

---

