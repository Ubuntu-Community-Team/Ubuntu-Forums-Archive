---
title: "Apache 403 forbidden error to access folders"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by mi6crazyheart on 2009-11-15
Hello.....
Just after the successfully installation of Apache+PHP5+MySQL in my new Ubuntu 9.10 (By this link : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ) when i tried to use Codeigniter by coping the Codeigniter files to my new config. root folder (/home/user/public_html/) and when tried to execute that **[http://localhost/ci/index.php](http://localhost/ci/index.php)** (**ci= codeigniter folder**) it is showing an error of ..... 

**403 Forbidden**

 You don't have permission to access /ci/index.php on this server.
  Apache/2.2.12 (Ubuntu) Server at localhost Port 80


------------------------------------------------------------------------------------------------------
[LEFT]Guys, can any body tell me what's going wrong at where & how i can solve this problem. I tried a lot in Google bit didn't able to get any perfect solution.
[/LEFT]

---

### Post by wojox on 2009-11-15
You followed this part to the T? 

Did you make a /home/user/public_html/ci/ and then change DocumentRoot to point there?

---

### Post by mi6crazyheart on 2009-11-15
No.....
First i change the Document root to this path : /home/user/public_html/ by following this link [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)  
Then i download the Codeigniter rar file and extrat that to Codeigniter folder & rename the **Codeigniter **folder to **ci**. Then i copy the **ci** folder to **/home/user/public_html/**. After this when i tried to run the index.php file in my browser whihc is present inside of that **ci** folder by this url **[http://localhost/ci/index.php](http://localhost/ci/index.php)  **i got that error

---

### Post by webtechquery on 2010-02-27
Hi there.
There might be the permission problem for not setting the right permission.
To solve your problem, may be the following URL will help:
[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

And if still your problem does not solve, then make one thing sure that your [http://localhost](http://localhost) is working fine. If even [http://localhost](http://localhost) is also not working fine, then I suggest you to re-install the LAMP (Linux Apache MySql Php) on your system. To get help on how to install LAMP, check the URL below:
[http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/)

For any further queries, contact me.

Thanx.

---

### Post by jmblock2 on 2010-06-06
Hi, not sure if I should have started my own thread on this, but it kind of just takes off from the same point.

I have apache 2.2.14 installed. The default website works fine at localhost. If I change the default conf file to a different directory (/home/jacob/Workspace/www) I get the 403 error. I changed the permissions to a+rwx and I get the same error. Not sure how I could get the permissions error when the directory is set so that 

The user and group of apache is www-data by default. If I change this to jacob or root in envvars the server works, but I am pretty sure I shouldn't keep it that way for safety reasons.

I tried to replicate the /var/www directory which is what the default path was. The owner and group are root, so I changed my /home/jacob/Workspace/www to root, still doesn't work. I then tried to change it to www-data, and it still doesn't work.

So I am out of ideas and I thought I had a good understanding of the problem, but apparently not.

Any ideas? Thanks,

Jacob

note:
I am pretty sure that, in the end, apache should have its own user and group, the owner of the new www directory should be jacob, the group should be www-data, and group www-data and other users should only have read privileges. I would like to get to that point.

If any of this sounds wrong please let me know.

---

### Post by jmblock2 on 2010-06-06
Ah, I figured out that my problem was the parent directory of www also needed to be set to www-data.

I still don't understand why, but once I did that the index.html displayed.

---

### Post by sebagr on 2010-11-11
> **jmblock2 said:**
> Ah, I figured out that my problem was the parent directory of www also needed to be set to www-data.

I still don't understand why, but once I did that the index.html displayed.

Thanks, man... you saved me like 2 hrs of banging my head on the wall :)

BTW, I don't understand either, why the parent folder needs read permissions too...

---

