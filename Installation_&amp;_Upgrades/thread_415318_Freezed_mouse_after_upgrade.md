---
title: "Freezed mouse after upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by wakan on 2007-04-20
After upgrading my xubuntu to feisty, my ps/2 mouse (working fine on prevoius xubuntu) is now freezed in the middle of the screen.
mdetect found it as an Intellimouse on psaux...I changed /etc/xorg.conf in various way, but with no success.
If I attach a usb mouse, it works nut I have to replug the mouse after X starts...
but I need ps2 mouse...it must work...why it worked in previous version?

---

### Post by Pete051 on 2007-04-20
I've been having the same problem on an alternate install of feisty, every thing worked fine then suddenly for no obvious reason the mouse and keyboard (Logitech itouch cordless) froze leaving the reset button as the only way out :( seems to be behaving it' self at the moment hope it continues

---

### Post by wakan on 2007-04-20
I tried
cat /dev/input/mice ...(or /dev/input/mouse0, or /dev/psaux)
but no garbage on the screen....
maybe the driver is not working? (even if with lsmod | grep mouse return psmouse)
...
what do you think?

---

### Post by renegado675 on 2007-04-20
I too have this problem with ny mouse (PS2). How can I solve it? HELP ME

---

### Post by Simon G Best on 2007-04-21
Others have been having this problem: [http://ubuntuforums.org/showthread.php?t=415872]("http://ubuntuforums.org/showthread.php?t=415872").

For a temporary work-around, you could choose an older kernel from GRUB's boot menu.  That's what I'm doing.  Of course, you need an older kernel available for that, though.

---

