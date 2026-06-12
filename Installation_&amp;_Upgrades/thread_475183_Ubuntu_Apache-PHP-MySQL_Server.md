---
title: "Ubuntu Apache-PHP-MySQL Server"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by crxvfr on 2007-06-15
New to this. I've been familiar with *nix(-like) so long as it had to do with running a site. .....not much. mod rewrite is like hieroglyphics to me. (gotta love FF spell check) These days, monster hosts use freebsd and the likes.

I wanted the cube thing. I have an amd64 (s).

I struggled thru how to install things, getting better. I can do the cube desktop (compiz) and run xp on oneside, 98 on one side, and I'm working on 3.11 for the heck of it.

This is neat. I want to set a computer up to serve a site from a static IP. I found [this page](http://www.strdoc.net/ubuntu-apache-php-mysql-server/) but its from **2005**. When I got to the lines with php4, it couldn't be found so I changed all the fours to fives and got php5,  All of the sudo stuff worked fine other than that. I obviously did it with the terminal.

My stupid newbie question is..... where is it? I looked thru synaptic and it looks like older apache files have been turned off? All files found when searching for apache are not installed but I've learned thats not a good place to guess at things.

Anybody have some tips for using ubuntu as a server to host a site on a static IP?

---

### Post by Bachstelze on 2007-06-15
```
sudo apt-get install phpmyadmin
```

Thanks to the magic of APT, it should install all you need to run your LAMP server :)

---

### Post by crxvfr on 2007-06-15
Unbelievable ! I really like how they handle this kind of stuff. Once I get more familiar and less intimidated by it, I know I'll be hooked. Thanks

---

### Post by az on 2007-06-15
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by crxvfr on 2007-06-15
Wow. 

Is Feisty just like Dapper?

How do I start from scratch? :(

-or-

If I could tell what I have, if its enabled or not, and where its at, I think I can figure out how to use it with the information from the docs page. They are very clear. Step by step. I had no idea there would be a page for exactly what I'm trying to do. I feel so stupid.  As you can see, I'm basically finding the first things I need to be familiar with.

I don't see anything new in the menus, no sign of php, mysql or apache in add\remove. 

How do I tell whats been installed when I see no visible signs that something was installed?

---

### Post by az on 2007-06-15
> **crxvfr said:**
> Wow. 

Is Feisty just like Dapper?

How do I start from scratch? :(

-or-

If I could tell what I have, if its enabled or not, and where its at, I think I can figure out how to use it with the information from the docs page. They are very clear. Step by step. I had no idea there would be a page for exactly what I'm trying to do. I feel so stupid.  As you can see, I'm basically finding the first things I need to be familiar with.

I don't see anything new in the menus, no sign of php, mysql or apache in add\remove. 

How do I tell whats been installed when I see no visible signs that something was installed?

dpkg -l |grep apache
dpkg -l | grep php

---

