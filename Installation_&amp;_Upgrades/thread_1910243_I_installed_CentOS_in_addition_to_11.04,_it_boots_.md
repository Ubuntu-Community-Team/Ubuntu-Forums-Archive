---
title: "I installed CentOS in addition to 11.04, it boots straight into CentOS now."
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by vincegata on 2012-01-16
Hi,

I had 11.04 installed:
/dev/sda1/ - swap
/dev/sda2/ - ext4 with 11.04

then I installed CentOS on extra space:
/dev/sda3/ - ext4 CentOS

Now it boots straight into CentOS, I expected some menu where I could choose between Ubuntu and CentOS.

How can I fix it? I do not care if I have to remove CentOS but I want to keep Ubuntu.

Thank you!

---

### Post by howefield on 2012-01-16
The earlier version of Grub that CentOS uses has overwritten your previous Grub installation. Reinstall Grub2 with your Ubuntu Live CD. It should pick up both operating systems.

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by vincegata on 2012-01-16
It worked, I get the menu so I can boot both. Thank you!

---

### Post by howefield on 2012-01-17
You're welcome, dual boot for the win :)

---

