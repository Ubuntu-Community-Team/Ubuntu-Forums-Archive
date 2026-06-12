---
title: "Ubiquity preseeding"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Rajvan on 2008-07-11
Hello,

I have created a unattended ubuntu installation for the office using remastersys and ubuntu8 (USB installation) from [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).

And finally I got the preseed part to work, using a preseed file i found on google. It uses ubiquity instead of the "d-i" commands found here: [https://help.ubuntu.com/7.04/installation-guide/powerpc/preseed-contents.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/preseed-contents.html)

The whole installation is now automated, except for some small details.. After the installation I would like the computer to reboot automatically, and not to eject the cdrom (since its installing from USB this is just annoying).

So, anyone know what the parameters should be for ubiquity?
With the d-i commands it looks like this:

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean false

Thanks,
Rajvan

---

### Post by Rajvan on 2008-07-14
Anyone?

---

