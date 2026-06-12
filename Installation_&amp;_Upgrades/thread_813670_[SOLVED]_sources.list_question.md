---
title: "[SOLVED] sources.list question?"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2008-05-31
Hi all,

After Upgrade from Ubuntu 7.10-amd64 to Ubuntu 8.04-amd64 I got these
entries in my sources.list

> # Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

I.m not sure if this makes sense but I want to uncomment them, 
because I think it is necessary to have the security sources. 

What do I have to do whith that?

---

### Post by aysiu on 2008-05-31
It sounds as if the last time you tried to update, Ubuntu wasn't able to connect to those servers. Certainly uncomment them and see if the servers are now available.

---

### Post by Kevbert on 2008-05-31
When you've upgraded you probably did this via CD with an inactive web connection.  You can either uncomment these lines or go to your Software Sources and select these there.  By the look of it you need to as you'll only get security updates by uncommenting these lines.

---

### Post by Cariboo1938 on 2008-06-07
Many thanks, aysiu, kevbert...
I followed aysiu's advice and un-commented the "deb http.* lines".

Now, there was another complain from the Update Manager:

## Update Packages NOT downloaded June 5,2008
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /pool/main /s/seahorse/seahorse_2.22.2-0ubuntu1_amd64.deb
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /pool/main /g/gnome-keyring/libpam-gnome-keyring_2.22.2-0ubuntu1_amd64.deb
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /pool/main /e/evolution-data-server/libexchange-
# storage1.2-3_2.22.1.1-0ubuntu3_amd64.deb
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /pool/main /e/eel2/libeel2-2_2.22.2-0ubuntu1_amd64.deb
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /pool/main /g/gvfs/gvfs-fuse_0.2.4-0ubuntu1_amd64.deb
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /dists/hardy/Release.gpg
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /dists/hardy-updates/Release.gpg
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) /dists/hardy-updates/main/i18n/Translation-en_CA.bz2

Is there something I miss in my sources.list (Attached)


EDIT: Case closed!
Next time I started automated update there where no error messages and the system was declared "up to date".

Anyway, it would be interesting for me if I knew that my sources.list is OK.
Maybe somebody could check the attachment.


Thanks for the support!

---

