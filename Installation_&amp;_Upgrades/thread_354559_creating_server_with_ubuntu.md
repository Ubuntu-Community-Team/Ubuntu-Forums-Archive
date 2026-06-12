---
title: "creating server with ubuntu"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by paulus4605 on 2007-02-06
Dears
since I'm new to all this I would like to try to install ubuntu on a old desktop pc 
and use this as a server.
the current situation is like this 
=>incomming internetconnection through cable modem
=>router
=>wired desktop windows xp
=>2 wireless laptops windows xp

If I'm correct I would like to install the server between cablemodem and router or should this be installed after the router.

and where can I find a manual to set this all up correctly 

thanks for your help and feedback

Paul

---

### Post by aberry5555 on 2007-02-06
I think your server should be installed on the router, but it entirely depends on what you want it to do. Is it meant to be a firewall or is it going to be a webserver etc? Please give a little more info if possible.

---

### Post by paulus4605 on 2007-02-06
Well
the meaning of the server will be
fileserver and mailserver mainly but I would like to be able to run a webserver also 

thanks for your help
Paul

---

### Post by usererror on 2007-02-06
> **paulus4605 said:**
> Well
the meaning of the server will be
fileserver and mailserver mainly but I would like to be able to run a webserver also 

thanks for your help
Paul

I would put on the LAN side of the Router NOT the WAN side (not between the router and the cable modem)

I am running a Debian web server with a static IP on the LAN (192.168.1.3) and I have port forwarding enabled for ports 80, 22, 21, etc for my services to be accessible from the outside world.  Oh, and make sure your ISP allows port 80 usage.  I had one cable modem ISP that did NOT allow it. :( 

Hope that helps a little bit!

---

### Post by paulus4605 on 2007-02-06
this helps indeed
is there anywhere online a site where I can find a manual in how to create a server like this?

Paul

---

### Post by aberry5555 on 2007-02-07
well to create a server like this all you need to do is install Ubuntu's LAMP server, then add FTP and mail server packages to it after you have installed it on the machine. The .iso is found in the same way you find the desktop image.

---

### Post by paulus4605 on 2007-02-07
thanks for your reply is there a manual in how to install all this?
thanks for your reaction

Paul

---

### Post by aberry5555 on 2007-02-07
umm off the top of my head I don't know, but the server install will automatically install LAMP for you (Linux-Apache-Mysql-Php). It is quite simple to install, although, unless you specify otherwise, it will all be command-prompt based. Install it first (following the on-screen prompts, much like any normal install) and then, if you want the normal ubuntu desktop to work with, type in to the terminal "sudo apt-get install ubuntu-desktop". This will basically give you normal Ubuntu with a few extras and missing a few bits you don't need. For the FTP and mail server there are a variety of different programs to try, I'm not up to scratch on either so maybe someone could suggest a tried and tested set of programs?

EDIT

There is one very useful program that would help you automate things like this called Webmin, it basically allows you to log in to your server remotely and change settings with a GUI rather than fiddling around with your configuration files. It isn't in the Ubuntu repositories but it can be installed like this: (quoted from another thread): 

> Re: Webmin installation in Ubuntu server 

--------------------------------------------------------------------------------

I don't think webmin is in the repos. However, you can download a .deb from here.


Code:
```
wget -c http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.320_all.deb 
```Then, you can install it with


Code:
```
sudo dpkg -i webmin_1.320_all.deb
```

Also, if you decide to install Webmin you might find you don't need the desktop environment on your Ubuntu install as it will only slow it down, and you could do most things with Webmin. I would install Webmin first, try it out and, if you find that it isn't easy enough or doesn't give you enough functionality, then install the desktop.

---

### Post by usererror on 2007-02-07
Here is my mini howto that I made mostly for myself for when I rebuild my server:

[http://www.iametarq.com/archived/v43/linux.php](http://www.iametarq.com/archived/v43/linux.php)

the apache documentation on their website is also really good.

---

### Post by The_It_Guy on 2007-10-31
Hi i would like some help creating an outgoing server on ubunthu to handle all outgoing mail for windows users

---

