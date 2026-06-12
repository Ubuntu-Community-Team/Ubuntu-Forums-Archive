---
title: "force local repository on upgrade"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by dread22 on 2009-11-23
I want to upgrade from 9.04 to 9.10 but I have a much faster connection to the local repository than the official ones and my downloads are not counted.

Is there a way to force the use of the local mirror for the distribution upgrade instead of the official mirror.

---

### Post by sebastianabate on 2009-11-25
Yes, you can. This is extracted from _[this bug]("https://bugs.launchpad.net/ubuntu/jaunty/+source/adept/+bug/147080")_

> The way it works is that you drop a file in /etc/update-manager/release-upgrades.d/
 with the extension .cfg (e.g.  /etc/update-manager/release-upgrades.d/my-config.cfg) that contains:
 [Sources]
AllowThirdParty=yes


---

### Post by sedawk on 2012-05-18
Thankx, your solution is the easiest and best solution I found on
the internet!

In more detail, here is what I did to install from in "apt-mirror" mirror
on my usb-stick:

1) I did a final apt-get update and apt-get upgrade with the old distro
   and the old sources.list. I checked that update-manager offers the
   button for installing the new distro.
2) Copied sources.list to sources.list.net and created a new sources.list
```

deb file:/media/<usb_mirror>/ubuntu precise main restricted
deb file:/media/<usb_mirror>/ubuntu precise-updates main restricted

```
3) Tried apt-get update to see if the new sources.list works 
4) created /etc/update-manager/release-upgrades.d/my_mirror.cfg
   according to your posting
5) Start update-manager (-d) 
6) Stage "Getting new packages" took some time (checking packages?), but
   did not download anything
7) Installation started and is still running now.
   (Installation from my USB stick is estimated to take 1 hour) 

Post) Update entries in sources.list.net manually to new distro and
      copy it to sources.list again ...

Thankx

---

