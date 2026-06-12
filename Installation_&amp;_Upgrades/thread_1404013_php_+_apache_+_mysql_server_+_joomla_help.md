---
title: "php + apache + mysql server + joomla help"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by urd on 2010-02-10
hi everyone, i was trying to install php, mysql, and apache for joomla, and in the proces y make something wrong 'cause localhost don't work, i think that i miss some option in the installing process but i try to remove them and installing again but the installation don't ask anything, how can i fix it?? 

thanks for helping me!!!

---

### Post by yogesh.girikumar on 2010-02-11
Hi,

Can you please elaborate on your issue?

   1. What version of Ubuntu are you running?
   2. Are you seeing any error? If so, what?
   3. How / In what order did you install apapache, php etc ??
   4. What do you see when you type localhost in the address bar of the browser?

This will help in narrowing down on possible causes for your problems..

---

### Post by urd on 2010-02-11
> **yogesh.girikumar said:**
> Hi,

Can you please elaborate on your issue?

   1. What version of Ubuntu are you running?
   2. Are you seeing any error? If so, what?
   3. How / In what order did you install apapache, php etc ??
   4. What do you see when you type localhost in the address bar of the browser?

This will help in narrowing down on possible causes for your problems..

i'm using ubuntu 9.10 and i still them in this order:

apache, mysql server, phpmyadmin

when i try the localhost it says that is ok the install but if a try localhost whit phpmyadmin don't show anything

---

### Post by yogesh.girikumar on 2010-02-12
Hi,[INDENT]> i'm using ubuntu 9.10 and i still them in this order:
       apache, mysql server, phpmyadmin
       when i try the localhost it says that is ok the install but if a try localhost whit phpmyadmin don't show anything
[/INDENT]    

   Please ensure that you have PHP5 installed in order to use PHPMyAdmin. PHP5 can be installed by using the command:
```
$ sudo apt-get install php5
```      You can verify if php5 is installed by using a test script.
       

To do this open the terminal:
       
[LIST]
[*]Applications -> Accessories -> Terminal
[/LIST]
       
[LIST]
[*]Type the following in the terminal
[/LIST]
   ```
$ cd /var/www
$ sudo gedit test.php
```      
[LIST]
[*]In the text editor that opens type the following line:
[/LIST]
   ```
<?php phpinfo(); ?>
```      
[LIST]
[*]Save the file and close gedit.
[/LIST]
       
[LIST]
[*]Go to the browser and type the following in the addressbar
[/LIST]
   ```
http://localhost/test.php
```If you get a lot of information about PHP in a tabulated form, your PHP installation is working. If not, then please reinstall PHP by issuing the following command in the terminal
```
$ sudo apt-get remove php5 &&  apt-get install php5 libapache2-mod-php5
```  Also please mention how you tried to install and access PHPMyAdmin. PHPMyAdmin can also be installed using apt-get:
```
$ sudo apt-get install phpmyadmin
```If you installed phpmyadmin using apt-get, then to access PHPMyAdmin, open the browser and type the following in the address bar:
```
http://localhost/phpMyAdmin/scripts/setup.php
```It will take you to a setup page where you can setup PHPMyAdmin configuration and settings by following instructions onscreen.

Hope this helps.

---

