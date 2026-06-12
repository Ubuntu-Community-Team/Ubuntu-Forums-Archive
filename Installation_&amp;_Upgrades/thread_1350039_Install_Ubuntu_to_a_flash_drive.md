---
title: "Install Ubuntu to a flash drive"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by chrisab508 on 2009-12-08
Hey Guys,
I have searched around for a while trying to figure out if this is possible.  I don't want to put a liveCD on a flash drive, I know this is very easy using tools like Unetbootin for example.  I was wondering if there was a way to actually install Ubuntu on a flash drive?  I.e. make Ubuntu run off a flash drive just like it would from a hard drive, saving settings and software downloaded, etc.

Thank you in advance,

- Chris

---

### Post by MelDJ on 2009-12-08
what i normally do is tell the installer to install to my pendrive.
check this website: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by darkod on 2009-12-09
> **MelDJ said:**
> what i normally do is tell the installer to install to my pendrive.
check this website: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I haven't used the mentioned tool but I see no reason to install linux into linux. Depending how it creates the whole process.
Yes, you can install it simply to the usb stick, like you said. Boot with the cd or another usb stick with the installation files on it, and simply specify as destination the usb stick you want, just like it is internal hdd. In the last step 7, before clicking Install, click on Advances and make sure grub2 will get installed on the usb stick and not the internal hdd. Depending what the stick is called in step 4, /dev/sdb, /dev/sdc etc, grub2 need to go to the same device. Select it yourself if it's not automatically selected.

---

