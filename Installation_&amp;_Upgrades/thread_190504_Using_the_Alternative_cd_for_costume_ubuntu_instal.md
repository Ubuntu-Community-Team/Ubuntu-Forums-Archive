---
title: "Using the Alternative cd for costume ubuntu installs..."
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by encompass on 2006-06-06
I am working wit some hardware vendors and creating some laptops and other what not, and I wnat ot set up these systems to have ubuntu on them.  Is there a way to create and OEM cd that could easily restore their system toa fresh install with no effort on there part?  I would love to know how.  Perhaps the best way is just to use an image cd.  What would be my best options whith an cd bootable image installer.  Ideas anyone?
Thanks for the help....

---

### Post by rcarring on 2006-06-06
First you would have to install Ubuntu with a default user. Use the alternate cd and create a user called ubuntu-user when asked, set password to same value.

Test installation.

Use a drive cloning program to create a drive image (I am not conversant with such programs for Linux, but maybe someone else could advise)

The drive image may span more than one cd.

Make a bootable cd.

Restoration:

Boot with bootable cd
Re-image the drive

User then removes the last cd and reboots

Logs in as ubuntu-user.

Problems: the restore cd will return the drive to factory fresh condition and won't include any mods made by the user, config files, app installs and updates.

I guess you know this already, but somebody else may be able to use this as a template for advising you how to do this.

Sorry, cannot help more.

---

### Post by az on 2006-06-06
There is an EOM installation mode on the alternate cd, AFAIK....

---

