---
title: "No multi-user log-in"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Alacrity on 2010-04-24
Installed ubuntu 10.04RC on a 8GB usb flash.  Added two more users (total of three:  two admin and one desktop guest.  All requiring password sign-in.

Rebooted and Ubuntu does not stop with a log-in sheet but goes all the way to a running fully booted system under the first admin.

I put a bug report in to Ubuntu (Bug #569495).

Also seems to be related to the remastersys process as well.  Making a remastersys iso and then applying it to another usb via Startup Disk Creator produces a boot o/s that only ends in a custom log on page and no authentication success.

Anybody else seeing one or both of these issues?

---

### Post by dcstar on 2010-04-24
> **Alacrity said:**
> **Installed** ubuntu 10.04RC on a 8GB usb flash.  Added two more users (total of three:  two admin and one desktop guest.  All requiring password sign-in.

Rebooted and Ubuntu does not stop with a log-in sheet but goes all the way to a running fully booted system under the first admin.

I put a bug report in to Ubuntu (Bug #569495).

Also seems to be related to the remastersys process as well.  Making a remastersys iso and then applying it to another usb via Startup Disk Creator produces a boot o/s that only ends in a custom log on page and no authentication success.

Anybody else seeing one or both of these issues?

If "installed" means you made a Live USB device then that is **exactly** how it is supposed to work.

If "installed" means you did a full Ubuntu installation process onto the drive, then it shouldn't happen.

A Live USB is **not** a proper Ubuntu installation, it is for booting a portable device for a single user instead of using a CD.

---

### Post by popat007 on 2010-04-24
No need to do this
> I put a bug report in to Ubuntu (Bug #569495).


just create casper-rw (read-write) drive on USB on different partition.

---

### Post by Alacrity on 2010-04-24
> **dcstar said:**
> If "installed" means you made a Live USB device then that is **exactly** how it is supposed to work.

If "installed" means you did a full Ubuntu installation process onto the drive, then it shouldn't happen.

A Live USB is **not** a proper Ubuntu installation, it is for booting a portable device for a single user instead of using a CD.



I did a full Ubuntu 10.04 installation on to the usb flash.....so from what you say,....it should not happen.  I have done this with many other previous Ubuntu versions successfully.

---

### Post by Alacrity on 2010-04-25
SOLVED.

Incorrect settings on the System/Administation/Login Screen.

Now get mulitiple user log-in.

---

