---
title: "installing phpmyadmin with no internet"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by vitor4 on 2014-03-19
Hi,
I have installed ubuntu server and LAMP on it.
Now I have to install phpmyadmin so I can configure my database. The thing is, I don't have Internet access on this server so I can't download the packages required.
So I googled phpmyadmin package and I've downloaded this one: [http://packages.ubuntu.com/lucid/phpmyadmin](http://packages.ubuntu.com/lucid/phpmyadmin)
I've put that file on my server and did the following command: sudo dpkg -i phpmyadminpackage.deb, but it gives me an error saying that package has a list of the following depencies:
phpmyadmin depends on php5mcrypt; however: packacge php5-mycyprt is not configured yet.
phpmyadmin depends on dbconfig-common; however: packacge dbconfig-common is not configured yet.
(...)
and the list goes on.

Now, the thing is that those depencies packages have other dependecies themselves >_>

How can I just download a single package with all the dependecies of phpmyadmin, and afterwards install it?

Thank you in advance.

---

### Post by vitor4 on 2014-03-19
bump

---

