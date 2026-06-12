---
title: "Root Password"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by cairnsys on 2005-11-25
Hello all

First post to the forum after a reasonably straightforward install!

However, now that I've got a working system I want to add more software to it and need the root (or su) password.  I cannot recall seeing it, setting it or changing anywhere during the installation.

Does anyone know the default root password for a Ubuntu instllation pleasE?

Best wishes

Robin

---

### Post by taurus on 2005-11-25
You need to create one like

sudo passwd root
(your logins password)
(root password)
(retype root password)

However, you can run or install pretty much everything with the "sudo" command...

---

### Post by frodon on 2005-11-25
There no root account by default in in ubuntu and it's not needed.
You can do all the root thing using "sudo", type "sudo" before each command you want to launch as root, and "gksudo" if you want to launch a GUI apps as root. By default the password for "sudo" is your user password but you can change that if you want.
If you want to become root in a terminal use the "sudo su" command.

---

### Post by cairnsys on 2005-11-25
Thanks Taurus, worked that one out for myself before your reply!!  Not bad for a newbie!!

---

### Post by taurus on 2005-11-25
[QUOTE=cairnsys]Thanks Taurus, worked that one out for myself before your reply!!  Not bad for a newbie!![/QUOTE]
Hey, you just have to spend some time playing around with it; that's how you learn it...  Have fun.

---

### Post by peanut butter on 2005-11-25
you should try easy ubuntu or automatix to get multimedia codecs ect.:)

---

### Post by earobinson on 2005-11-25
love the sig peanut butter

---

