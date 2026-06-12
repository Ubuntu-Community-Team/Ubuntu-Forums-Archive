---
title: "Installed cURL will not update phpinfo"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by torreblancajr1 on 2015-04-07
Hello, 

I am new to Ubuntu and I have installed a LAMP into it. yet the cURL version is at 7.3x and i have downloaded a newer version 7.41 with the help of Pavel Polyakov's blog "http://pavelpolyakov.com/2014/11/17/updating-php-curl-on-ubuntu/" yet at the end of his steps i don't have php5-fpm it wont restart. I did restart Apache2,  yet get a  [OK] with a message along the lines of this: " could not reliably determine the server's fully qualified domain name" . After the restart I check the phpinfo and the old version is still there. How can i update the phpinfo to show the new version of cURL.   phpinfo.ini ?

how can i troubleshoot the issue. 

p.s. 
new to ubuntu 14.04.1
virtual box

---

### Post by Habitual on 2015-04-08
Did it show before the curl upgrade?

for the "could not reliably determine the server's fully qualified domain name"
you can do this:
```
sudo echo "ServerName localhost" >> /etc/apache2/apache2.conf && sudo service apache2 restart
```

---

