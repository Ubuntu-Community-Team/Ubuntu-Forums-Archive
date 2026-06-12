---
title: "Replacing a existing package in hardy"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by raghaven.kumar on 2008-10-30
Hi,

I rebuilt a source package of apache2.2-common using the below link
[http://blog.our-files.com/?p=6]("http://blog.our-files.com/?p=6")

i need that to be installed at a ubuntu 8.04 server which is currently having apache2 and apache2.2-commmon installed
and also has some critical websites running live on it.

I have even changed the build number as specified in the blog using 'dch -i'.

Ok, the million dollar question is
how do i upgrade the systems' apache2.2-common with the package i built without disturbing other packages and the sites?
I mean is there a way like its done for a package by 'apt-get update' ? :confused:

---

### Post by raghaven.kumar on 2008-10-31
Ok, one may want to know why i am doing this?

Actually, i am installing virtualmin in webmin
It says 
```
Failed to save enabled features : The Suexec command on your system is configured to only run scripts under /var/www, 
but the Virtualmin base directory is /home. CGI and PHP scripts run as domain owners will not be executed.
```

On googling i found that i need to recompile suexec module with docroot as /home

Thats what i did !

Now is there a solution for installing virtualmin in webmin w/o disturbing the existing apache?
or
Can the apache2.2-common be just upgraded with the rebuilt deb package?
:confused:

---

