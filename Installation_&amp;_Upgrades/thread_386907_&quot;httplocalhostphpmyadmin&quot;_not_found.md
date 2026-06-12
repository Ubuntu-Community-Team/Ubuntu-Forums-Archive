---
title: "&quot;http://localhost/phpmyadmin&quot; not found"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by cje on 2007-03-17
I've installed php5. But [http://localhost/phpmyadmin](http://localhost/phpmyadmin) return "not found"
Whats wrong?

---

### Post by MikeDX on 2007-03-17
Can you give us a few more details please?

did you type the address in? or is that a link you have clicked

is the mysql daemon running?

have you restarted apache since installing phpmyadmin?

is it possible you might mean [http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/)

trailing slashes and case sensitivity are regular places for simple errors in linux.

---

### Post by cje on 2007-03-17
Thanks for your quick reply.
[http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/) didn't work either

Yes apache has been restarted
I'm not quite sure how to check if the mysql daemon is running ("newbie error")

---

### Post by cje on 2007-03-17
I'm able to access the MySQL db through MYSQL Administrator. So, the mysql daemon is running....

---

### Post by scxtt on 2007-03-17
what directory is phpmyadmin being served from?  for me, it's in "/var/www/localhost/htdocs/phpmyadmin/" (on gentoo) ... i'd make sure it's in the right place, 1st off ...

---

### Post by louieb on 2007-03-17
Do you have phpmyadmin installed. I believe the default HTML directory is /var/www. Have a look there and see if you can find it. 
I have the Ubuntu LAMP server installed on one machine. phpmyadmin in  /var/www is a symbolic (shortcut in windows terms) link to /usr/share/phpmyadmin.

---

### Post by cje on 2007-03-17
there are no mysql link in /var/www to /usr/share/phpmyadmin
how should the link look like? - or do you have a command I may use?

---

### Post by louieb on 2007-03-17
My mistake I thought you were looking for phpmyadmin.

---

### Post by cje on 2007-03-17
> **louieb said:**
> My mistake I thought you were looking for phpmyadmin.

I do! ;-)

---

### Post by scxtt on 2007-03-17
do this:
 
sudo slocate -u
sudo slocate phpmyadmin | grep index
 
and post the results

---

### Post by az on 2007-03-17
> **cje said:**
> I've installed php5. But [http://localhost/phpmyadmin](http://localhost/phpmyadmin) return "not found"
Whats wrong?

Installing php5 does not install phpmyadmin.  You need to install it yourself.  not everyone who uses php5 would want to run phpmyadmin.

sudo apt-get install phpmyadmin

(you need to enable the universe repository.)

---

### Post by cje on 2007-03-18
It's amazing how small things that can change your day!
Thanks for your help - it made me sing!

---

### Post by Maffu on 2008-01-30
I am having the same problem.
PHP, Apache and MySql are all getting along famously.
I have installed and re-installed phpMyAdmin as detailed above but it still doesn't work.  The phpMyAdmin directory is there in the /usr/share/ directory, but there is nothing pointing to it in the /var/www/ directories.
I am using Ubuntu 7.10.

Could you tell me how to make one of these symbolic links that are mentioned?

---

### Post by Maffu on 2008-01-30
Never mind - I made it work with my brain.

---

### Post by betrion on 2008-01-30
i had the same problem but clues on this topic helped me with solution
```
sudo ln -s /usr/share/phpmyadmin /var/www
```

---

### Post by scxtt on 2008-01-30
that's strange, if you installed it from the repos, it should have taken care of all that by creating a file called:

/etc/apache2/conf.d/phpmyadmin.conf

as well as a few other config-related things ...

---

### Post by newb4sure on 2008-03-18
Same thing.  I followed Addison Berry's short video ([www.lullabot.com](www.lullabot.com)) on installing LAMP and phpmyadmin did not end up in /var/www as she noted it should.  She was installing on Fiesty Fawn (7.04) but said it would work the same on 7.10.  

[http://localhost/phpmyadmin](http://localhost/phpmyadmin) worked the first time around, but did not work correctly the second time around hence I got the 404 message too. The sudo ln -s command you offered in a previous post fixed the problem nicely.  Although I would rather have seen phpmyadmin in the /var/www directory so my worries about messing things up would be lessened :) 

Wonder if this is a new feature in 7.10?

BTW, Ubuntu rocks, you guys are great for all the assistance and informative posts.  I'm having a great time!

---

### Post by nichpakaich on 2008-03-21
Whoa .. this thread just solved my problem. That ln command is just what I was looking for (guess it before, but didn't know how to do it::noob)

Thanks, guys!

---

### Post by bsulzen on 2008-03-31
Tracked down a solution to the 404 error when trying to access localhost/phpmyadmin. When installing phpmyadmin (sudo apt-get install phpmyadmin) at the command line, during the install a window will open telling you about phpmyadmin auto configuring for apache. To select the appropriate apache option, tab through to highlight the apache option you want and then press the space bar to place an asterick in the box. Hit enter to proceed with install and you should be good to go. Found this info at: [http://devolio.com/blog/archives/221-How-to-install-Apache,-MySQL-and-PHP-LAMP-in-Ubuntu-7.10.html]("http://devolio.com/blog/archives/221-How-to-install-Apache,-MySQL-and-PHP-LAMP-in-Ubuntu-7.10.html")

---

