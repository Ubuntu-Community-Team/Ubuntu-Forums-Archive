---
title: "digikam 3.5 download very slow on Ubuntu 14.04"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2014-06-10
I recently upgraded from Ubuntu 13.04 to 14.04.

Since the upgrade, the rate at which digikam downloads images from the camera has decreased by a factor of 100.
Before the upgrade, the transfer rate was about 2 images/sec.
After the upgrade, the transfer rate is about 1 image/minute.

I submitted a bug report, and I got the following reply:
[https://bugs.kde.org/show_bug.cgi?id=336022](https://bugs.kde.org/show_bug.cgi?id=336022)

Gilles Caulier [EMAIL="caulier.gilles@gmail.com"]<caulier.gilles@gmail.com>[/EMAIL] changed:

           What    |Removed                     |Added
----------------------------------------------------------------------------
             Status|UNCONFIRMED                 |RESOLVED
                 CC|                            |[EMAIL="caulier.gilles@gmail.com"]caulier.gilles@gmail.com[/EMAIL]
         Resolution|---                         |UPSTREAM

--- Comment #1 from Gilles Caulier [EMAIL="caulier.gilles@gmail.com"]<caulier.gilles@gmail.com>[/EMAIL] ---
Nikon camera use Gphoto2 camera driver.

The dysfunction is clear : with same digiKam version running on different
Ubuntu releases, You see introduced time latency with last internal components.
This want mean that libgphoto, or libusb, has a problem (or another sub
library)...

Gilles Caulier

As a test, I downloaded gphoto2,which also uses libgphoto for downlods.  When I executed
>gphoto2 --get-all-files
the files transfer rate was about 2 images/sec.

I tried and failed to submit a bug report using ubuntu-bug.

---

