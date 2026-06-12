---
title: "Install ubuntu 9.04 with a cd-rw of 650 mb"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by Wakawakamush on 2010-09-08
Hi,

I need to install Ubuntu 9.04 to fix my grub error 17, but when i try to burn the ISO to the CD-r it (Nero Burning ROM Essentials)says that i need to use a CD-rw, but i only have a CD-rw of 650 MB. can i install Ubuntu with that CD?

I cant use a usb stick, when i try that i get a weird screen that is striped and the stripes change color from white to black. (Wow, that was a bad explanation!)

---

### Post by mörgæs on 2010-09-08
Yes, you can install the mini.iso:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After installing and rebooting, run the command

```
sudo apt-get install ubuntu-desktop
```


Remember to have wired internet access during the process.

By the way, 9.04 is running out of support next month. Wasn't it better to go for a clean install of 10.04?

---

### Post by Wakawakamush on 2010-09-08
I already fixed the grub and installed Ubuntu, but thanks for replying.

I am not going to install 10.04 because that was the cause of my grub error 17.

---

