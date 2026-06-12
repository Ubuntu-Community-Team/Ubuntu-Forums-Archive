---
title: "Problem installing LAMP"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by johnmackin on 2006-08-22
I just installed Ubuntu desktop and wanted to install a web development environment. When I try to install the pacages for Apache/PHP/MySQL for the GUI i get error messages. The firs screen asks to "Mark additional required changes" and lists libapr0. After selecting Mark, I get an error messages telling me that various dependent packages(files?) are "not installable" or "not going to be installed.

What does this mean and how do I get the environment installed?

Thanks,

John M.

---

### Post by johnmackin on 2006-08-23
I wound up figuring this out myself. It seems that the default Ubuntu intallation had no software channels selected in software preferences. After selecting appropriate channels the applications installed.

My first experience with Ubuntu has not been great. This information was not contained in the Desktop Guide (Read this First) but got to it through the Common Questions page. I was also not overwhelmed by community response to my new user question. It seems several new user questions in the forum go unanswered.

The forum site is excruitiating to use. Very slow to load pages (sometimes minutes on searches)and frequent time outs. 

John M.

---

### Post by az on 2006-08-23
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You probably are asking it to install a few things that are not in main.

The main repo is activated by default:  You should be able to install 
apache2 php5-mysql libapache2-mod-php5 mysql-server

which are what youneed to run LAMP.

Also, you must be online to fetch packages from the net.

As well, be sure to have the security-updates repos active, too.  They too should be on by default.  Perhaps a package is no longer in the main archive but in security because of a fixed vulnerability.

---

### Post by h0mer on 2006-08-23
too bad your first experience hasn't been that great. I have found these forums to be really lifesavers... but you are probably right in that there should be more straightforward help for newbies. The Ubuntu Wiki is getting there, though, with new ideas like the Classroom for this kind of situations.  The forums though are a wealth of info when searched properly. At least, your solution will now help others in similar situations!:D

---

### Post by johnmackin on 2006-08-24
Thanks for the replies! I seem to be up and running now.

---

