---
title: "Xubuntu 20.04 LibreOffice Help doesn't work"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by rattskjelke on 2020-04-24
I did a fresh install of Xubuntu 20.04 LTS.
When I ran LibreOffice the built in Help function didn't work.
All I got was an empty two-paned window with the title *LibreOffice Help* and a pop up error window that says:
```
!
Object not accessible.
The object cannot be accessed due to insufficient user rights.
```
I purged libreoffice* and did a full install. Still no help and the same error message.

Then I booted the Xubuntu 20.04 LTS live install USB to see what was installed there. It has:
```
Listing...
libreoffice-base-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-calc/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-common/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-draw/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gnome/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gtk3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-impress/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-math/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-style-colibre/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-elementary/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-tango/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-writer/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
```
Help isn't installed by default and the same thing happens (blank window and error).
So I went back to my HD installation purged *libreoffice** again and installed the default apps above plus *libreoffice-help-en-us* and *libreoffice-help-common*. Still no Help. It still just makes a blank window and the error message window.

Is there a way to fix it or is LibreOffice now limited to online help only?

---

### Post by rattskjelke on 2020-05-12
Am I the only person who uses LibreOffice on Xubuntu??

---

### Post by tea for one on 2020-05-12
There is a bug already raised in Launchpad

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1869561](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1869561)

Also, there is a work-around in comments 9 and 10

---

