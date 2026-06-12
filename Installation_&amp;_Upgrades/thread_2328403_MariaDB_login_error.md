---
title: "MariaDB login error"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by angela8 on 2016-06-20
I just set up a new home server with Ubuntu Server 16.04 last weekend and I'm attempting to get mariadb up and running (version 10.0.25).  Here's what I did:

[LIST=1]
[*]Connect to server via SSH
[*]Followed the directions to install mariadb here: [https://downloads.mariadb.org/mariadb/repositories/#mirror=digitalocean-sfo&distro=Ubuntu&distro_release=xenial--ubuntu_xenial&version=10.0](https://downloads.mariadb.org/mariadb/repositories/#mirror=digitalocean-sfo&distro=Ubuntu&distro_release=xenial--ubuntu_xenial&version=10.0)
[*]Ran mysql_secure_installation (including setting a root password)
[*]Logged in to mysql as root: ```
mysql -u root -p
``` and entered root password.
[*]Created a new user (for the sake of example, let's call it PERSON with password PASSWORD) using the command: ```
CREATE USER 'PERSON'@'localhost' IDENTIFIED BY 'PASSWORD';
```
[*]Gave the user privileges on a test database and flushed privileges: ```
GRANT ALL ON test.* TO 'PERSON'@'localhost'; FLUSH PRIVILEGES;
```
[*]Quit mariadb and tried to log in as PERSON: ```
mysql -u PERSON -p
```
[*]Entered PASSWORD when prompted.
[*]Received this error: ```
ERROR 1045 (28000): Access denied for user 'PERSON'@'localhost' (using password: YES)
```
[*]Googled this error for hours with no luck.
[*]Elevated the privileges of PERSON to see if giving them root-like privileges solved the problem since the root user is working fine: ```
GRANT ALL ON *.* TO 'PERSON'@'localhost'; FLUSH PRIVILEGES;
```
[*]Still no luck logging in. (Same error.)
[*]Restarted the mysql process.
[*]Still no luck logging in. (Same error.)
[/LIST]

My guess is that it could be related to firewall settings, or other network settings outside of mariadb, but I'm seriously stumped.  And I'm not going to use root for everything, obviously, even though that user works perfectly fine.  Can anyone help?

Thanks,
AB

---

