---
title: "apache2 php module missing"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by aliyuzaki on 2007-12-14
[SIZE="3"]hi guyz

im just trying to install and run php and apache but after installation the apache server is running fine but it cant open php pages, when i try to enable it with a2enmod its apcent, so check in the /etc/apache2/mods-available the php5 module is not there. it seems that they forget to compile with it when they compile.

any one with a way out???

thanks all[/SIZE]

---

### Post by cheesey_toastie on 2007-12-15
I am having exactly the same problem.  After bodging my php / apache2 install trying to run different sites on different ports I uninstalled everything and then reinstalled. 

I notice that i don't have any libphp modules in the modules Available directory.  Is there any command i can use to get these without having to reinstall apache?

---

### Post by cheesey_toastie on 2007-12-15
I've tried stopping my Apache2 server
```

sudo /etc/init.d/apache2 stop

```
Then uninstalling the apache2 php5 library (this is where I think my problem lies?!)
```

sudo apt-get remove libapache2-mod-php5

```

The output is 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxcb-xv0 libmcrypt4 libxcb1 libt1-5 libxcb-shape0 libgd2-xpm libmodplug0c2
  libxcb-shm0 libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libapache2-mod-php5
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 5755kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105910 files and directories currently installed.)
Removing libapache2-mod-php5 ...
**Module php5 does not exist!**

```

So I install it again 
sudo apt-get install libapache2-mod-php5

And restart my Apache2 server.  Still no luck, php files are downloaded and I can't find any module that seems to be php related in the Apache2 Modules Available directory.

What is going wrong!!

```

Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxcb-xv0 libmcrypt4 libxcb1 libt1-5 libxcb-shape0 libgd2-xpm libmodplug0c2
  libxcb-shm0 libxine1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  php-pear
The following NEW packages will be installed
  libapache2-mod-php5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2543kB of archives.
After unpacking 5755kB of additional disk space will be used.
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... 105908 files and directories currently installed.)
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.3-1ubuntu6.2_i386.deb) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.2) ...

```

---

### Post by cheesey_toastie on 2007-12-15
OK - I don't know why this works - but it's two hours of my life that I will never get back so hopefully this will help someone else.

```

sudo /etc/init.d/apache2 stop
sudo apt-get remove --purge apache2 php5
sudo apt-get remove --purge libapache2-mod-php5
sudo apt-get install php5 apache2 libapache2-mod-php5
sudo /etc/init.d/apache2 start

```

It seems that the libapache2-mod-php5 wasn't correctly installing.  Just uninstalling and reinstalling didn't seem to clear the problem but the above does. 

Hope that helps.

---

### Post by praddie on 2008-03-07
> **cheesey_toastie said:**
> OK - I don't know why this works - but it's two hours of my life that I will never get back so hopefully this will help someone else.

```

sudo /etc/init.d/apache2 stop
sudo apt-get remove --purge apache2 php5
sudo apt-get remove --purge libapache2-mod-php5
sudo apt-get install php5 apache2 libapache2-mod-php5
sudo /etc/init.d/apache2 start

```

It seems that the libapache2-mod-php5 wasn't correctly installing.  Just uninstalling and reinstalling didn't seem to clear the problem but the above does. 

Hope that helps.


Cheesey_toastie,

Thanks a ton friend.... got over my frustration on PHP with your suggestion.. Thanks again :guitar:

---

### Post by cheesey_toastie on 2008-03-07
You're very welcome.  Always good to hear I've saved someone some pain!

---

### Post by kellemes on 2008-03-11
And another thanks.. ;-)
I was struggling with this myself and your post fixed it indeed.

---

### Post by modustollens on 2008-03-16
Cheesy - another big thanks !  I searched for solutions on many occasions to get my php server to work - nothing helped until I tried your suggestion - and it worked straight away!

---

### Post by jul1976 on 2008-05-31
> **cheesey_toastie said:**
> OK - I don't know why this works - but it's two hours of my life that I will never get back so hopefully this will help someone else.

```

sudo /etc/init.d/apache2 stop
sudo apt-get remove --purge apache2 php5
sudo apt-get remove --purge libapache2-mod-php5
sudo apt-get install php5 apache2 libapache2-mod-php5
sudo /etc/init.d/apache2 start

```

It seems that the libapache2-mod-php5 wasn't correctly installing.  Just uninstalling and reinstalling didn't seem to clear the problem but the above does. 

Hope that helps.

THANK YOU!!! - I was having the same problem, and the commands you listed worked perfectly. For some reason, PHP5 didn't get loaded at all on my machine (even though I installed it!). Tried everything under the sun to no avail, and then I found those beautiful 5 lines of yours and all is well in the world again.

Thanks again Toastie!!!

---

### Post by gos1 on 2008-06-12
i am still getting a download box when I try to run a php file I dont know what is wrong still and I dont have php5 module what should I do ? I tried almost everything .

---

### Post by cheesey_toastie on 2008-06-13
> **gos1 said:**
> i am still getting a download box when I try to run a php file I dont know what is wrong still and I dont have php5 module what should I do ? I tried almost everything .

Try to clear the history in your browser, if it has cached the page you're testing that could cause problems.   

If it still doesnt work can your please run the commands above and copy and paste the output into this forum.  I might not be able to understand it but I'm sure someone here will!

---

