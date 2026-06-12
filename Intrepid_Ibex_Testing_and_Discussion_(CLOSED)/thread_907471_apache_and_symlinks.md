---
title: "apache and symlinks"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-09-01
I just noticed that my symlinks don't show anymore in localhost.

Seems I lost/overwrote some config file during upgrading.

I added a Servername to httpd.conf to get rid of this new error
> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

but what do I have to do that my symlinks show and work again?

---

### Post by xerosis on 2008-09-01
You need the "Options FollowSymLinks" option in the corresponding Directory section.

---

### Post by excogitation on 2008-09-01
That's on by default in
/etc/apache2/sites-available/default

Might be because the folders the symlinks point to have wrong permissions (but I didn't change anything there).

---

