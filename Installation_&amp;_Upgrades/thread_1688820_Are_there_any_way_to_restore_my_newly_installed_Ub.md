---
title: "Are there any way to restore my newly installed Ubuntu as my Deleted on:"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by erogol on 2011-02-15
I have already a UBUNTU in my system but I will remove it and will install again but I wonder that is there any way or a program to restore my newly installed Ubuntu as my removed one. I mean, I want to see all my system settings and programs will be in my newly installed Ubuntu as the old one.

Thanks for help.

---

### Post by clgy15 on 2011-02-15
I havent seen something thats like the windows migration assistant but you could backup your config files. Theres a few guides for backing up your settings for unbuntu around

---

### Post by tommcd on 2011-02-15
> **erogol said:**
> I want to see all my system settings and programs will be in my newly installed Ubuntu as the old one.

If you have a separate home partition, then all of your individual user settings will be preserved, as these are stored in hidden (i.e., they start with a period) files and folders in your home directory. Also, all of your data will be safe since your home directory is on a separate partition.
If you do not have a separate home partition, then reinstalling Ubuntu is a good opportunity to create one.

---

### Post by Bucky Ball on 2011-02-15
> **tommcd said:**
> If you have a separate home partition, then all of your individual user settings will be preserved, as these are stored in hidden (i.e., they start with a period) files and folders in your home directory. Also, all of your data will be safe since your home directory is on a separate partition.
If you do not have a separate home partition, then reinstalling Ubuntu is a good opportunity to create one.

++1. Manual partition when installing and just don't format /home (if you have one) or /swap for that matter. You only need to install Ubuntu OS to /.

Good luck.

---

