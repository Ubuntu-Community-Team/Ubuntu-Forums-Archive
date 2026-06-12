---
title: "aptitude and package versions"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by vanderkerkoff on 2008-03-11
is it possible to install an old version of mysql with aptitude?

I've seearched for mysql but it's only showing 5.0

sudo aptitude search mysql

Thanks in advance

---

### Post by insineratehymn on 2008-03-11
The quick answer is no.

The long answer is probably.

[http://dev.mysql.com/downloads/mysql/4.1.html#linux](http://dev.mysql.com/downloads/mysql/4.1.html#linux)

That is a link to the 4.1 version of non-RPM modules form mysql.

If you want earlier than 4.1.... Google knows all.

Edit:

Oh. 
I'm gonna assume someone reading this does not know how to install that...

First remove the mysql you already have:
sudo apt-get remove mysql*

Then download the one you want from [http://dev.mysql.com/downloads/mysql/4.1.html#linux](http://dev.mysql.com/downloads/mysql/4.1.html#linux)

Go into the tar and read the documentation.

---

### Post by vanderkerkoff on 2008-03-11
thanks insineratehymn  

You answered the question, it's not possible with aptitude.

I'm going to go with mysql5.0 and apache 2 and work out the textpattern fixes afterwards.

I've been putting it off for a long time now

:-)

Thanks again

---

