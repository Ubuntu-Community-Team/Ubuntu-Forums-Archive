---
title: "Installing apache with perl (for running sql-ledger)"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by DavidTangye on 2005-09-29
Hi all,
I installed the sql-ledger deb package. To run Sql-ledger I need a web server that has perl capability built in, because sql-ledger is mainly a bunch of perl scripts. However I think that the apache 1.3 webserver that I have installed does not have perl capability. Questions:
1. How do I check whether my apache has perl capability?
If it does not ..
2. Which apache deb package is the one I need?
3. Should I switch to apache 2 while I am at it? If so must I uninstall apache 1.3 first?
Thanks

---

### Post by Tinwood on 2005-10-06
[quote=DavidTangye]Hi all,
I installed the sql-ledger deb package. To run Sql-ledger I need a web server that has perl capability built in, because sql-ledger is mainly a bunch of perl scripts. However I think that the apache 1.3 webserver that I have installed does not have perl capability. Questions:
1. How do I check whether my apache has perl capability?
If it does not ..
2. Which apache deb package is the one I need?
3. Should I switch to apache 2 while I am at it? If so must I uninstall apache 1.3 first?
Thanks[/quote] 
I had a quick look at the installation instructions on their web site and it doesn't need mod_perl (which is good because it doesn't work properly with Apache2 yet). Therefore you DON'T need the apache-perl package.

Use Synaptic to install the Apache2 or Apache package - you may have already done the later.

Don't worry about your apache not having the 'perl' capability - it will run the perl scripts using CGI. See the following snippet from the README instructions from the SQL Ledger website:

```
create a file sql-ledger-httpd.conf in the same location
 where your httpd.conf is and copy the next section into the file
 
   Alias /sql-ledger /usr/local/sql-ledger/
   <Directory /usr/local/sql-ledger>
     AllowOverride All
     AddHandler cgi-script .pl
     AddDefaultCharset On
     Options ExecCGI Includes FollowSymlinks
     Order Allow,Deny
     Allow from All
   </Directory>
 
   <Directory /usr/local/sql-ledger/users>
     Order Deny,Allow
     Deny from All
   </Directory>
 
 edit httpd.conf and add
 
   # SQL-Ledger
   Include /config_directory/sql-ledger-httpd.conf
``` Good luck!

Cheers
Alex.

---

