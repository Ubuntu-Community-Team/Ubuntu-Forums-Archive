---
title: "Default web server in 10.04"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sebast on 2010-03-22
I tried to install XAMPP but when I run it and type 127.0.0.1 my browser, I don't get the content that is in my XAMPP's htdoc directory, but a page that says:

> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

It it possible that there is already a default web server installed in 10.04 that's running instead of XAMPP? Where should I put the files then?


Thanks a lot!

---

### Post by seeker5528 on 2010-03-24
Don't know about XAMPP, but if you install Apache from the repositories the directory for the web stuff is '/var/www/'.

Later, Seeker

---

### Post by cariboo on 2010-03-24
XAMPP gets installed in /opt, you may want to look in there for your htdocs directory. Also make sure /opt/etc/Apache2/sites-available/default points to the correct directory.

---

