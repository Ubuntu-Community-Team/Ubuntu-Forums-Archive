---
title: "Installing Moodle"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by swu on 2006-09-12
I'd like to install Moodle on my new 6.06 server box. I installed it as a LAMP box. When I do apt-get install moodle - it can't find the package.

I think I have downloaded the correct package from packages.ubuntu.com. Now what? Where do I put the package on the server itself? Do I still use apt-get to do the install? Will the package contain all the dependancies?

Thx again for all the help!

---

### Post by croak77 on 2006-09-12
First check your /etc/apt/sources/list. moodle is in universe. Make sure you have it enabled.

If you downloaded it, you can use dpkg to install.
```
 sudo dpkg -i /path/to/moddle.deb
```

It will not contain dependancies. That's why you should try to fix your sources.list first.

---

