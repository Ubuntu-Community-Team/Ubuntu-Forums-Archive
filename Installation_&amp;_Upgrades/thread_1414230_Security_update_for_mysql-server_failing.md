---
title: "Security update for mysql-server failing"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by col48 on 2010-02-23
I am getting an error message from Synaptic which is preventing a couple of security updates from installing for
mysql-server
mysql-server-5.0

The updates appeared within the last week.

The errors I get are

E: /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.5_all.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.5_i386.deb: subprocess new pre-removal script returned error exit status 1

Can anyone help?

(Ubuntu 8.04 Hardy)

---

### Post by col48 on 2010-02-26
Anyone??

---

### Post by odalcet on 2010-11-19
I'm using Ubuntu 8 in an old Toshiba laptop with memory problems. The error message appeared 2 weeks ago but I found a solution just today:

Go to mysql

[FONT="Courier New"]mysql -u yoyo -p[/FONT]
(enter password)

(now you are in mysql)

my upgrade script said there was a problem with user 'debian-sys-maint'

so I deleted that user:
[FONT="Courier New"]
DROP USER 'debian-sys-maint'@'localhost';[/FONT]

Then I created that user again with privileges

[FONT="Courier New"]CREATE USER 'debian-sys-maint'@'localhost' IDENTIFIED BY 'xxxxxxxxxxxxxxxx';

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' WITH GRANT OPTION;

FLUSH PRIVILEGES;
[/FONT]

... and my upgrade finally worked!!!

There is some information (the password) in this file:

/etc/mysql/debian.cnf

Change above instructions (the 'xxxxxxxxxxxxxxx's) and replace it with the password in debian.cnf

---

