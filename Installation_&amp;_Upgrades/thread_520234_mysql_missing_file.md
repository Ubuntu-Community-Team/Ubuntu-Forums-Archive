---
title: "mysql? missing file"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by drewsmug on 2007-08-07
i have the fiesty something version of ubuntu

i have succesfully installed apache2 and php using this tutorial
file:///home/drewsmug/Desktop/enoph%2076.27.220.26/lamp.htm

i ever get all the way through the mysql steps on said tutorial.  i like it
but then i tried to setup a phpbb forum.

will one of the first steps is

mysql -u root

this is my problem
i cant get in.  this is my error

ERROR 1045: Access denied for user: 'root@localhost' (Using 
password: NO)

i found this tutorial to supposedly fix this.
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

but when i run the following command it says no such file or directory

/usr/bin/mysqld --skip-grant-tables --user=root

i did look for a file called mysqld in /usr/bin and it does in fact not exist.
i searched for other tutorials or help sites but came up with nothing.
i dont know if just sticking a file in there will help or what.

also i assume its the latest mysql.

i just use the sudo get-apt install mysql-server command
maybe i dont have the client or something.
anyways im new and clueless.  any help please.
thanks in advance.

---

### Post by Wim Sturkenboom on 2007-08-08
[http://ubuntuforums.org/showthread.php?t=27156](http://ubuntuforums.org/showthread.php?t=27156) might be of interest, specifically post #12 on the second page.

---

