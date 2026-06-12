---
title: "Trouble getting PHP4 working with Apache 1.4"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by veraction on 2005-05-24
Ok, so I have a default installation of apache installed and its working ok, with html files at least. I installed libapache-mod-php4, php4, and a few other packages via apt-get. In /etc/apache/httpd.conf, I uncommented the two lines for PHP4 support (so it can recognize .php and .phps, I think). I didn't modify anything in modules.conf yet (it says not to edit it)

Anyways, I can't think of what else to do.** My localhost server can interpret HTML fine, but not PHP** (it asks to save file). The annoying thing is that I had this all working earlier today, but removed every apache thing cause I was trying to install something else. I have a clean slate now -- with the installed packages via apt-get.

Also, is there any way for me refresh the Apache settings without rebooting? like a simple command?

Thanks ;)

[edit] using apache 1.3 (yes, I know apache2 is out there)

---

### Post by veraction on 2005-05-24
Am now trying apache2 with php4, and am still having same problems. the web server can't read .php files...

---

### Post by Infernal on 2005-05-24
[http://www.ubuntuguide.org/#apachehttpserver](http://www.ubuntuguide.org/#apachehttpserver)

follow those steps

---

### Post by veraction on 2005-05-24
well, those instructions didn't seem to do anything different than what I've done before -- I did that stuff about 4-5 times already.

but anyways, I removed all of apache and php, then followed those steps to reinstall everything. when I try to go to the testphp.php, my web browser (firefox) still prompts me to save the file.

do I need to edit anything in the php.ini file to get it to work?

---

### Post by veraction on 2005-05-24
OK, I finally got it working sortof. It now interprets PHP. I had to add the LoadModule for php to my httpd.conf (which was weird since I didn't do that last time)

---

