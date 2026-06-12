---
title: "webmin fails after reboot"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by stephenb on 2006-11-14
Hi, 
I've managed to get apache2 going and install wordpress, etc. I used webmin to set some things up. However, the next day when I started up and logged in to Ubuntu, webmin wouldn't load. I got the message "Firefox can't establish a connection to the server at localhost:10000" I've spent hours trying to figure this one out. Of course, if I reinstall webmin from source, it fires up after the installation. 

I can access the server locally and from my ip. Localhost works fine for 8080. I've changed the router to forward to the 10000 port. I've modified miniserve.conf to say "allow=127.0.0.1. to allow=0.0.0.0" and other variations. Basically, I've done everything I've found to do on the net. Frankly, I've got better things to do. 

Has anyone experienced the same problem?

---

### Post by stephenb on 2006-11-14
I'm back after wasting a little more of my life on this issue and managing to solve it. It was something to do with this, I think:
allow=192.168.1.0/24

and then *RESTART* webmin.

That entry versus 127.0.0.1, will give the network 192.168.1.1-254
access to the webmin.

you could also do: allow=192.168.1.0/24 127.0.0.1

That will give you both. 

This was part of an entry from [http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/2180.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/2180.html)

I hope this is of help to others.

---

