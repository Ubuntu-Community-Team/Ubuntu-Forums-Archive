---
title: "Downgrade mysql-server w/o internet"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by eluzi on 2007-10-05
I'm inside a corporative network with a Ubuntu Server 7.04. To get internet access i'd need some packages to make it authenticate in the Microsoft AD, and since i've got no access to the internet i'm kinda in a loop...

 I've got DotProject installed, but it's having problems with Mysql-Server 5.0... I needed to downgrade it to 4.0, but how to do this without internet access ? I'd have to download every dependency of the package in another machine (all other are WindowsXP), take it to the server and force it to install the older version ?

 Suggestions are really welcome ! Thnx !

---

### Post by elvis on 2007-10-06
MySQL 4 is available in the 7.04 sources, so you're in luck.

Have a look at AptOnCD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

It will allow you to use an internet-connected machine to download the packages you'd need to  install a program, burn it to a CD, and then add that CD to the sources.list on another machine somewhere else that has no internet connection.

I think it might be the best way to deal with your issue.

---

### Post by caseydk on 2007-10-06
HI, core dotProject developer and Ubuntu 7.04 user here...

if you're having problems on mysql 5, the problem is that you're probably using dotProject 2.0.4 or earlier.  As of 2.1rc1, dotProject is fully PHP/mysql 5 compliant.

Go try out 2.1rc2.  The full release is due out any day now.  If you know how to use CVS, grab the Stable_2 branch for the latest and greatest.  It's quite stable and very functional.  I host a number of customers on it right now.

Thanks.

Keith Casey
[http://CaseySoftware.com/blog](http://CaseySoftware.com/blog)

---

