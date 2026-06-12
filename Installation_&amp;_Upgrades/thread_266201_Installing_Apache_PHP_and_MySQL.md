---
title: "Installing Apache PHP and MySQL"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-26
I've already installed Ubuntu 6.06 Desktop and dont know how to install Apache, PHP and MySQL. Hope you can guide me on this installation?

---

### Post by koshari on 2006-09-27
have you used synaptic package manager before?

as the programs you are seeking are all on there, 

# System -> Administration -> Synaptic Package Manager


then simply search for each of the programs you want and tell synaptic to install them, 

easy.

---

### Post by textguru on 2006-09-27
I cant find what I need on the Synaptic Manager. I also tried to search but found no apache. Any online instruction on how to do this?

---

### Post by textguru on 2006-09-27
I have found a link on this site:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service](http://ubuntuguide.org/wiki/Dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service)

But when I will try
 apt-get install apache2 on root's terminal window, i get this prompt:

Reading package list... Done
Building dependency tree... Done
E: Couldn't find package apache2

what does it mean?

---

### Post by koshari on 2006-09-27
you want these packages and they are in the repositorys, 

apache2-common

php5

mysql database server (current version)

---

### Post by koshari on 2006-09-27
if you cant find these you may have to update your sources list to give access to the multiverse and universe repositorys 

/etc/apt/sources.list

heres mine. (not you wont need the 4 lines at the bottom as they are for other softwares outside the official ubuntu repos.

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian) ./

---

### Post by TooRight on 2006-09-27
Check this page out... just scroll down for the apache.mysql.php etc stuff... it makes setting up a server as easy as a few copy and pastes!! :O

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

