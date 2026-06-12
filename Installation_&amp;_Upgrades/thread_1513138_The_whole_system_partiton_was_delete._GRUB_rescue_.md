---
title: "The whole system partiton was delete. GRUB rescue error"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by m4design on 2010-06-19
Hi,

I (stupidly) deleted the partition that was holding Ubuntu. The system had windows xp before, but now I can't boot into windows.
I [magicly]("http://tuts4tech.net/2009/07/14/creating-a-usb-bootable-xp-recovery-console/") were able to log-in into the windows recovery system, and then tried rebuilding the boot configuration. But when I restart I stil get the GRUB rescue message.


Unfortunately I have a netbook, so no CD drive available.


Edit: I only found the 'ls' command that is working, not even 'help' is identified anymore.

---

### Post by dino99 on 2010-06-19
maybe you can reinstall with a usb stick (unetbootin)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu](http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu)

---

### Post by darkod on 2010-06-19
Since you have a netbook, do you have ubuntu bootable usb stick?

Just boot with it, and to quickly fix you hdd mbr in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command it will show you some warnings that will sound scary. Ignore them, it's normal. Just run the second command too.

That should make XP boot. Later on you might consider installing ubuntu again if you want to.

---

