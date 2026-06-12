---
title: "mysql error"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by malola123 on 2007-12-30
Hi,

I recently installed mysql database server on my linux ubuntu 7.10

When I try to access mysql through terminal, i get the following error:
[B]
root@Sriram:/usr/local# mysql -u -p
ERROR 1045 (28000): Access denied for user '-p'@'localhost' (using password: NO)[/B]

I am not too sure what this error means.  Plz help!

Also, is there was graphical inerface where i can open mysql and add a database?

Thanks!

---

### Post by tgilber1 on 2007-12-30
> **malola123 said:**
> Hi,

I recently installed mysql database server on my linux ubuntu 7.10

When I try to access mysql through terminal, i get the following error:
[B]
root@Sriram:/usr/local# mysql -u -p
ERROR 1045 (28000): Access denied for user '-p'@'localhost' (using password: NO)[/B]

I am not too sure what this error means.  Plz help!

Also, is there was graphical inerface where i can open mysql and add a database?

Thanks!

msyql -u <username> -p <password> # e.g., mysql -u johndoe -p abc123

you must populate a username after the u flag and the password after the p flag

The error message states that mysql denied username -p without a password.

---

