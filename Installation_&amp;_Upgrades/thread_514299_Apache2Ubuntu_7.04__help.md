---
title: "Apache2/Ubuntu 7.04  help"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by MSCTC2 on 2007-07-31
I'm trying to setup Joomla, i need to be able to browse to the index.php file that i extracted in public_html in my home folder. I browse my server on the browser with IP, i get the "Index of /" and a folder shows up apache2-default/

on the bottom says "Apache 2.2.3 (Ubuntu)server. So it looks like Apache 2 is running. I copied all the extracted Joomla files inside public_html folder. The guide says if I use [http://your_ubuntu_IP/~username](http://your_ubuntu_IP/~username) I should get the setup/index php page from Joomla. I don't get that, i get a "Page cannot be found".

I think i have to point Apache2 to that folder if i'm not mistaken, how do I do that?

Also i tried to open/edit my httpd.conf file but when i do it says "Read 0 Lines" and its blank. Could that be the real file or does Apache2 have a different file?

I'm sorry about these basic question, but its hard to break 15+ years of Windows with 1 week of Linux.

Thank you for reading!

---

### Post by gunderwood on 2007-07-31
You need to enable user directories. 

To enable userdir module

```
sudo a2enmod userdir
```

---

### Post by MSCTC2 on 2007-08-01
ok, thanks for the suggestion. It did something thats for sure. Now I get a "Downlaod http-php" save or open prompt. 

I think my other problem is apache2 is not reading php files. If i try [http://my_IP/testphp.php](http://my_IP/testphp.php) it says "Not found" . 

If could find that httpd.conf that would help.. :( 

tks!

---

### Post by MSCTC2 on 2007-08-01
Anyone?

---

### Post by az on 2007-08-01
Do you have libapache2-mod-php5 installed?

---

