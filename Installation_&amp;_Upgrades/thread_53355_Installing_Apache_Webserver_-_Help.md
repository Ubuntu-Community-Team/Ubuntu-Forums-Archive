---
title: "Installing Apache Webserver - Help"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by erisco on 2005-07-31
I am new to linux, new to debian, new to unbuntu, new to apache. I have downloaded apache... extracted the files.... I can't get anything to work. I also downloaded the apache packages... I don't know how to access them though. Can anyone point me in the right direction?

Thanks, -e

---

### Post by heimo on 2005-07-31
Why not install apache using package management? Synaptic or apt-get - that's a way more easier and smarter, unless you have a very good reason not to. System->Administration->Synaptic Package Manager

Official Apache documentation:
[http://httpd.apache.org/]("http://httpd.apache.org/")

---

### Post by erisco on 2005-07-31
yes i said i did that... i downloaded the packages... i don't know where to get to them at though.

---

### Post by heimo on 2005-07-31
Sounds like you downloaded something, maybe source files for Apache? What I mean, is that instead of downloading packages from for example apache.org, you should use synaptic or apt-get to install apache, using pre-compiled Ubuntu packages.

To install Apache, just write this in console:
 ```
sudo apt-get update
sudo apt-get install apache2

``` 

To start apache,
sudo /etc/init.d/apache2 start

To stop
sudo /etc/init.d/apache2 stop

You may need to edit configuration files under /etc/apache2, for configuration changes to take effect, you need to restart or reload apache2

Then just point your browser to [http://localhost/]("http://localhost/") or [http://127.0.0.1/]("http://127.0.0.1/")

---

### Post by erisco on 2005-07-31
that is exactly what i wanted!!! thanks!!! YIPEEE!

---

### Post by erisco on 2005-07-31
now i just need to learn how to actually use the server. And I need to know how to be the root user! So i can even change anything! But anyways.... where would be the best help site for using apache? apache.org?

---

### Post by heimo on 2005-07-31
I don't know any tutorials for apache, but there probably exists tons of them. Go search at Google or on this forum. [http://httpd.apache.org/]("http://httpd.apache.org/") is the best reference, when you want to know what some configuration option does.

You can use sudo to run commands with super user (root) privileges and sudo -s to open root shell.

---

### Post by erisco on 2005-07-31
okay cool, power to sudo =0
I just need to know how to install php, even just put pages on my server... lol. I would also hope to be able to ftp into it. Don't worry, i will check around for tutorials... your right there would be millions =)

---

### Post by heimo on 2005-07-31
Install libapache2-mod-php4 and enable module (here /etc/apache2/mods-enabled should be symlinks to /etc/apache2/mods-available - php4.conf and php4.load).

---

### Post by erisco on 2005-07-31
Alright.... there aren't millions of tutorials... actually i can't find any. Only ones on installing apache, which I already did now. How could people hand you apache and not tell you how to use it? Where would anyone go to learn the commands, where to put things, etc.? It doesn't make much sense

---

### Post by heimo on 2005-07-31
Surf here:
[http://httpd.apache.org/docs/2.0/misc/tutorials.html](http://httpd.apache.org/docs/2.0/misc/tutorials.html)

Or get a good book about it. If you have any specific questions, just ask.

Where to put files? Your website goes to wwwroot, which path is defines in configuration files and is typically directory under /var/www/

---

