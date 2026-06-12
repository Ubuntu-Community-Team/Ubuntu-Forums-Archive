---
title: "Ubuntu as webserver"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by xssnet on 2006-03-10
I come from a microsoft background and would like to know how can I go about installing Ubuntu as my webserver?  Can I install it as a desktop and publish the website or do I need to install it as a server ? I have my website already, I used to run it on microsoft windows 2003 webserver, so I have all the files that use to run under IIS.:confused: 

A step-by-step guide would assist, if anyone does not mind assisting me.:confused:

---

### Post by Zelut on 2006-03-10
I run a small hosting company on a Ubuntu server so I can tell you it can be done :)

You can host the site whether its a 'server' install or standard-desktop install.  Its just a matter of having apache, etc installed.  I run mine as 'server' (no GUI) because I knew I wouldn't need it & I remotely manage everyone via ssh.

If you have more specific questions I'm sure I can help you out..

---

### Post by xssnet on 2006-03-10
[QUOTE=kuyaedz]I run a small hosting company on a Ubuntu server so I can tell you it can be done :)

You can host the site whether its a 'server' install or standard-desktop install.  Its just a matter of having apache, etc installed.  I run mine as 'server' (no GUI) because I knew I wouldn't need it & I remotely manage everyone via ssh.

If you have more specific questions I'm sure I can help you out..[/QUOTE]

Kuyaedz, seen that I am a newbie to Linux, I will choose to go the desktop/gui interface, ourely because I am use to gui's. So I will boot from the CD and then I will need to install apache, according to the documentation I need to run Synaptic Universe and Multiverse, for the repository updates. Once this is done, do I install apache and then just copy my website and paste into apache or is there more to it? Oh thanks for your reply.

---

### Post by Zelut on 2006-03-10
That'll work fine too.  The only reason you would ever need to revert back to non-GUI is to save system resources, but for one site I'm sure you're probably fine.

Yeah, pop in the CD & just do a standard installation.  You can then install apache from the command line using:

> sudo apt-get install apache2
or from Synaptic by searching for & installing the apache2 package.  If you need other support (ie, PHP, MySQL, etc) those will also need to be installed as well.

You'll want to copy your website files into: /var/www/
[http://localhost/](http://localhost/) should display your site for you at that point..

---

### Post by xssnet on 2006-03-10
kuyaedz, thank you for your assistance, I will give it a try and let you know if I am successful.:mrgreen:

---

### Post by GTX on 2006-03-10
I have arround 20 servers all running ubuntu-server and running websites.

It is realy simple to install! Just simple apt-get commands.

I would say its EASIER than windows to install apache2/php5/mysq/php-mysql

---

### Post by dermotti on 2006-03-10
Yup, it IS easier then windows and the performance blows windows out of the water. I actually just switched my site from apache to lighttpd.

[http://www.xorg.us](http://www.xorg.us)

---

### Post by ephman on 2006-03-11
here's a pretty good howto about setting up a basic server.

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

ephman

---

### Post by John.Michael.Kane on 2006-03-11
[http://yolinux.com/TUTORIALS/LinuxTutorialWebSiteConfig.html](http://yolinux.com/TUTORIALS/LinuxTutorialWebSiteConfig.html)
[http://www.reallylinux.com/tips/3.html](http://www.reallylinux.com/tips/3.html)

---

