---
title: "Problems with Ubuntu web server"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by ronhagley on 2010-03-12
Ubuntu Server being used as local web server.

Hi, I have set up an old laptop with Ubuntu server and wish to use it as a teaching aid where students can upload (via FTP) web pages.
The main page folder is working fine - I placed files in a folder var/www/ these work fine with no problem. I can publish them there via filezilla and open them using Firefox.
However I need a sub-domain for each student - there are 8 of them required.
What I did next was:

Sudo usermod -g www-data student1
Sudo chown -R www-data:www-data/var/www/student1
Sudo chmod -R 775 /var/www/student1

This seems to have created sucessfully subfolders withing VAR/WWW
when I access a sub-domain via FTP all I see is the subdomain name - within that is a folder called cache and 3 files called .bash-logout, .bashrc and .profile
Where do I place the Web page files please? I would have expected a directory like HTDOCS or similar - help appreciated.

---

