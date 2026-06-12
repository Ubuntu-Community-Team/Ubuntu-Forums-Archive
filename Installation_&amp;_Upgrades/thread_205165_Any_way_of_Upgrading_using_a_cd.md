---
title: "Any way of Upgrading using a cd?"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by morbid_bean on 2006-06-28
I want to upgrade my current version of ubuntu (v. 5.10) to the newest one (v. 6.06)....and since my internet is so crappy it would take a long time to upgrade it from using the internet. My question is that can you upgrade it by using the cd, without having to remove the current v. 5.10 out....or would you have to do that?

---

### Post by aysiu on 2006-06-28
If you have the Alternate Install CD, yes. If you have the Desktop CD, no.

First, make sure you have the appropriate metapackage installed: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` since you appear to be using Gnome.

Pop the Alternate Install CD in your drive. ```
sudo cp /etc/apt/sources.list /etc/apt/sources.breezy.list
sudo nano /etc/apt/sources.list
``` Erase (Control-K) all the sources in there. Save (Control-X), confirm (Y), exit (Enter). ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
``` [quote=morbid_bean]My question is that can you upgrade it by using the cd, without having to remove the current v. 5.10 out....or would you have to do that?[/quote] An upgrade, by definition, replaces the old version. Or were you planning to dual boot 5.10 and 6.06?

---

### Post by alamba on 2006-06-28
[http://daniel.holba.ch/blog/?p=14](http://daniel.holba.ch/blog/?p=14)

I think this should work if you add the 6.06 CD as part of the repositories in synaptic.

A

---

