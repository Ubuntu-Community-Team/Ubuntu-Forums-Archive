---
title: "Cannot Dual Boot?! Boot record unaffected!"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by madhatter64 on 2007-09-16
I have tried 3 times, with same results.

Ubuntu install works, but the bootloader is not affected... in othr words, I'm stuck with XP after a seemingly perfect install of Ubuntu.


Help?

---

### Post by Pumalite on 2007-09-16
Plug in Live CD, mount your partition and post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by madhatter64 on 2007-09-17
Can you tell me more about these commands? What can I expect to happen after I enter them?

Thanks

MH

---

### Post by Pumalite on 2007-09-17
The output of these commands will give me the information I need to help you.

---

### Post by Shazaam on 2007-09-17
In a console session fdisk prints out your disk geometry. The other command prints out your menu.lst file (used for booting linux).
fdisk is the command and -lu are the arguments used to control the information printed out.

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

