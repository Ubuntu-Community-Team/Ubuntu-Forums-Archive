---
title: "how to update/upgrade PHP  version to the latest stable? and mysql as well"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by capt_nemo777 on 2011-11-19
hi, my current installed PHP version is 5.3.5
my MySQL installed version is 5.1.54

how to update/upgrade my PHP
into 5.3.8

and my MySQL into 5.5.8 ? 

via ubuntu terminal ?

---

### Post by raja.genupula on 2011-11-19
actually 
```
sudo apt-get install --resinstall <app_name>
```

for specific pkg updating .

---

### Post by capt_nemo777 on 2011-11-19
> **raja.genupula said:**
> actually 
```
sudo apt-get install --resinstall <app_name>
```

for specific pkg updating .

do you know what's the specific <app_name> for PHP5.3.8 and MySQL 5.5 ?

---

### Post by raja.genupula on 2011-11-19
I think if they are stable then automatically that updates will send to your system through your update manager man .

---

### Post by capt_nemo777 on 2011-11-19
> **raja.genupula said:**
> I think if they are stable then automatically that updates will send to your system through your update manager man .

but apparently, there's not automatic update in my update manager , what to do now?

---

### Post by SeijiSensei on 2011-11-19
Unless there's something in particular you need that PHP 5.3.8 offers and 5.3.5 does not, why bother?  My production server (running CentOS 5.5) uses 5.1.6 with some 5.3 code backported. 

If you really want to upgrade PHP, you can see if there's a PPA repository that has the newer version, or else you'll be building it from source code.

A quick Google search shows a lot of discussions about MySQL 5.5 on Ubuntu.

---

### Post by capt_nemo777 on 2011-11-19
> **SeijiSensei said:**
> Unless there's something in particular you need that PHP 5.3.8 offers and 5.3.5 does not, why bother?  My production server (running CentOS 5.5) uses 5.1.6 with some 5.3 code backported. 

If you really want to upgrade PHP, you can see if there's a PPA repository that has the newer version, or else you'll be building it from source code.

A quick Google search shows a lot of discussions about MySQL 5.5 on Ubuntu.

ok, where can i find the httpd-vhosts.conf file on ubuntu linux ?

---

### Post by raja.genupula on 2011-11-19
use this command to find files

```
locate filename
```

---

### Post by capt_nemo777 on 2011-11-19
how to add named virtual hosts on ubuntu's apache2 ?

is this the correct directory to edit ?
```

/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-vhosts.conf

```

```

<VirtualHost *:80>
	ServerAdmin webmaster@dummyhost.com
	DocumentRoot "/var/www/durog"
	SErverName test test.com
	ErrorLog "/var/log/apache2/test-error_log"
	CustomLog "/var/log/apache2/durog-access_log" common
</VirtualHost>

```

then i added
```

127.0.0.1   test

```

to the /etc/hosts file

then restarted apache via /etc/init.d/apache2 stop , -> start

when i typed [http://test](http://test) at the browser bar , it's a white page of death

---

### Post by raja.genupula on 2011-11-20
Use this link , its have complete tutorial
[http://brucewampler.wordpress.com/2009/02/28/adding-virtual-hosts-to-ubuntu-apache/](http://brucewampler.wordpress.com/2009/02/28/adding-virtual-hosts-to-ubuntu-apache/)

---

