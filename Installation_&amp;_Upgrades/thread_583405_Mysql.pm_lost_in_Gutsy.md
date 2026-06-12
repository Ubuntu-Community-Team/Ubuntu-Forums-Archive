---
title: "Mysql.pm lost in Gutsy"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by tai133 on 2007-10-20
After upgrading to Gutsy I get the following error when trying to access my Perl webapps on localhost:  "Can't locate Mysql.pm in @INC"

libmysql-dbd-perl 
libclass-dbi-mysql-perl
libclass-dbi-perl
libdbi-perl   

are all installed.

Everything worked in Feisty.

---

### Post by tai133 on 2007-10-21
I 'solved' this problem by copying the Mysql.pm file from another installation directly into the @INC path which in my case included /usr/share/perl/5.8.8, so that's where I put it. I then got an error that Mysql/Statement.pm could not be found. The 'fix' for this was to create a folder named Mysql in /usr/share/perl/5.8.8 and then copy the Statement.pm file into it.

I put quotes around 'solved' and 'fixed' because I'm guessing there is an apt-get package that would have done this for me. My problem is that I couldn't figure out which one(s). Probably I applied this same 'back-door' approach when I upgraded to Feisty and that is why those files were lost when moving to Gutsy.

---

### Post by Lido on 2008-03-05
I think that interface has been discontinued. See this thread:

[http://forums.gentoo.org/viewtopic-p-4916645.html](http://forums.gentoo.org/viewtopic-p-4916645.html)

---

### Post by tai133 on 2008-03-10
Very interesting read. Thanks Lido.

---

