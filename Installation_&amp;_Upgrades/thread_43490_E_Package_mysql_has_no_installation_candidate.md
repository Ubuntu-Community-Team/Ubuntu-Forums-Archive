---
title: "E: Package mysql has no installation candidate"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by hq4ever on 2005-06-22
Hello, I've just installed ubuntu.

I'm trying to get my system up and running.
What I'm basicly do is php development so I need a good testing envirment on my laptop.

Here is my sources file:

>  # cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

I think is did some mess when I tried to install apache, somehow it installed me the worker process instead (didn't quite understood what happend there...).

anyhow, please give your opinion on this :
```

root@ubuntu:/home/hq4ever # apt-get install smeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg
root@ubuntu:/home/hq4ever # apt-get install mysql
Reading package lists... Done
Building dependency tree... Done
Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql has no installation candidate
root@ubuntu:/home/hq4ever # apt-get install httpd
Reading package lists... Done
Building dependency tree... Done
Package httpd is a virtual package provided by:
  apache2-mpm-worker 2.0.53-5ubuntu5.1
  apache2-mpm-prefork 2.0.53-5ubuntu5.1
  apache2-mpm-perchild 2.0.53-5ubuntu5.1
  thy 0.9.4-1
  thttpd 2.23beta1-2.5
  roxen3 3.3.63-6
  mzscheme 1:208-1
  mathopd 1.5p4-1
  fnord 1.8-4
  dhttpd 1.02a-11
  caudium 2:1.2.35-1ubuntu2
  bozohttpd 20030313-1
  boa 0.94.13-8
  apache-ssl 1.3.33-4
  apache-perl 1.3.33-4
  apache 1.3.33-4
  aolserver4 4.0.9-1
  aolserver 3.5.6-7
You should explicitly select one to install.
E: Package httpd has no installation candidate
```

Thank you.

---

### Post by afonic on 2005-06-22
Hmmm in your topic you say about mysql and in the logs about httpd?

Anyway try 

sudo apt-get install apache2

It should do the job.

For mysql

sudo apt-get install mysql-server

---

### Post by hq4ever on 2005-06-22
Ooops, sorry.

I was tring to get all the LAMP idea working on the laptop and nither the apache nor mysql worked.

Anyhow, thank you. 
Both mySQL & apache2 got installed just fine.

I would to continuy this thread for just a few more closly related questions (instead of opening a new one).

How can I search for packages ?
How to install apache-doc ?
How to install smeg ?```
# apt-get install smeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg
``` 
How to install php4 ?

Thank you for answering.

---

