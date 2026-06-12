---
title: "ubuntu-base missing"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by diezare on 2006-07-03
Hello,

I was updating from ubuntu 5.10 to ubuntu 6.0 through the "Update Manager" and it gave me an error stating that ubuntu-base is missing. So, I tried to install it through apt-get but it gave me the following error.

[COLOR="Red"]user@system:~$ sudo apt-get install ubuntu-base
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-base[/COLOR]

And I tried to google how to get this package, but I found nothing usefull. Can anyone help?

---

### Post by Jagot on 2006-07-03
Try sudo apt-get update first and see if it works then.

---

### Post by diezare on 2006-07-03
Oh! thanks it worked now. :)

---

