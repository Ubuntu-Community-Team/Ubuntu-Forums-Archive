---
title: "mysql-server-5.1 broken but synaptic wont remove"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by linuxNewb on 2009-12-20
I tried installing the LAMP stack using:
 sudo apt-get install lamp-server^

I got an error when it got to mysql-server-5.1 so I tried reinstalling it using synaptic. It's still broken and marked for removal, but synaptic won't let me unmark it. When I hit Apply I get the following error:

E: mysql-server-5.1: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

What do I need to do to fix it, or remove it, I just want to MOVE ON. Thanks in advance.

Edit: Um, after rebooting, I was able to Apply an Upgrade :confused: It is now working.

---

### Post by phillw on 2009-12-20
Hi,

Glad you got it sorted. As ever - the hint is in the error message

>  E: mysql-server-5.1: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Having had a MySQL go poorly on me - doing the re-instal also healed mine & i lost no data (I had backed it up).

You will sometimes see messages like this - Doing as they tell you sorts out most problems, Linux is very good at taking a 'best bet' to heal itself when a 'funnie' occurs.

Regards,

Phill.

---

