---
title: "beginner ubuntu ftp question"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Aphotic_13 on 2007-04-04
I was wondering how you enable ftp access in ubuntu 6.10? i have the kasablanca client installed right now, and can access other machines.  however how do i allow other machines to access me?

---

### Post by thelinuxguy on 2007-04-04
> **Aphotic_13 said:**
> however how do i allow other machines to access me?

Install an FTP server. I use PureFTP. It is available in the repo. You may also want PureAdmin - a GUI management tool for PureFTP.

---

### Post by Aphotic_13 on 2007-04-04
Thanks alot, i tested it and everything works great. I guess my lingering question involves doing this without downloading a program.  I understand that this is not secure, nor do I plan to run ftp this way. But just for my curiosity's sake, purely.  I know in freebsd for instance, you can do this running inetd by just uncommenting the lines in /etc/inetd.conf and rebooting. Any thoughts on ubuntu in this regard?

---

