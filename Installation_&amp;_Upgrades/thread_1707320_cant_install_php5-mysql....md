---
title: "cant install php5-mysql..."
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by adamkhawla on 2011-03-15
adam@adam-HP-G60-Notebook-PC:~$ sudo apt-get install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmpphp5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php5-snmpphp5-sqlite

---

### Post by Chame_Wizard on 2011-03-15
> **adamkhawla said:**
> sudo apt-get install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmpphp5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php5-snmpphp5-sqlite

What you need is the following ones
```
aptitude install php5-mysql php5-curl php5-gd php5-imagick php5-imap php5-mcrypt php5-dbg 
php5-common php5-cgi mysql-client-core-5.1 mysql-admin mysql-server-core-5.1 mysql-common
```

---

### Post by anglican on 2011-03-15
> **adamkhawla said:**
> adam@adam-HP-G60-Notebook-PC:~$ sudo apt-get install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmpphp5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php5-snmpphp5-sqliteThere should be a space between php5-snmp and php5-sqlite in your command.

H

---

