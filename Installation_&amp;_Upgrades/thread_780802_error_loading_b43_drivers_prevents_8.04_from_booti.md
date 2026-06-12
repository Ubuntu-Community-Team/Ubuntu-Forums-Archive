---
title: "error loading b43 drivers prevents 8.04 from booting?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by shreaded_teddy on 2008-05-03
installed 8.04 to a 8Gb usb flash drive on my dell e1505 laptop.  ran off the live cd no problem but when it boots the install off the usb it loads the desktop background and the cursor but won't do anything after that.  pressed ctr + alt F8 which brought up a black screen that kept giving me an error about b43/ucode5.fw and something about linuxwireless.org/en/users/drivers/b43#devicefirmwareversion4.  is there an easy way to skip this driver or copy the drivers to the flash drive from a different computer?  also would installing the restricted drivers for my wireless when running the live cd then installing fix this?

---

### Post by alan34 on 2008-05-04
The file you need to edit is

/etc/modprobe.d/blacklist

On a line on its own at the bottom of the file add

blacklist b43

You should be able to edit the file using the live cd or pick the recovery mode from
the grub menu and pick drop to a root shell then enter

cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup

vi /etc/modprobe.d/blacklist

curser down to the bottom hit the letter o ( lower case ) then type

blacklist b43

then hit the Esc key twice, then type :wq!

Sorry about the horrible editor but it is the one I am used to.

If you mess up editing the file hit the Esc key and type :q! will exit the editor without saving.

To restore the backup file type

cp /etc/modprobe.d/blacklist.backup /etc/modprobe.d/blacklist

---

### Post by shreaded_teddy on 2008-05-08
i added "blacklist b43" "blacklist b43-phy0" and ""blacklist b43/ucode5" in the blacklist file but no matter what i try it still won't load anything more than the background and the mouse cursor.  ctrl + alt F8 doesn't display anything anymore so i'm stumped, any ideas?

also tried putting the firmware in /lib/firmware manually like [http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/) shows but still no luck.

~ended up installing 7.10, used the restricted drivers, then upgraded to 8.04 which now boots up no problem.

---

