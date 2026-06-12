---
title: "Trying to install torrentflux but I get an error"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by tee2 on 2006-11-29
I get this error when trying to install torrentflux on my ubuntu edgy box

[[IMG]http://img81.imageshack.us/img81/4539/errorns9.png[/IMG]](http://imageshack.us)

edit: sorry is this the right sub-forum for this? :o

---

### Post by Dr_Dooom33 on 2006-12-28
Yea Im getting the same thing. I have looked at the Torrentlux forum ALL 40+ pages for a solution. I looked at linuxforums to no avail. And even here to no Avail](*,) 

lots of browsers and no replies. This is really selfish. Please help if you know something. In the mean time try this

sudo /etc/init.d/mysql stop
sudo /usr/bin/mysqld_safe --skip-grant-tables --user=root

---

