---
title: "Install a GUI"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2010-06-27
Hi,

I'm currently running a Debian server through SSH only. I'm not at all familiar with graphical Linux systems and cannot even install one. I only know how to manage a Linux server on the console. Now I thought it would be about time to use a GUI which should simplify some things.

I have downloaded Ubuntu Server 32-bit and installed the CD image into VMware (can't use 64-bit here). I am now at the point where I have a text console login. There doesn't seem to be any graphics interface installed.

How can I get that? What packages do I need to install? I'm sure it's a whole lot of different packages that need to fit precisely together, maybe they even need some advanced configuration? (Last time I saw somebody install a Linux GUI was like 8 years ago... Is it still as complicated?)

---

### Post by metalf8801 on 2010-06-27
try 
sudo apt-get install ubuntu-desktop 

that will install the default Ubuntu desktop with gnome there are other options but thats how I would start

---

### Post by ygoe on 2010-06-27
Thanks. Installing 2 GB now... I'll see what packages it installed then. The list was several screens long, I didn't check it.

Edit: Seeing openoffice, xulrunner and cups scrolling through - I think this was a bit too huge of a package for my needs. Are there smaller alternatives?

---

### Post by metalf8801 on 2010-06-27
really good chance you know all this but just in case you don't 

Just wondering what do you want to do with the GUI? Its great for uses as a desktop OS but I don't think its meant to be used to manage a server 

If you want a GUI for the server you should look for a web interface
like Landscape [http://www.canonical.com/enterprise-services/landscape](http://www.canonical.com/enterprise-services/landscape)
which cost money but the money goes to Canonical the company thats makes Ubuntu (I wish they had a home server version/price) 

Ebox which is free an is in the Ubuntu repo 
[https://help.ubuntu.com/10.04/serverguide/C/ebox.html](https://help.ubuntu.com/10.04/serverguide/C/ebox.html)

I've used Webmin in the past but its not in the repo 
[http://www.webmin.com/](http://www.webmin.com/)
there is a free open source version of Webmin and a proprietary paid for version 
 
again you most likely know all this but... 

Just trying to help 
Dan

---

### Post by ygoe on 2010-07-10
Okay, after browsing the packages list for a while, I think the ubuntu-desktop package wasn't all that bad, it just includes loads of recommendations that I don't need. So next time I'll try "aptitude -R install ubuntu-desktop" to omit the additional stuff.

---

