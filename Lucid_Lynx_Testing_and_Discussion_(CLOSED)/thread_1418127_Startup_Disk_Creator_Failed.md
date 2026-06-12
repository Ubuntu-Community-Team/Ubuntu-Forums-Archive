---
title: "Startup Disk Creator Failed"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-02-28
Starting with yesterdays (02-27-10) updates I cannot make a live USB. I have been making daily live USB's for months and this is the first time had any trouble with "Startup Disk Creator".

It tries to install the bootloader and fails. I get the attached dialog box.

Bill

---

### Post by twelve on 2010-02-28
Yes same issue here with Startup Disk Creator.First i thought the problem was with my usb.

---

### Post by sparker256 on 2010-02-28
> **twelve said:**
> Yes same issue here with Startup Disk Creator.First i thought the problem was with my usb.

I tried three of my thumb drives with the same result. I used 9.10 usb disk creator and it worked fine. I have filed this bug report.

[https://bugs.launchpad.net/lucid/+bug/529481](https://bugs.launchpad.net/lucid/+bug/529481)

Bill

---

### Post by VMC on 2010-02-28
I also have the same issue.

I have Mint8 installed. I install the usb creator, and it worked.
It installed version 0.2.8

But on both system the version numbers differ from what aptitude shows. On Ubuntu it has a higher version in aptitude. This is the one that fails. But still interesting of the different version info.

From current Ubuntu:
```
 $ usb-creator-gtk --version
[COLOR="Red"][B]0.2.8
[/B][/COLOR]
===============================
$ aptitude show usb-creator-gtk
Package: usb-creator-gtk
State: installed
Automatically installed: no
[COLOR="Red"]**Version: 0.2.16**[/COLOR]
Priority: optional
Section: admin
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Uncompressed Size: 197k
Depends: python, python-central (>= 0.6.11), usb-creator-common (= 0.2.16),
         python-gtk2 (>= 2.12), python-dbus, python-gnome2
Description: Ubuntu startup disk creator for GTK+
 This is a simple utility designed to make startup disks from Ubuntu CDs. 
 
 This package contains the GTK+ client frontend.

```

Thanks for creating the bug report. I will "me too" it.

---

### Post by Didius Falco on 2010-02-28
I added a "me too" as well. For me, USB Creator has never worked, across versions and different computers.

---

### Post by bennachie on 2010-02-28
Not sure if this is relevant, but I have noticed in 9.10 that USB Disk Creator never works if you set the persistent partition to the maximum possible size. It works OK if you back off by 10% or so.

---

### Post by gibbylinks on 2010-03-06
> **bennachie said:**
> Not sure if this is relevant, but I have noticed in 9.10 that USB Disk Creator never works if you set the persistent partition to the maximum possible size. It works OK if you back off by 10% or so.

This makes no difference here :o

---

### Post by sparker256 on 2010-03-06
> **bennachie said:**
> Not sure if this is relevant, but I have noticed in 9.10 that USB Disk Creator never works if you set the persistent partition to the maximum possible size. It works OK if you back off by 10% or so.

I set mine to 2G on a 8G flash drive. I saw that we got a new updated version on 03-05-10 and it still has the same problem. Anyone else still have the same problem. The new bug number is [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/529366](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/529366)

Bill

---

### Post by MacUntu on 2010-03-08
Working fine again with version 0.2.18.

---

### Post by knattlhuber on 2010-03-17
> **MacUntu said:**
> Working fine again with version 0.2.18.

0.2.18 doesn't install under Karmic because of unmet dependencies (package 'udisks', which in turn won't install either...). Does anybody know how to make it work?

---

