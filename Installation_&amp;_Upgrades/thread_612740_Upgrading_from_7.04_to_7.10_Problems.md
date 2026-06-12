---
title: "Upgrading from 7.04 to 7.10 Problems"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by banjopikker on 2007-11-14
I tried the upgrade  to 7.10. Here is the error messages .
your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.
I need instructions on how to do this .. Thanks

---

### Post by bulldog on 2007-11-14
> **banjopikker said:**
> I tried the upgrade  to 7.10. Here is the error messages .
your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.
I need instructions on how to do this .. Thanks
Pick the one you want```
sudo aptitude install ubuntu-desktop
```
This will install the standard gnome desktop,but if you prefer another one,be my guest :)

---

### Post by banjopikker on 2007-11-16
I tried the:  sudo aptitude install ubuntu-desktop. It  Wouldn't install. I looked in Synaptic. There is desktop environment. I don't really know what I am looking at though.   I tried again today. got this:: [  Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.3_i386.deb]](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.3_i386.deb])
  404 Not Found:: And this.::[Can't guess meta-package]

[Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding. And this box::[A unresolvable problem occurred while calculating the upgrade].

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport].

---

