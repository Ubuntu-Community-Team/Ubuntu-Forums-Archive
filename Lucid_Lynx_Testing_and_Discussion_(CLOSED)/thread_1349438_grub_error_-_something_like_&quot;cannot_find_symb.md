---
title: "grub error - something like &quot;cannot find symbol 'grub_gettext' &quot;"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-12-08
I just installed the latest grub updates and on reboot got an error that read something like "cannot find symbol 'grub_gettext' ". It then dropped me to a grub rescue prompt. I then tried booting from a LiveCD and selecting the "boot from first hard disk" option, which successfully took me to the grub menu, and I was able to boot an OS successfully.

Anyone else confirm?

---

### Post by ubername on 2009-12-08
Same here.

The message was 

error: the symbol 'grub_gettext' not found

leads to a prompt (grub rescue>)
Googling the error message gets some results which says 
[http://osdir.com/ml/debian-bugs-rc/2009-11/msg02604.html](http://osdir.com/ml/debian-bugs-rc/2009-11/msg02604.html)
'Hi,

There's no bug here. You installed different versions of GRUB to different
drives using the same /boot/grub/. One of them stopped booting because of
ABI incompatibility.'

Just tell the debconf template to install GRUB to each drive and you'll be ok.'

I don't know what debconf is our hpw to do this (may be Debian specific?)


I tried: (from live cd - I had to apt-get install grub) 
sudo grub
find /boot/grub/stage1

get error 15: file not found

yet if I look on the drive there is a /boot/grub folder

Apologies if the commands / error messages are not exact - I wrote them down but there might be the odd typo.

Can anyone help?

---

### Post by ubername on 2009-12-08
Should point out that this is trying to boot from a USB drive (lucid install) I can boot from Hard drive (from where I am posting)

---

