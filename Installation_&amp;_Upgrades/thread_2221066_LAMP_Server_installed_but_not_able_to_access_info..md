---
title: "LAMP Server installed but not able to access info.php"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by John_McAdoo on 2014-04-30
I'm hoping that I am asking in the right place. First and foremost, I am new to the Ubuntu and Linux Community but after opening a repair shop, I wanted to explore other options besides Windows. I am currently using 14.04 and followed a guide to install a LAMP Server on one of my systems. The purpose of the server is to hold a database for Phreebooks so that I can have some control over my inventory that I will be carrying. Now that is in the future because I have already hit a roadblock. The details are below...

I installed Apache, MySql, and PHP 5 on my system. I can log into the server and get a message that Apache is working just as it should. Following the guide, I installed PHP as well and have seen no errors. I created a file within /var/www called info.php with a generic script that just tells me about my PHP properties. When I log into my server to check if the file is working, I get an error that Server is not found. I have done a bit of research and still can't figure what exactly I am doing wrong. I am wondering if I am missing some libraries but I have installed all the ones that I have been told to. 

Im assuming that this a really low level question but any help would be appreciated. I look forward to working with the Ubuntu Community!
Thanks

Edit... I also forgot to mention that I have restarted the apache service twice and still no luck.

---

### Post by SeijiSensei on 2014-04-30
In 14.04 the Apache version was upgraded to 2.4 and the default location for the website changed from /var/www to /var/www/html.  Try putting info.php in that directory and see if it works.

Also run the command "sudo apt-get install libapache2-mod-php5" and make sure that package is installed.  It tells Apache to apply the PHP interpreter to files ending in .php (and some deprecated extensions like .phtml).

---

### Post by John_McAdoo on 2014-04-30
Thanks! I had already had that Library but my problem was that I had it placed in the area just as you had said. Moving the file to appropriate area fixed the issue

---

