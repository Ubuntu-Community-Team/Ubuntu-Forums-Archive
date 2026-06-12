---
title: "Trying to create bootable copy of laptop on external usb drive. Ubuntu 16.04.1"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by khmerkerry on 2017-01-25
I can create iso using Pinguy Builder or Systemback - I can create bootable disk from Etcher or Startup Disk Creator but no user / pass combinations work.  Tried terminal dd but now system will not recognize usb drive - I have tried now for 1 week to create copy of system that I can boot from and reinstall from - nothing works - please help

---

### Post by yancek on 2017-01-25
I'm not familiar with the other software but you should certainly be able to do this with Systemback.  If you run it from an installed system on which you have created a user with a password, that user and password will be available when you boot the created iso.  That's how it worked for me.  Systemback creates an iso of an installed system.  An installed system does not have an installer as there would be no point to that.  If you want an installer on the created iso, you will need to install the ubiquity installer on the installed system before you run Systemback from it.

I think the following command should install Ubiquity but haven't tried it myself.

```
sudo apt-get install ubiquity-frontend-gtk
```

I have an installation of Lubuntu on my computer and booted it up and ran the above command which did install Ubiquity.  Didn't create the Desktop icon but it may do that on Ubuntu?  If not, just right click the Desktop and select Create Launcher and navigate to /usr/bin/ubiquity.  You can also start it from a terminal with that command or with just ubiquity.

---

