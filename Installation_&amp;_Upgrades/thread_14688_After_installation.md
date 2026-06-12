---
title: "After installation"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by StIcK on 2005-02-09
Ola

I've now installed Ubuntu distribution :)
But there's on thing i cannot understand : during the installation i never had to enter the root password. Now i m as an user but not the root one. When i enter su in the shell i have to enter the root password, and of course i haven't it !

So now what can i do to ?

i know i can edit the password file with some manipulation, but i think that's the wrong way with a fresh install, do i ?

please help

---

### Post by Wim Sturkenboom on 2005-02-09
Ubuntu uses sudo. This allows certain users to execute programs that are usually only allowed for the root user. I personally don't like this approach (I'm used to a root password) but most people seem to forget a root password if they don't use it regularly). It will ask you to enter **your** password.

You can (under gnome) open a root terminal.


You can set a root password with the following command.
```
sudo passwd root
```Once you've entered the password, a normal root user is available.

---

### Post by StIcK on 2005-02-09
thanks i undersand now the difference between sudo and root.

it's a nice distribution and got the avantage to integer all the Debian package  8)

---

