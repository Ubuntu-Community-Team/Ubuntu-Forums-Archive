---
title: "ROOT passowrd.  It didnt ask me?"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-08-01
Hi guys..

I have a little prob, I installed Ubuntu, basically a stock install except i did the partitioning. It asked me for a username and password, but not to make a ROOT password.
I now cannot  log on as root, even with the log on password i set.

I was wondering i could just re-install but it never asked me to set a root PW in the first place? Is there a way to make one in Linux? Or where do i enter it when i install.

thanx..

---

### Post by jdodson on 2005-08-01
yes, when you install ubuntu the default user has sudo privs.  so you can set a root password by typing:

sudo su 

type in your user password.

and then type:

passwd

ubuntu defaults to sudo and not root.

---

### Post by adwait on 2005-08-01
Ubuntu by default doesn't have a root account. You can use sudo for all commands requiring root permissions.

---

### Post by grj on 2005-08-01
Ubuntu does not use root as other distributions. Try typing

sudo <command>
When prompted for a password, enter the current users password.

If you want su privileges:

sudo su
Then the password as above.

You can also open a root console from the menu.

---

### Post by kosmic on 2005-08-01
I think the best you can do now is read the Ubuntu  Guide - [http://ubuntuguide.org/](http://ubuntuguide.org/) , because Ubuntu doesn't use the root account it is deactivated in the begining, in ubuntu if you want to do administration task you use ( sudo ) instead.

---

