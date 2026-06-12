---
title: "Can't boot windows partition after upgrade to 10.4"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by quimkaos on 2010-04-09
After upgrade to Ubuntu 10.4 i can't boot windows partition. the only thing i get it's a blinking underscore after choosing it from grub.
under ubuntu the window partition seams to be ok, and i can access every file.

this is my partition table:
sda1 - ntfs
sda2 - extended
sda5 - swap
sda6 - ext4 linux (0x83)

any ideas how to solve this?
is there any tool to config grub? like yast on suse?
(off the topic : is there any "grafic" version of grub?)

---

### Post by lindsay7 on 2010-04-09
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by quimkaos on 2010-04-09
didn't work...

backing up data and going to rebuild the system from scratch...
i'm getting also trouble with compiz with 10.4 beta

---

### Post by oldfred on 2010-04-09
Did grub install to the windows PBR? If so you will have to run the windows repairs.

---

