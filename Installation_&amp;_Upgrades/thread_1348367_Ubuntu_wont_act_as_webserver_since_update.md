---
title: "Ubuntu wont act as webserver since update"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by cheadle on 2009-12-07
Hi,
 
We have just restarted the computer (as requested) to complete the install of updates, however the computer no longer appears to be acting as a web server - which we had running successfully before hand. 
 
Now we are at a loss to what is causing this as we are fairly newbies to all this - so suggestions of help would be good on this one.

---

### Post by cheadle on 2009-12-07
Sorry I should point out we were using 9.10 and just updated to the latest bug fixes - thats what im talking about when saying updating. :)

---

### Post by hal10000 on 2009-12-07
First verify if apache is running after booting the system:
```
ps ax | grep apache
```
you should see something like this, presumably more than one line:
```
3235 ?        Ss     0:01 /usr/sbin/apache2 -k start
```
If you don't see such a line, then it's not running. You then should try to start it manually with this command:
```
sudo /etc/init.d/apache2 start
```
Then open a browser window and type into the address line:
```
http://localhost
```
If your browser does not show an error message, then it works.

Maybe during the upgrade process your own apache configuration file was overwritten by a default config that came with the update. Usually during an upgrade you will be asked if an existing config file should be replaced by the new config file. You should be carefull with overwriting it if you did specialconfigurations.

---

