---
title: "Apache...bahumbug!"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by nate22 on 2007-07-02
ok so i installed apache..but cant figure out where and WHAT i need to update in order for it to display MY webpages... rite now it has the defoualt


but i am familiar w/ xaamp AKA laamp so installed that...HOWEVER isince apache is there xaamp cant start..

wuts the command to remove apache?

OR wut file can i update to get my web up?

---

### Post by bikeboy on 2007-07-02
By default, web pages are stored in /var/www/ so that's where you need to put them. You can make it a different location such as /home/user/public_html/ if you want. First, I would suggest having a read of the config file to get an understanding of some of the settings.

Depending on which apache you installed it could be /etc/apache/httpd.conf or /etc/apache2/apache2.conf

---

### Post by nate22 on 2007-07-03
wim prolly gona put the web on there...but b4 i do.. is there a way to just copy and paste there?

or do i have to be on root?

---

### Post by bikeboy on 2007-07-03
You could set up an ftp server fdor uploading files to the right location, but someone else would have to help with that.

You need to be root (temporarily, using sudo), if you have a gui try this (be very careful what you do though)
```
gksudo nautilus
```

If you're running the server without a gui, I suggest installing midnight commander to make copy/paste/rename etc easier.
```
sudo apt-get install mc
```

When pasting to /var/www/ you would do 'sudo mc' to open mc as root.

---

### Post by nate22 on 2007-07-03
im running w/ gui

and right now all i need to do is copy nd paste my premade website to www folder

but i dont have privlages? even tho im admin ...but it says i have no root privalages...booo

---

### Post by bikeboy on 2007-07-04
Did you try the gksudo nautilus???

---

### Post by nate22 on 2007-07-04
yea.. and i got this error..
(nautilus:9145): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

eh nvm i got it to work...now one porblem... how do i make it public?

---

### Post by bikeboy on 2007-07-04
Yeah everyone gets that error, it still works.

What exactly do you mean by public? If you want people on the internet to see you site, you need port 80 forwarded (presuming you have a router) to your server.

Otherwise, provided apache is running, people should be able to see the site as long as they know the address.

---

### Post by steveneddy on 2007-07-04
@ nate22

I would like to help as I run an apache2 server for my web page, but I can't understand what you are trying to type.....

Think you could use real words here?

:D

---

### Post by nate22 on 2007-07-06
ok heres wut im trying to do steve
i have a my very own private WOW server yes WOW
it uses Mysql as its Database

there are webstite that you can download..place in the htdocs, that allows other (for ex. you) to create an account on the DB what i was able to do was have it local..but i need to get it public for it to work

---

