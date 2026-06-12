---
title: "phpMyAdmin"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by ravenbear on 2007-02-18
I have installed Ubuntu 6.10 and have set it up as a LAMP server but am having trouble with phpMyAdmin.  It won't launch.  Instead, I get a pop-up with the following message:

You have chosen to open

(Blank - no file or program name given)

which is a PHTML file
from [http://localhost](http://localhost)

I have previously installed phpMyAdmin without a hitch on Breezy Badger.  Any ideas on what might be causing this?:confused:

Thanks in advance.

---

### Post by ktusyn on 2007-02-24
this is kinda late but are you connect over "http" or "https" i got that error when i tried to connect over https

---

### Post by don durito on 2007-06-22
Hi,

I have the same problem. But don't know how to change the type of connection.
I tried to  just type https//:localhost/phpmyadmin but this wont make a change?
what should i do?

I am using a thinkpad x31, with xubuntu 7.04

---

### Post by don durito on 2007-06-22
Ok,

There is still no light in the dark yet. 
I tried several times to reinstall my lamp, but no  differnece. 
Then i searched through various threads, and came to one conclusion: non of them worked for me. 
I installed php5-gd wich seemed to be a dependency of drupal. But still this donwload sheet anoise me. 
Some threads suggested to clear my cach. So i cleared my cach but still no differnece. 
During my experiments i  ****** up my apache twice but was able to make it work again. I also had some mysql problems but they are solved by now. 

So please guys help me. I just cant understand why the apache won't open phpmyadmin but trys to donwload some stupide .phtml file.

so please guys help me i need drupal and phpmyadmin working realy bad

thanks in advance

don

a screenshot is attached
ps.: sorry for the language but i am realy frustrated right now

---

### Post by don durito on 2007-06-22
By now i have completly destroyed drupal. I neither can install nor uninstall it, but thats not my main problem. As far as i read in various threads. I believe that i know what the problem is. Some threads suggest that my appache doesn't know how to handel php files. And tells the browser to download those files like a zip or rar file. So i chekéd my apache2.conf if the php extension is suported.
But there weren't any entrys like :
```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```
But i won't post my whole code here cause it s just too long;

After this i checkt if the package: libapache2-mod-php5 was installed by:
```
peter@peter-think:~$ sudo a2enmod php5
Password:
This module is already enabled!
``` 
seems to be installed too me;

After this i forced a reload by:
```
 peter@peter-think:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                             [ OK ] 

```

And for sure cleared my chache. But still no difference...
please guys help me

right now, a pretty pissed 
don

---

### Post by don durito on 2007-06-23
<b> <h1>Sovedy</h1> </b>

after doing what i posted in my last post and <b> clearing the cache twice </b> after a reboot. everything works again.

But i stil have no clue what happend.

ca 
don

---

