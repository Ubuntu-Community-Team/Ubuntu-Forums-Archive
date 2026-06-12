---
title: "Mysql refuses to install and work on Ubuntu"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by pfbroome on 2007-10-16
Greetings all,

I have been working on this problem for a while now and frankly, I"m stumped.  Situation is this; Just finished an install of server 7.0.4. During installation I loaded the bare minimum.  Now that the server is up and running I want to install the required packages. In my case, the first such package is MySql.

Sooo, I fire up apt-get mysql-client mysql-server ...which it handles without errors. I then edit the /etc/mysql/my.cnf file to comment out the 127.0.0... bind. Stop & restart MySql.  From what I can find, the next step is to enter "mysql_install_db" to set up the grant tables and (presumably) the initial ropot account. WHen I do that I get:

root@ubuntu01:/home# mysql_install_db
Installing MySQL system tables...
ERROR: 1062  Duplicate entry '%-test-' for key 1
071016 11:54:56 [ERROR] Aborting

071016 11:54:56 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

Examine the logs in /var/lib/mysql for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:

shell> /usr/bin/mysql -u root mysql
mysql> show tables

Try 'mysqld --help' if you have problems with paths. Using --log
gives you a log in /var/lib/mysql that may be helpful.

The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Please consult the MySQL manual section: 'Problems running mysql_install_db',
and the manual section that describes problems on your OS.
Another information source is the MySQL email archive.
Please check all of the above before mailing us!
And if you do mail us, you MUST use the /usr/bin/mysqlbug script!

...Sadly, no, there are no log files in /var/lib/mysql (some binaries but nothing helpful)

Well, if at first you don't succeed, try something else.  Next   I try to set the password for the root account. I am doing this from a terminal into the Ubuntu server but the console gives me the same results. I fire up the mysqladmin tool to set the root password and this is what I get:

root@ubuntu01:/# mysqladmin -u root password pass12345
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

No matter what I try it appears that the root user was never set up in MySQL during install and, as such, I have no way in to in to fix it.

Logic dictates that I MUST be doing something wrong; This CAN'T be a common problem.  But therein lies my problem-I don't have a clue as to what I have messed up/didn't do. I have looked around the disk for some kind of post install scripts. 

I am stuck!.. any and all help will be greatly appreciated.

Thanks,

Pete

---

### Post by paul.drover on 2007-10-16
> **pfbroome said:**
> Greetings all,

...
I then edit the /etc/mysql/my.cnf file to comment out the 127.0.0... bind. Stop & restart MySql. 
...
Pete

Are you not supposed to supply a new IP in the my.cnf file? I'm new to this too and I've gotten to this point in the MySQL install and not known what to put there. I reason that my IP is dynamically allocated by my service provider so that changes each time I boot. But then again, that's actually my router IP. Behind that, I think I've a static address (that I'd have to look up) set by my router. If I do a ping <hostname> (essentially a ping of myself) it should deliver the IP, no? Perhaps that's what I have to do. Anyone more knowledgeable about MySQL care to elaborate? The install instructions are a bit flimsy on this point.
Cheers,
Paul.

---

### Post by az on 2007-10-16
> **pfbroome said:**
> From what I can find, the next step is to enter "mysql_install_db" to set up the grant tables and (presumably) the initial ropot account. WHen I do that I get:


You don't need to do that.

See: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

See [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset) about reseting your root password

---

### Post by pfbroome on 2007-10-17
Greetings all,

OK, things are working.  While I remember what all I did to make it work I want to document it so when someone else runs into this problem, they have a working solution available.

Situation; I have installed mysql-client, mysql-server and mysql-common via "sudo apt-get install......"  Once that finished, I went into mysql and established a root password via the methods described in this article: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset).

Once I had a password, I went into mysql as root (i.e. >mysql -u root -p) This prompted for a password (interestingly, putting the password in as an argument didn't work-Kept saying root@localhost had no access or something to that effect.)

When I reached the prompt (mysql>) I did a USE mysql; to get the right db and then I inserted several users/host/passwords in the user table as follows:

INSERT INTO [table name] (Host,User,Password) VALUES('%','user',PASSWORD('password'));

For instance, if I want to insert user "Bob" from the host "MyBox" with password of "tt123456" then I entered;

INSERT INTO user  (Host,User,Password) VALUES('MyBox','Bob',PASSWORD('tt123456'));

I added all the basic accounts/users; at least enough to get access via a better tool like SQLyog.  I finished everything with a FLUSH PRIVILEGES; (just to be sure) and then I changed the "bind-address" in the my.cnf file to be the IP of the machine running the mysql server process.  If, for instance, I had mysql running on 192.168.25.50 then I changed the bind line in /etc/mysql/my.cnf as shown below:

bind-address            =192.168.25.50


And that's what made it work for me.  I hope this will be useful for others.  I also discovered a nice, "cheat sheet" for critical MySQL commands at:

[http://www.pantz.org/database/mysql/mysqlcommands.shtml](http://www.pantz.org/database/mysql/mysqlcommands.shtml)


That's it. Thanks to everyone for their help


Pete

---

