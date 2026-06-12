---
title: "Install near Win8.1 and Win10"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by furlani-massimo on 2015-11-11
[LEFT]               [LEFT]Good morning.
I would like to install Ubuntu on my notebook 14.04, near Win 8.1 and Win10. Now I use the bootloader to Win10 to access the two operating systems.

I wanted to know where to install grub, in the ubuntu partition?

Thank you.

[/LEFT]
             [/LEFT]

---

### Post by yancek on 2015-11-11
windows 8 and 10 default to using UEFI so dual booting windows and Ubuntu will be different.  Some details on it at the Ubuntu site below.  You need to select the option to use UEFI when booting Ubuntu to install so I would suggest reading through the link below and posting back if you have questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-11-11
Post this from terminal in Ubuntu live installer,  to see current configuration:
 sudo parted -l

---

