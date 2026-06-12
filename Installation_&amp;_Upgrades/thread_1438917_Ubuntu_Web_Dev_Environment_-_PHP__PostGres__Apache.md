---
title: "Ubuntu Web Dev Environment - PHP / PostGres / Apache?"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by n00b0101 on 2010-03-25
I'm just now switching to Ubuntu (as in, it's still downloading the iso image)... so, I'm really hoping someone will take pity on me and help me out...
 
Basically, my ultimate goal is to have the following installed for use in a local dev environment: 
 
Apache
PHP
PostGres
Pgtcl
pgloader
 
I thought I could use XAMPP for this, but I don't actually see a way to use pg instead of mysql? 
 
Could someone tell me / suggest / instruct / dumb down the best way to accomplish this?

---

### Post by gordintoronto on 2010-03-25
If you have a graphical environment, the most common way of installing software in Ubuntu is Administration/Synaptic. Synaptic lets you sort/search through the 27,000 available packages.

I'm a version behind, and XAMPP is not listed in Synaptic. However, Apache, PHP and Postgres are.  I have Apache, PHP and Mysql installed for development in my Ubuntu desktop. I haven't done anything terribly complicated, but it all works just fine. My only complaint is that I have to use sudo to copy files to /var/www, Apache's default location for web pages. I assume that something in your PHP code would specify using pg instead of mysql.

---

