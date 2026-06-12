---
title: "Ask for root passwd"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by tsnsidon on 2006-03-06
Hi all,

I download the image Ubuntu 5.10, burned it to the CD and installed well.

Ubuntu run nicely with the normal user I created drung installation.
However, when everything seems good, I need to change the default boot loader to Windows. I tried to alter /boot/grub/menu.lst. Certainly,  it require root.

I tried :

$ su

then I didnot get the password....

I thought I have miss some where during the installation phase. I tried to new-install Ubuntu again. No where did I find the installer ask for root passwd.

I tried with 
root
admin
[blank]

None above works. :-k 

Kindly comment. Thanks in advance

---

### Post by taurus on 2006-03-06
Try
```

sudo gedit /boot/grub/menu.lst
(And when it asks you for a password, use the same one that you log in to your account...)

```

---

### Post by hod139 on 2006-03-06
"By default, the password for root is locked in Ubuntu. This means you cannot login as root or use su."  See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for all the details.

---

