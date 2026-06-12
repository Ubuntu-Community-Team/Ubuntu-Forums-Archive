---
title: "Installing SSL for Apache2"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by aplonis on 2010-04-18
Sometime ago I got Apache2 working. I also did my best to enable it for SSL, but failed. I'd like to give that another go. I have OpenSSL installed and all (or so Karmic reports). But port 443 gives an error when I try to connect.

The server in question is here..

[https://starling.ws](https://starling.ws)

...where you can see the error.

Enlightenment please?

---

### Post by aplonis on 2010-04-18
After scratching the old noggin for a few hours and just browsing my config files, I discovered the problem was that did not have a soft link in the directory sites-enabled pointing to the appropriate file in the directory sites-available. So it was "available" but not "enabled" when I would restart Apache2

cd /etc/apache2
sudo ln -s sites-available/ssl sites-enabled/ssl
ls -l sites-enabled
total 0
lrwxrwxrwx 1 root root 26 2009-12-27 13:24 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 22 2010-04-18 10:17 ssl -> ../sites-available/ssl
sudo apache2ctl restart

---

