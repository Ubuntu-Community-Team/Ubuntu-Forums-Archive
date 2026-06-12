---
title: "SUDO doesn't work."
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by Bougle on 2005-05-08
Help. Please.

The first thing I wanted to do on installing Ubuntu was to get my usb adsl modem working. I'd previously downloaded the drivers onto my XP installation so tried to edit fstab. No joy it was ro. So a quick visit trip to the forums with XP and I was back trying to rum the application "gksudo gedit". Nothing, nada, a complete blank. In fact nothing happens when I try to access any applications using that method or indeed any applications that require sudo access. Whats going on! If anyone can help I'd be very grateful.

---

### Post by dave9191 on 2005-05-08
at a terminal type 

sudo gedit

I prefer to use nano for editing config files (sudo nano filename). 

Dave

---

### Post by Bougle on 2005-05-08
When I use *sudo gedit* I get the response:

*Sudo: unable to look up ubuntu via gethostbyname(). Password: postdrop: warning: unable to look up public/pickup. No such file or directory.* 

Any ideas? ](*,)

---

### Post by dave9191 on 2005-05-08
:-s err..... looks like your sudo is messed up. And I dont know enought about it to help, sorry.

---

### Post by Bougle on 2005-05-08
Its OK I got it now.

Booted from a live distro and edited /etc/hosts. That fixed it. Phew \\:D/

---

### Post by dave9191 on 2005-05-08
cool  \\:D/

---

