---
title: "Installation package python failed"
date: 2024-04-27
forum: Installation &amp; Upgrades
---

### Post by mikevaz216 on 2024-04-27
Hi, im a student and im doing a webpage through AWS academy, and i counter this problem, what i did it was just launching the instance, then opening cmd, tried to get everything right for my site (using LAMP and Kod Explorer) then trying to get everything installed i got this error, can anyone help me? (i go a similar error a few hours ago (Installation package xz-utils, it got fixed by launching another instance on AWS academy))

------------------------- Install Overview --------------------------


Apache: httpd-2.4.59
Apache Location: /usr/local/apache
Apache Additional Modules: do_not_install


Database: mysql-8.0.36
MySQL Location: /usr/local/mysql
MySQL Data Location: /usr/local/mysql/data
MySQL Root Password: prepa123


Database Management Modules:
phpMyAdmin-5.2.1-all-languages


PHP: php-8.2.18
PHP Location: /usr/local/php
PHP Additional Extensions: do_not_install


KodExplorer: kodfile-4.52
KodExplorer Location: /data/www/default/kod


---------------------------------------------------------------------


Press any key to start...or Press Ctrl+C to cancel


Installing development tools...
Installing package xz-utils
Installing package tar
Installing package gcc
Installing package g++
Installing package make
Installing package wget
Installing package perl
Installing package curl
Installing package bzip2
Installing package libreadline-dev
Installing package net-tools
Installing package cron
Installing package ca-certificates
Installing package ntpdate
Installing package python


+------------------+
|  ERROR DETECTED  |
+------------------+
Installation package python failed.
The Full Log is available at /home/ubuntu/lamp/lamp/lamp/lamp/lamp.log
Please visit website: [https://lamp.sh/faq.html](https://lamp.sh/faq.html) for help

---

### Post by TheFu on 2024-04-29
All of this looks extremely customized for how AWS academy wants it. It isn't the way that an Ubuntu Admin would do it, however.

I've been a UNIX, Unix, and Linux admin since the early 1990s.  Around 2000, I stopped installing stuff from source and started using packages - from the repos.  If I absolutely needed a newer version of anything specific, then I'd use the PPA.  Source code is the absolute LAST way I'd install any services/servers unless it was the only thing to be installed on that specific system. I'd strive to ensure everything around it, all other dependencies, were NOT installed from source.  Maintaining source code installs is just too hard.  By using repos and PPAs, we have 1 command a week to run to keep patched.  That's vastly different from having to hunt down new source packages, install all new dependencies and maintain all of those too.  Just too much work.

BTW, in Ubuntu, MySQL has been deprecated for about 8 yrs. We use MariaDB, not MySQL.

Of course, you are free to do things the hard way, as that training seems to want.

Also, python is already installed on Ubuntu. It is used for all sorts of glue stuff used inside the OS.  Whatever you do, don't try to change the version of python used by the OS. That will break your Ubuntu install.  There are ways to have different versions of python, perl, ruby, installed and used for specific needs, while not being used by the OS.

---

### Post by mikevaz216 on 2024-04-29
Dont worry, i found a fix by my own, the thing was on the version of ubuntu, it was on default version (24.20.04 i think something like that) i had to go back to an older version (20.0.03 or some) and it worked!
Thank you for response!
-From Mexico, B.C., Tijuana
Student from: Preparatoria Federal Lazaro Cardenas #1 (Highschool). Jose M. Vazquez.

---

### Post by TheFu on 2024-04-30
24.20.04?

You'll need to pay attention to details much more closely.  If you don't know something, say that rather than make up a number.  If instructions say to use a specific version of anything, then you should ensure that's the version used.  Things change between versions.  It is like working on a car.  You have instructions for a Toyota, but you what you have is a Ford.  Sometimes those instructions are fine, but usually they are not.

Glad you figured it out.  BTW, please mark this thread as "SOLVED" using the _Thread Tools_ button near the top. It will help others who have a similar issue find the answer.

---

