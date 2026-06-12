---
title: "preventing upgrades from reconfiguring rc.d links"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by simon_w on 2010-04-27
I have a laptop system that I do a lot of development and other kinds of work on.  I have a lot of different packages installed, including a great many that run as services.  Since I use most of them only occasionally, after installing them I generally remove the rc-d configuration ```
sudo update-rc.d -f <package> remove
``` and then I start them manually as I need them.

For example, my system has MySQL and PostgreSQL installed, as well as an OpenSSH server, Apache, Tomcat, polipo etc. etc., and I don't need or want any of these to start every time I boot my laptop.  They constitute unnecessary load and security risks if all I'm doing is browsing the web in a coffee shop.

My problem is that every time one of these packages is upgraded, the rc.d links are recreated, without even a notice, let alone a request for permission.  I find this really annoying!  Does anyone know a way to deal with this?

Grateful for any solutions or suggestions :)

---

