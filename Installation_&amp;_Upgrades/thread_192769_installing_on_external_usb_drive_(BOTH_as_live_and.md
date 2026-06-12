---
title: "installing on external usb drive (BOTH as live and as persistent)"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by edoardo on 2006-06-09
I had a look at the install from usb [https://wiki.ubuntu.com/Installation/FromUSBStick](https://wiki.ubuntu.com/Installation/FromUSBStick)
has anyone tried it with 6.06 ?

I have an external 30G usb drive that used to contain a bootable dapper alpha with vmware and a large fat32 data partition that included my vmware machines.

Now that bootable alpha only worked for my won laptop. 
I'd like to repartition the drive so that on boot from USB I'd get a grub menu which allows me to choose
-the installed dapper (to have an optimal system when booting attached to my laptop)
-a LIVE cd -like system which does hw detection to which I added vmware player (to have a subotpimal system to be used for booting attached to any other machine)

has anyone any pointers ?

---

### Post by hubick on 2006-07-06
I just got my ext2 formatted usb flash drive booting the live desktop (copied from the live cd image) via grub.  Details at [http://ubuntuforums.org/showpost.php?p=1221276&postcount=153](http://ubuntuforums.org/showpost.php?p=1221276&postcount=153)

---

### Post by edoardo on 2006-07-14
thanks, I did it too, in my case with a custom live cd!
[http://ubuntuforums.org/showpost.php?p=1221276&postcount=153](http://ubuntuforums.org/showpost.php?p=1221276&postcount=153)

---

