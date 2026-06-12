---
title: "File /etc/sudoers not pre-edited"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by brunogabuzomeu on 2005-04-18
Hellow,

  I downloaded the 05.04 version and installed it on a completely cleared computer.

  During the installation, I was asked for the root password.

  The users are not declared in /etc/sudoers and I can't use the applications from the gnome administrator menu: gksu asks me for my password and then crashes with the message in .xsessions-error that user is not declared in sudoers file.

  Can anyone help me ?

  Thank you

  Bruno

---

### Post by TravisNewman on 2005-04-18
What DOES your /etc/sudoers file look like?

---

### Post by junkie on 2005-04-18
10 seconds ago i had the same issue on my brand new Ubuntu Box. I used to use Debian before so i am new to this distro.

I edited sudoers

root@trashbin# pico /etc/sudoers

and than added the line

junkie  ALL=(ALL) ALL

than everything worked fine for me..

---

### Post by az on 2005-04-18
If you need to, boot into recovery mode to become root without a password...

---

### Post by brunogabuzomeu on 2005-04-18
[QUOTE=panickedthumb]What DOES your /etc/sudoers file look like?[/QUOTE]

  It is virgin: standard explanation comments and as the last line:

root ALL=(ALL) ALL

Of course I could add

bruno ALL=(ALL) ALL

But I don't think it is the best solution for security reasons... I added the users during the installation process.

  Isn't it strange that I was asked for a root password ?

---

