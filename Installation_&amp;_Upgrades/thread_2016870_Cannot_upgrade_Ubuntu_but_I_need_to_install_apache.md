---
title: "Cannot upgrade Ubuntu but I need to install apache"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2012-07-04
I need to install apache2 on a Ubuntu 9.10 system. Yes, 9.10 is no longer supported.

I am not allowed to upgrade this system because the system has some custom applications running on it.  These applications have been running without any problems for a few years.

Is it still possible to install apache2 here?

---

### Post by cipherboy_loc on 2012-07-04
Look into compiling apache from source, using the latest apache version. This will be more secure than running an older .deb if you can find one, though it will take more time.

Cipherboy

---

### Post by SeijiSensei on 2012-07-04
If you do decide to compile from source, make sure you do an inventory of other software that your applications might require, like PHP, Ruby, or Python.

---

### Post by azmyth on 2012-07-04
Wouldn't apache2 be on the install CD?

---

