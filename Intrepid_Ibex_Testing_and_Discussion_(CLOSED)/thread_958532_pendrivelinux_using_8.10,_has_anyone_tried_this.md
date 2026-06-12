---
title: "pendrivelinux using 8.10, has anyone tried this?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-10-25
[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

how well does it work?
Does this mean you can put in the usb thumb drive and boot the pc without anything else?
What does it do about graphics cards?

---

### Post by psyke83 on 2008-10-25
> **sdowney717 said:**
> [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

how well does it work?
Does this mean you can put in the usb thumb drive and boot the pc without anything else?
What does it do about graphics cards?

You don't need to use external scripts anymore. Ubuntu now ships with a utility named "usb-creator" that creates a persistent USB image. Although you may need to manually format your USB key before installing, it works perfectly!

---

### Post by sdowney717 on 2008-10-25
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

do you have to boot the live cd? it would be nice to just have the iso downloaded and simply use that.

---

### Post by psyke83 on 2008-10-25
> **sdowney717 said:**
> [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

do you have to boot the live cd? it would be nice to just have the iso downloaded and simply use that.

That wiki page is outdated. If you're running Intrepid now, launch usb-creator and it'll go through the steps to create a bootable, persistent USB image. You only need the ISO to create the image, not a CD.

---

