---
title: "How to install Joomla 2.5 after XAMPP"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by YigalB on 2012-07-13
I re-installed Ubuntu, so now I have fresh 12.04 installed.

Any recommendation for Joomla installation guide?

---

### Post by mastablasta on 2012-07-13
follow Joomla install documentation.
 
it's preety easy to do it, once you initiate install on your server.

---

### Post by YigalB on 2012-07-13
> **mastablasta said:**
> follow Joomla install documentation.
 
it's preety easy to do it, once you initiate install on your server.
I wouldn't have asked if it was easy for me.

The relase notes:
[http://www.joomla.org/announcements/release-news/5428-joomla-256-released.html](http://www.joomla.org/announcements/release-news/5428-joomla-256-released.html)
Talks only about windows:
[http://docs.joomla.org/Use_Joomla!_on_your_own_computer](http://docs.joomla.org/Use_Joomla!_on_your_own_computer)

XAMPP is already installed.

I found Ubuntu wiki - referring to Ubuntu 6. I am using 12

---

### Post by pe7er on 2012-07-18
Joomla installation guide: [http://docs.joomla.org/Installation](http://docs.joomla.org/Installation)

btw: why do you use XAMPP?
You could also opt for installing Apache/PHP/mySQL and phpMyAdmin manually: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The only difficulty I had was with permissions/ownership (Joomla's directories where not writable by Joomla/Apache).
I solved it by running Apache under my user account:
[http://ubuntuforums.org/showpost.php?p=5960549&postcount=2](http://ubuntuforums.org/showpost.php?p=5960549&postcount=2)
(btw: don't do it like that on production servers that are publicly available through the internet)

---

### Post by YigalB on 2012-07-19
> **pe7er said:**
> 
btw: why do you use XAMPP?

I was looking at the documentation and they mentioned XAMPP is the replacement for LAMP - just a naming change for upgraded tool. That was my understanding.

I don't mind uninstalling and use LAMP instead. Is that what will make it easier? I have no crucial data, so I don't mind any idea, that will bring me to a fast, out of the box, working environment.

I have to mention that after suffering with Joomla installation on Ubuntu, and later on with Eclipse, I tried working on Win7. After less than 1 hour I had XAMPP and netBeans working  - out of the box. I still prefer Ubuntu, but this is frustrating.

> **pe7er said:**
> Joomla installation guide: [http://docs.joomla.org/Installation](http://docs.joomla.org/Installation)
Many steps... but I can give it a try.
Will it work if I do it with current XAMPP installation? i.e. will this procedure overide the current, or should I remove XAMPP? (how)?

---

### Post by Version Dependency on 2012-07-19
I recently installed Joomla 2.5 on a LAMP installation on Ubuntu 12.04.  Dead simple stuff.  You may just want to go that route.  Here's a great [guide]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/") to installing LAMP on 12.04.  Once apache is running and you put Joomla in var/www/ and give ownership of that directory to www-data...you just run the install.

---

### Post by mastablasta on 2012-07-19
[http://docs.joomla.org/Installation](http://docs.joomla.org/Installation)
 
the key here is to give ownership www-data to the directory
 
then it's just [http://www.yoursite.com/installation](http://www.yoursite.com/installation)
or more likely it will be [http://localhost/](http://localhost/)  or similar.
 
if you have the ownership it is easy as the installation kicks off and then you just follow instructions and do what you want to do in it. it's like installing ubuntu. mnostly user name&password, language, database name and such.
 
if you still have porblems you should mention what exactly is giving you the trouble in linux. any specific error messages connected with Ubuntu?

---

### Post by YigalB on 2012-07-19
> **Version Dependency said:**
> I recently installed Joomla 2.5 on a LAMP installation on Ubuntu 12.04.  Dead simple stuff.  You may just want to go that route.  Here's a great [guide]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/") to installing LAMP on 12.04.  Once apache is running and you put Joomla in var/www/ and give ownership of that directory to www-data...you just run the install.
i followed the LAMP instruction you gave: it was easy, all worked by the guide. Thanks !
I had a permission issue, so I used chmod 777 for all the www folder. I hope that's ok.

Now Joomla zip file is residing within the www folder. What guide should I use to install?

---

### Post by lukeiamyourfather on 2012-07-19
> **YigalB said:**
> 
I had a permission issue, so I used chmod 777 for all the www folder. I hope that's ok.


That will allow normal users to see things like database passwords.

---

### Post by pe7er on 2012-07-19
> **YigalB said:**
> Now Joomla zip file is residing within the www folder. What guide should I use to install?
[http://docs.joomla.org/Installation](http://docs.joomla.org/Installation) or [http://docs.joomla.org/Installing_Joomla!_1.7](http://docs.joomla.org/Installing_Joomla!_1.7) (1.6 + 1.7 are short term support versions for the current Long Term Support version 2.5)

In short:
Did you create a database using phpMyAdmin?
If you did, unzip the Joomla 2.5.6 full package within the WWW folder.
Use your browser to go to [http://localhost/](http://localhost/) and follow the instructions during installation.

If the Joomla installation procedure cannot create a configuration.php in your WWW folder, just create the file yourself and copy + paste the configuration info from the last(?) step into it.

If you have any problems installing 3rd party extensions > check the folder permissions (Site > System Information > tab "Directory Permissions").
If they are unwritable: "chown" the files to the "Apache user" (probably www-data).

If you have any Joomla related questions, you could visit Joomla's documentation site [http://docs.joomla.org/](http://docs.joomla.org/) , or the forum at [http://forum.joomla.org/](http://forum.joomla.org/)

---

### Post by pe7er on 2012-07-19
> **lukeiamyourfather said:**
> That will allow normal users to see things like database passwords.
777 is indeed not safe...
More info about Joomla & permissions: [http://docs.joomla.org/Verifying_permissions](http://docs.joomla.org/Verifying_permissions)

---

### Post by Version Dependency on 2012-07-20
> **YigalB said:**
> I had a permission issue, so I used chmod 777 for all the www folder. I hope that's ok.

If this is just going to be a test install on localhost that will never be a live site then I wouldn't worry, but if this site is going to be live on the web, then you need to go back and make sure critical files (config files, anything with database passwords, etc.) are not readable and  writeable to the public...for very obvious reasons.

---

### Post by YigalB on 2012-07-20
> **Version Dependency said:**
> If this is just going to be a test install on localhost that will never be a live site then I wouldn't worry, but if this site is going to be live on the web, then you need to go back and make sure critical files (config files, anything with database passwords, etc.) are not readable and  writeable to the public...for very obvious reasons.
Just locally, nothing public. Thanks.

---

### Post by AdamDevise on 2012-09-21
> **Version Dependency said:**
> If this is just going to be a test install on localhost that will never be a live site then I wouldn't worry, but if this site is going to be live on the web, then you need to go back and make sure critical files (config files, anything with database passwords, etc.) are not readable and  writeable to the public...for very obvious reasons.
I'm absolutely agree with you .

---

