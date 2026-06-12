---
title: "automate install of mysql-server"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by shl0m0 on 2008-11-14
In order to install mysql-server I do this:
```
sudo apt-get install -y mysql-server
```
But, the installation process pops up a blue dialog asking for a root password.

I need to completely automate the installation of mysql-server.

This post on the Forum Archives has a solution, but it didn't work:

[http://ubuntuforums.org/archive/index.php/t-677482.html](http://ubuntuforums.org/archive/index.php/t-677482.html)

It was a good start, though. Here is what I needed to do in order to prevent the prompt from happening:

```
echo "mysql-server mysql-server/root_password select (password omitted)" | debconf-set-selections
echo "mysql-server mysql-server/root_password_again select (password omitted)" | debconf-set-selections
```

I put those lines in my setup script and then the mysql-server installation doesn't prompt for a root password.

---

### Post by webmasteroy on 2009-12-25
That worked perfectly, to clear up any confusion others may have...  The lines he provided should be placed right above your apt-get install command for MySQL, within the bash script you are using to automate the process.

---

### Post by shadowlemon on 2010-12-04
it does work indeed like expected; however what is the password when this is installed? it's not blank, and neither is it one of the default passwords one might expect.

---

### Post by arunncce2089 on 2011-12-02
The correct commands are

echo "mysql-server-5.1 mysql-server/root_password password your_mysql_root_password" | debconf-set-selections
echo "mysql-server-5.1 mysql-server/root_password_again password your_mysql_root_password" | debconf-set-selections
sudo apt-get -y install mysql-server-5.1

---

