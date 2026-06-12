---
title: "Bug in usb-creator-gtk"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by kerryhall on 2012-04-05
I'm trying to make a bootable usb drive. I'm using usb-creator-gtk. When I try to use the file selection dialog to pick and ISO, I click "open" but the iso does not get added to the list of images. The most frustrating error, the ones that fail silently.

---

### Post by Paddy Landau on 2012-04-06
This program is specialised for Ubuntu, and will accept only Ubuntu ISOs.

(I agree that Startup Disk Creator should give an error message instead of just not doing anything. Perhaps you can raise this as a bug?)

If you wish to write a non-Ubuntu ISO, you need to use something like unetbootin (I think it is available from the standard repositories).

---

### Post by kerryhall on 2012-04-23
Thanks for the help here!

---

### Post by techsupport on 2012-04-23
> **kerryhall said:**
> I'm trying to make a bootable usb drive. I'm using usb-creator-gtk. When I try to use the file selection dialog to pick and ISO, I click "open" but the iso does not get added to the list of images. The most frustrating error, the ones that fail silently.

Unetbootin should work. 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

```
sudo apt-get install unetbootin
```

And I only use Startup Disc Creator to erase my USB Pendrive when need be.

---

