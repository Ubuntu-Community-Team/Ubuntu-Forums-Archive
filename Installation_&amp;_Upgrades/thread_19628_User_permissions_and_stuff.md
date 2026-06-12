---
title: "User permissions and stuff"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by NotMe on 2005-03-12
Hi, I installed Ubuntu a couple of days ago. It's great, I was very happy to see that most things just worked (unlike the last time I tried to install Linux... no sound, no usb mouse, etc). The printer was a bit of a problem but I found a guide and  I was able to download the drivers and get it working. One of the best things about Ubuntu is the amount of support like these forums for example.  :grin: 

Anyway, I have 2 problems at the moment. The first is that I can't switch to root when I'm logged in as a normal user. When I use the default account that is created on installation I can log into the root terminal. I created a new user called say X using 'adduser X'. When I logged in as X I tried to open a root terminal but I couldn't and when I typed su in a normal terminal and then entered the root password it said  authenication failure.

The other problem is running some programs I've installed. I installed gdesklets and it works fine in my default account but it doesn't work in the X account. I think both of these problems are related to permissions or groups but I don't really know enough about it. Any ideas? Thanks.

---

### Post by vladimir on 2005-03-13
Hi, 
Did you add your new user to the "sudoers" ?

$ sudo gedit /etc/sudoers

and then append the line

your_system_username	ALL=(ALL) ALL

at the end of the file, then save it.

Your file should look like this

[http://ubuntuguide.org/sample/sudoers_allowmoresudoers](http://ubuntuguide.org/sample/sudoers_allowmoresudoers)

---

### Post by NotMe on 2005-03-13
Thanks that works. But then that user can log in as root with their own password. Would I be able to log into a root terminal while another user (who doesn't have root privileges) is logged in, if you know what I mean. 

The problem I was having with gdesklets not working was my mistake so thats ok now.

---

### Post by bored2k on 2005-03-13
[QUOTE=NotMe]Thanks that works. But then that user can log in as root with their own password. Would I be able to log into a root terminal while another user (who doesn't have root privileges) is logged in, if you know what I mean. 

The problem I was having with gdesklets not working was my mistake so thats ok now.[/QUOTE]
 Yes that is what sudo doest basically, wich you find a problem.
You can exclude commands from sudo  [notice the input ALL=ALL], or you can just assign a root password for you to know and remove the user from the sudo file.

---

