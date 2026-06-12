---
title: "Failed to install the bootloader."
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-03-06
Hi,

I am trying to install today's daily image on USB using disk creator but i get this error.

> Failed to install the bootloader.

Thanks.

---

### Post by wilee-nilee on 2010-03-06
I have gotten the same with Lucid using the usb creator but unetbootin will load the usb. With lucid though I have to hit enter at the boot screen then tab to get it to read the iso.

---

### Post by gibbylinks on 2010-03-06
> **soham_1207 said:**
> Hi,

I am trying to install today's daily image on USB using disk creator but i get this error.



Thanks.

This is a confirmed bug. See this thread [http://ubuntuforums.org/showthread.php?t=1418127](http://ubuntuforums.org/showthread.php?t=1418127)

---

### Post by VMC on 2010-03-06
It is fixed with my current updates. I used it just now to confirm.

---

### Post by donniezazen on 2010-03-06
> **VMC said:**
> It is fixed with my current updates. I used it just now to confirm.

Thanks. Another thing is it takes too long to load Ubuntu untill then their is a black screen for over 5 mins. And i had to hard boot after installation.

---

### Post by sparker256 on 2010-03-06
> **VMC said:**
> It is fixed with my current updates. I used it just now to confirm.

My installed version is 0.2.17 and mine is still giving the "Failed to install the bootloader" error as of today's updates.

---

### Post by sparker256 on 2010-03-06
> **VMC said:**
> It is fixed with my current updates. I used it just now to confirm.

My version that works in 9.10 is

```

bill@game-910:~$ usb-creator-gtk --version
0.2.8
bill@game-910:~$ aptitude show usb-creator-gtk
Package: usb-creator-gtk
State: installed
Automatically installed: no
Version: 0.2.12
Priority: optional
Section: admin
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Uncompressed Size: 193k
Depends: python, python-central (>= 0.6.11), usb-creator-common (= 0.2.12),
         python-gtk2 (>= 2.12), python-dbus, python-gnome2
Description: Ubuntu USB desktop image creator for GTK+
 This is a simple utility designed to make bootable USB desktop images from
 Ubuntu CDs. 
 
 This package contains the GTK+ client frontend.

```

---

### Post by VMC on 2010-03-06
That's strange. I have a Jan dailt-live that I keep updated and it works. It show this:

```
$ usb-creator-gtk --version
0.2.8
```

Also I have another Lucid installed using live-dailt of Mar5th and it works.

---

