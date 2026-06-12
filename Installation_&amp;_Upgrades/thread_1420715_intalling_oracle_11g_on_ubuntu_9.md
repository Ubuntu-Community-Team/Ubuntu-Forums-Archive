---
title: "intalling oracle 11g on ubuntu 9"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by gopal1626 on 2010-03-03
can anybody help me how to install oracle on ubuntu? i have searched in many sites but i didn't get the solutions,due to this i have installed n uninstalled ubuntu.
please anybody help me i badly require oracle.

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

You can install Oracle Database XE Server in Ubuntu using these instructions.

**Note:** Doing these would **NOT** install oracle 11g. It installs only Oracle 10. Installing the default oracle-xe is quite straightforward and easy. Installing 11g is different. But I've also included links to pages that have instruction on how to install 11g on linux. Hope you find them useful.

Open your /etc/apt/sources.list file
```
$ sudo nano /etc/apt/sources.list
```
Append the following line
```
deb http://oss.oracle.com/debian unstable main non-free
```

Save and close the file and add the GPG key. To do that execute the following lines in the terminal one after the other
```
$ sudo wget http://oss.oracle.com/el4/RPM-GPG-KEY-oracle -O- | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install oracle-xe
```
Then configure Oracle using this command
```
$ sudo /etc/init.d/oracle-xe configure
```
When you are prompted to specify HTTP port, simply press enter to select the default port ( which is 8080 )

When you are prompted to select the port that listens to the db again press enter to select the default port ( port 1521 )

When it asks for a password give a password of your choice. Confirm it by entering it again.

Let the installer complete the configuration.

To access the Database Home Page go to [http://localhost:8080/apex](http://localhost:8080/apex) in the browser. The username is 'system'. Password is the one that you set.

These steps were taken from this link: [http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/](http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/)

This link correspond to Intrepid Ibex. But it should work on Ubuntu Karmic too. (**Oracle 11g**) [http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/](http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/)
Generic Help: [http://mediakey.dk/~cc/ubuntu-howto-install-oracle/](http://mediakey.dk/~cc/ubuntu-howto-install-oracle/)

**More help:**
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

Download link for **oracle images** here: [http://www.oracle.com/technology/software/products/database/index.html](http://www.oracle.com/technology/software/products/database/index.html)

HTH

---

