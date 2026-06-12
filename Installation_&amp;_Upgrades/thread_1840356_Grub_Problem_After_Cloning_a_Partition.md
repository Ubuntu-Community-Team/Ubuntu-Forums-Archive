---
title: "Grub Problem After Cloning a Partition"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by miousername on 2011-09-07
Hi at all,
This is my problem:

I've an hold Hard Disk with Windows XP and Ubuntu, I copied my ubuntu partition /dev/sda6 in a new ssd hard disk with gparted (I used "copy" from my old hard disk and "paste" in my new ssd).

With Ubuntu Live CD I tried to reinstall grub with some HOW TO like this :

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

without any success, grub give me the error :

Error 15 File Not Found

grub-install doesn't work.


How can I do to reinstall grub and boot my copied partition?

---

### Post by oldfred on 2011-09-07
Several issues. You have instructions for reinstalling grub legacy, but all the versions since 9.04 use grub2, so you need instructions to reinstall grub2. But having tried to install old grub you may have bigger issues and now have to chroot into your system &  uninstall both grub & grub2 and do a clean reinstall of grub2. 

If you cloned the partition do you have both drives still connected. You may have the same UUID for the partition which cannot be. You have to change the UUID before doing anything.

To see UUIDs
```

sudo blkid
```

If they are the same change one:
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YesWeCan on 2011-09-07
+1
and you will also need to edit the fstab file for the Ubuntu whose partition has had its UUID changed. Otherwise when you try to boot it the original root directory will be mounted in error.

---

### Post by miousername on 2011-09-08
:)
Thank you very much guys!
You solved my problem!The new ssd Hard disk now it works !

Bye!):P

---

