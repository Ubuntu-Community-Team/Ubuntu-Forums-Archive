---
title: "libapache2-mod-php5 is not configured yet"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by kmuzheri on 2010-08-23
Hie Guys.
I am running on Ubuntu 10.04. I am trying to install PHP5. I have so far successfully installed Apache 2 and MySQL 5+. I am doing this the manual (.deb) way, mainly because I want to understand the OS better.

While installing php5, the following .debs installed well:
1. php5-common_5.3.2-2_i386.deb
2. libonig2_5.9.1-1_i386.deb
3. libqdbm14_1.8.77-3_i386.deb
4. libssl0.9.8_0.9.8o-1_i386.deb

When I try to install php5_5.3.2-2_all.deb using the following command: 
```
dpkg -i php5_5.3.2-2_all.deb
```

I get the following error:
```

(Reading database ... 126337 files and directories currently installed.)
Preparing to replace php5 5.3.2-2 (using php5_5.3.2-2_all.deb) ...
Unpacking replacement php5 ...
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-2) | libapache2-mod-php5filter (>= 5.3.2-2) | php5-cgi (>= 5.3.2-2); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5

```

Can anyone help me identify what the problem is. How can I solve this issue.
Remember, my intention is to understand the underlying OS and how it works hence my preference of manual over **apt-get install** approach.
Thank you in advance, your help is greatly appreciated.

Kernan

---

### Post by Charlietje on 2010-08-23
using apt-get install, will also install the dependencies while using dpkg, it will abort the installation if not all dependencies are met.

regards

---

### Post by kmuzheri on 2010-08-24
Thanx Charlietje
I understand that Charlietje, my question is what should i do when it says:
```
Package libapache2-mod-php5 is not configured yet.
```
Or, let me rephrase the question, How do I configure a package once I run it using dpkg and it does not automatically configure itself properly

---

### Post by Charlietje on 2010-08-24
you could apt-get install libapache2-mod-php5

you could install lamp by using 
```
sudo tasksel
```
and choose LAMP

it will install everything you need.

---

