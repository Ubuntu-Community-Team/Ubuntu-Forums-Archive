---
title: "installing server edition"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-09
Hi,
I have desktop version installed and working perfect. How can I upgrate to server version. Is server version having all facilities included in desktop?
thanks

---

### Post by lkagan on 2006-06-09
I'm not sure of all the differences.  However, the main differences are probably that server does not have a gui desktop or any gui tools  but does have server services such as postfix, apache, samba, etc...  These can of course be customized.   If you plan on using a browser, email, office software, you don't want the server.  However, if you're like me and have a computer at home that you actually work on and serve a website from, you can have everything in one machine by using the Synaptic package manager to install those server software packages or if you want more of a server feel, use apt-get from the command line.

Larry

---

### Post by vasimakhtar on 2006-06-09
Thanks. It was very useful info. My purpose is to install MYSQL on home PC to learn more about. How can I do that in desktop version to install MYSQL and create databases.

---

### Post by lkagan on 2006-06-09
sudo apt-get install mysql-server mysql-client mysql-admin mysql-query-browser

Of course you can find all these by using the Synaptic package manager but the above directions are easier for me to type. :)

To create databases you should know SQL and use the MySQL Query Browser.  At this point I'll have to difer you to the [MySQL forums]("http://forums.mysql.com/").  But there are tons of tutorials on the web.  Note that you will have two ways of entering in data into mysql.  1) From the command line by first typing mysql -u root and 2) by using the MySQL Query Browser (in your menu after installation).   By the way, Ubuntu is now an offically supported Linux distribution for MySQL by MySQL AB.

Good luck

Larry

---

### Post by vasimakhtar on 2006-06-09
Thanks Larry. I appreciate your reply. I will try for that.
Best Wishes.

---

