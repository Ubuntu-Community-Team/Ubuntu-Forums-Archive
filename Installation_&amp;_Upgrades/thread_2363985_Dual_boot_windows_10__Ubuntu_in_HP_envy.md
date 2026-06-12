---
title: "Dual boot windows 10 / Ubuntu in HP envy"
date: 2017-06-17
forum: Installation &amp; Upgrades
---

### Post by frjaher on 2017-06-17
This is the first time I decide to install ubutu seriously

Now way, I've tried everything but I cannot grub boot loader to work. My computer always start with Windows....

I've Installed Windows creating an extra partition at the begin of the disk and tried boot-repair... nothing.

I've been trying for a while to upload th report from boot-repair, but I didn't success. 


Help!

---

### Post by yancek on 2017-06-17
Is windows 10 UEFI.  Check the Ubuntu documentation which tells how to install Ubuntu UEFI.  You need both systems UEFI or both MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Without the information from boot repair it will just be guessing.  On boot you should be able to hit the Esc key and have several option after hitting the F9.  Check to see if you have multiple options.

---

### Post by oldfred on 2017-06-17
Boot-Repair's report is too big in most cases to post to forum.
And sometimes it is not copying or giving a correct pastebin link.
But you still can manually copy the report to any pastebin site. If from live installer, it tries to save report in your ESP - efi system partition. If from working install it saves to your /var/log/boot-sav/log folders.

---

