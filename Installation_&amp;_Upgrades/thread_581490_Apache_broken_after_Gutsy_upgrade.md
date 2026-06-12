---
title: "Apache broken after Gutsy upgrade?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by andrewheiss on 2007-10-19
I just upgraded to Gutsy on my LAMP Server using sudo do-release-upgrade like it said on the main Ubuntu page. Everything went smoothly, but now man programs are not working. 

I had Hamachi installed for pseudo VPN access, but it's dead. I've tried uninstalling and reinstalling it to no avail. It was optional though...

The main problem is that Apache is now seemingly dead. Everything looks OK in the config files, with the document root and all, but I can't get to any pages from my local network (or even from lynx on the server - it says [http://localhost](http://localhost) doesn't exist and gives me an error "Can't access start file")

Is Apache configured differently in Gutsy? How can I get my web server up and running? I know the actual server works - I can SSH into it... Apache just seems to be dead.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=422113") in the forums that says I need to "edit the sites.conf file to give the server root again," but I'm a newb and think I already have that set...I don't know though

Thanks!

---

### Post by andrewheiss on 2007-10-19
I got Hamachi to work finally.

Apache is still dead, but there are some new developments:

When I try to start, stop, or restart apache (sudo apache2ctl start, etc.), I get this error:
```
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```
What does that all mean and how can I get httpd to actually start?

---

### Post by andrewheiss on 2007-10-19
I just uninstalled apache and php completely to try to get it to work. Ugh.

Now when I try to access my index.php page, at least apache is trying to serve it. However, in Firefox, I get this message:

Trying to open (no file)
which is a: application/x-httpd-php

So, obviously something is wrong here. I don't think this applies to Gutsy upgrading anymore, so I'll start a thread in the Server group.

---

### Post by solidwolf on 2007-10-20
I had the same problem with Apache not working after upgrading to Gutsy from Feisty.  In my case, checking the /var/log/apache2/error.log showed the problem was with Eaccelerator (which I had installed manually).  I had to recompile Eaccelerator to work with Gutsy's version of php (5.2.3).  After doing so, Apache started up just fine.

---

### Post by andrewheiss on 2007-10-20
I actually noticed that after looking at the error logs of the Apache I reinstalled (after killing Gutsy's Apache and PHP). I tried recompiling Eaccelerator but for some reason it wouldn't recompile, so I just disabled it. After that Apache worked great again--except the Firefox I was using to test it didn't realize it - it had cached the broken version of all my sites - after more than 2 hours of messing with Apache and PHP, I finally tried it in Safari out of frustration and it worked! I cleared FF's cache and all was well! Stupid cache!

---

### Post by rotalever on 2007-10-21
> **solidwolf said:**
>  I had to recompile Eaccelerator to work with Gutsy's version of php (5.2.3).  After doing so, Apache started up just fine.
Thanks man! That worked.

---

### Post by erwall on 2007-11-30
> **solidwolf said:**
>  I had to recompile Eaccelerator to work with Gutsy's version of php (5.2.3).  After doing so, Apache started up just fine.

How exactly did you do that?

---

### Post by fujikofujio on 2007-12-05
I have tried to recompile eaccelerator using the steps I followed when I first installed it ( [http://advosys.ca/viewpoints/2006/10/installing-eaccelerator-in-ubuntu-server/](http://advosys.ca/viewpoints/2006/10/installing-eaccelerator-in-ubuntu-server/) ) but still it won't work with my current setup.

I'm using Ubuntu 7.10

---

### Post by bluemike807 on 2008-01-08
I found a solution to at least my occurance of the problem. I also recompiled eaccelerator but it didnt seem to do much - maybe do it anyway

Gutsy comes with a built-in webserver; lighttpd which is by default using the same ports Apache tries to use - apache tries to start, cant open a socket, fails. Lighttpd doesnt natively use php so that causes screwups too.

To see if/what may be using your ports, turn off apache:

sudo /etc/init.d/apache2 stop 

And check for http processes

ps -ax | grep http

if you see anything there except for your ps/grep - there's another webserver running. 
I removed lighttp and now apache works just fine.

Hope this helps someone.

---

