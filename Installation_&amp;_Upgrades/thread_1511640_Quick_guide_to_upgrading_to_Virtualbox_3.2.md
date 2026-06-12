---
title: "Quick guide to upgrading to Virtualbox 3.2"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by rvndmnmt on 2010-06-17
Sorry if this has been posted before.  Couldn't find it myself when I looked.  

The purpose behind this was simply to upgrade the most used tool in my arsenal.  Couldn't use the debian package manager.  There seemed to be this conflict with V 3.1 going into the light.  Did a little digging on the net and pieced this together.  This is primarily for noobs such as myself just in case there is another lost soul out there on the web.

First you want to update your sources.  Type the following command:

sudo gedit /etc/apt/sources.list

Then enter the following and save in your sources list:

deb [http://download.virtualbox.org/virtualbox/debian]("http://download.virtualbox.org/debian") lucid non-free

The non-free meaning that it is not officially supported.  Not that it's going to cost you some dough.

I tried adding the key then downloading but hit a wall for some reason.  So I used this command to combine the both.  Lo and behold the heavens parted, angles blew their horns, and it worked.

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

That, by the way, is an O and not a zero.  Just in case it's one in the morning and you have to be up in four hours ;\

Then follow up with the:

sudo apt-get update
sudo apt-get install virtualbox-3.2 

commands.  Let the coffee percolate a bit.  And before you know it you have a functioning updated version of Virtualbox 3.2.4.

*Thanks for pointing that out Southy.  Looks like I am going to need to up the caffeine intake if I do anymore posting at o'god thirty in the morning again lol.*

---

### Post by Southy_ on 2010-06-18
this line: deb [http://download.virtualbox.org/debian](http://download.virtualbox.org/debian)  lucid non-free
should be: deb [http://download.virtualbox.org/virtualbox/debian]("http://download.virtualbox.org/debian")  lucid non-free

Thanks for the guide :)

---

