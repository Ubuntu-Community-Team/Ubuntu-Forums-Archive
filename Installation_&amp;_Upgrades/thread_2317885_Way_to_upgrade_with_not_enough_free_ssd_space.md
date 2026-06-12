---
title: "Way to upgrade with not enough free ssd space?"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by ultragamer2 on 2016-03-21
I am asking about this for the future what I anticipate to happen.

I Lubuntu installed on an 8gb ssd and it works well, I left a bit of space to over provision which I had to reduce recently due to not enough free space for the software updater to install updates.

But this makes me think when Lubuntu 16.04 comes out I probably won't have enough space to run the automatic upgrader program.
Is there a way I can use a usb stick to store the downloads or some other method to get around this with the automatic upgrader?

---

### Post by sudodus on 2016-03-21
I suggest that you get a big and fast USB 3 pendrive (at least 16 GB, maybe even more for example 32 GB). See the following links to get tips on what to select,

[Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

[Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

Then you can clone your system from the 8GB SSD to the USB pendrive. You can clone with ***Clonezilla*** or ***mkusb***.

And then you can use the cloned system in the pendrive for upgrading to 16.04 LTS. But I suggest that you wait until July or August, when 16.04.1 LTS will be released. By that time the worst bugs will be squashed :-P

After upgrading to the 16.04.1 LTS system you should clean it to get rid of old files so that it will be small enough to squeeze into the 8 GB SSD. But this time you cannot use cloning. You can't clone into a smaller drive. Instead you can use for example ***rsync***, fix some settings and install the bootloader manually.

-o-

An alternative is to keep only the /home directory and make a fresh install of 16.04 LTS. It means that you have to reinstall the program packages, that you have installed manually, but the settings of your environment and your personal files (saved in your home directory) will be there.

---

