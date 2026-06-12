---
title: "Unable to find mysql-admin package to install..."
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by sean talbert on 2006-06-24
I'm unable to find the mysql-admin package to install. I've tried "sudo apt-get install mysql-admin", looked through dselect and Synaptic. 

I even downloaded the .rpm from mysql.com, converted it to a .deb package using alien, installed using gdebi package installer where it put it in /usr/share, but when I try to run it, I get a lot of "..GLib-GObject-CRITICAL **: g_type_register_static: assertion..." messages. How do I uninstall this?

I read that if you installed it using apt-get, MySQL Admin was put in the Administration menu... I'd really appreciate some help getting that setup.

Thanks.

---

### Post by tonyr on 2006-06-24
What repositories are you using? The **gb** repos seem to be having problems at
the moment.  Examine **/etc/apt/sources.list** and look for things that say
**gb.archive.ubuntu.com**.  It might not say **gb**.  Try one of the other
repo sites: **eu** **us** **ca**.

---

### Post by tonyr on 2006-06-24
I installed it using the **us** repositories (us.archive.ubuntu.com).  It showed up
under **Applications->System Tools**

---

### Post by sean talbert on 2006-06-24
My sources.list has:

deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

Maybe if I added the Ubuntu-Desktop cdrom?

---

### Post by tonyr on 2006-06-24
Once installed by **gdebi** you should be able to remove it with any of regular
command line package managers: a**pt-get**, **dselect**, **dpkg**, **aptitude**.

**mysql** and it's relatives may live in the **universe** or **multiverse** repositories.  Add **universe** and **multiverse** to the end of the two 
**dapper main restricted** lines, update your packages DB either in Synaptic
or in a terminal with** sudo apt-get update**, and try the install again.

---

### Post by sean talbert on 2006-06-24
That got it:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 

And I was able to unistall using Synaptic. 

Thanks for your help!

---

