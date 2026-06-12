---
title: "Problem installing/running sendmail"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by ccheaton on 2006-08-21
Hi, I'm trying to install and run sendmail on my fresh Ubuntu install.  I selected it for install through the 'Add/Remove Programs...' advanced menu.  It found dependencies, installed, etc...

Now, on startup, I get a pause and a few error messages.  The first is that it cannot remove
/etc/mail/sendmail.cf

and the second is that a directory is read only, so that
/usr/share/sendmail/update_auto: line 98
cannot create a temp file

It then says that I should restart sendmail.  How do I fix this problem?  (As you can tell, I'm a Linux noob.)

---

### Post by wpshooter on 2006-08-21
What are you trying to do ?

Are you trying to setup and configure an e-mail program ?

---

### Post by ccheaton on 2006-08-21
No, I've set up a LAMP server so I can do web work locally and I want PHP to be able to call sendmail.

---

### Post by Tyler Oderkirk on 2006-08-30
This might help...

[http://ubuntuos.wordpress.com/2006/07/31/howto-ubuntu-sendmail-boot-error/](http://ubuntuos.wordpress.com/2006/07/31/howto-ubuntu-sendmail-boot-error/)

---

