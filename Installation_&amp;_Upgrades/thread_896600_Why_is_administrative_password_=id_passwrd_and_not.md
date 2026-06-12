---
title: "Why is administrative password =id passwrd and not root's ???"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-08-21
I have just changed my root's password to not be the same as my main ID (one created at install time) because I believe those two should have different passwords.

But when I started the package update download, on the question of the administrative password, I had entered the root's password and it rejected it. It only accepted the main ID's password.

Why ????

This does not make sense. In all Unix systems and Linux system, all administrative autorization should be done via the root id and have a password of its own.

Why is that procedure established through all Ubuntu's process and installation process ???

It can cause security risks. Lets say someone uses my Ubuntu and because I didn't created a new id and put my trust into that someone, that something gets messed up because he/she entered my id's password on one administratove pannel to process a high level command ????

---

### Post by meindian523 on 2008-08-21
That's called stupidity because you never hand over admin passwords when you aren't sure whether they know enough to avoid commands which can trash your system.You would be better off creating a new account,it takes under 5 minutes.
Also read:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ilrudie on 2008-08-21
Root does not have a password in Ubuntu (effectively disabling the root account).  The "admin" password works like sudo and is just the users password.  You can create users who don't have sudo/admin access.  Remove the root password and create unprivileged accounts for those who should not have root access.

---

### Post by maybeway36 on 2008-08-21
Ib Ubuntu, **you have to protect your user password as you would the root password.** Ubuntu 8.10 will ship with a "guest account"; until then, you can make one yourself if needed.

---

### Post by snowpine on 2008-08-21
Hi Browser Ice, you have stumbled upon one of the big differences between Ubuntu and other Linux distros. I can assure you it is a conscious security decision, not a bug or flaw. :) Check out the link in meindian523's post for more information. You can, of course, choose a different security model if you don't like Ubuntu's default, because Linux is all about freedom and choice. :)

---

### Post by Vivaldi Gloria on 2008-08-21
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

