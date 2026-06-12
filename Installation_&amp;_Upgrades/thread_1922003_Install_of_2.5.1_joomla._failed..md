---
title: "Install of 2.5.1 joomla. failed."
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by jamstir on 2012-02-07
Hi guys, anyone tried to install the new Joomla?? 2.5.1  i have tried a dew idea,s and got stuck.

seems to be saved some where.
jam@jam-desktop:~$ `joomal_2.5.1-stable-Full_Package.zip' saved [8694]
>

Before i got to this i       **cd /etc/apache2/**
[B]sudo cp sites-available/default sites-available/joomla

[/B]**sudo a2ensite joomla**
[B]sudo /etc/init.d/apache2 restart


[/B][B]mysql -u root -p 

[/B][B]create database [COLOR=red]joomla[/COLOR];

[/B][B]CREATE USER '[COLOR=red]joomla[/COLOR]'@'localhost' IDENTIFIED BY '[COLOR=red]xxxxx, [my pass...]

.[/COLOR][/B][B]grant all privileges on [COLOR=red]joomla[/COLOR].* to [COLOR=red]joomla[/COLOR]@localhost;

[FONT=Arial]All went fine till this..

[/FONT][/B]**wget joomlacode.org/gf/download/frsrelease/15900/68956/Joomla_1.7.2-Stable-Full_Package.zip**
**sudo mkdir joomla**
[B]sudo unzip Joomla_1.7.2-Stable-Full_Package.zip -d /var/www/joomla

I left out the /15900/68956  and changed  1.7.2 with    2.5.1.

I got a warning to say  short html
[/B]then this..

seems to be saved some where.
jam@jam-desktop:~$ `joomal_2.5.1-stable-Full_Package.zip' saved [8694]


I have tried to unzip, but cant be found, i tried everywhere i know of to try and get it.. i cant understand if i have it saved where it is, or what command i should give.. and there,s not a clear install for this release yet.
Sudo   tells me there,s a file in the var/www/joomla      i went to that location and i not see one, only var/www with no file in it bar a php test page i set in.

Anyone help.. :(

---

### Post by Rodney9 on 2012-02-07
[http://www.upubuntu.com/2011/11/how-to-install-joomla-17x-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-joomla-17x-on-ubuntu.html)

This site is for version 1.7 but you could try it replacing 1.7 wherever for 2.5.

Rodney

---

### Post by jamstir on 2012-02-08
I tried that, replaces the numbers with the new 2.5.1, i have the joomla on desktop and extract from there, i have set up apache mysql, and turned of buffer in php.
I have tried a few commands to get joomla to install, i have tried putting the folder into www/ and installing.. nothing seems to kick it. I think i might have to install it manually.

Might move on and try to install Codelgniter 2.1.0, what am trying to do is set up a complete web site,s building programs.

using..     frameworks...   codelgnitor.     Template engine,   Dwoo  And content manager being  wordpress and joomla.

---

