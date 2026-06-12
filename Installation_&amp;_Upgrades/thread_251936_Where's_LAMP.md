---
title: "Where's LAMP?"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by divali on 2006-09-06
I've just downloaded Dapper 6.06 from the server section of the Ubuntu site and I cant see LAMP in the installation dialogue. 
How can I install Lamp? Can anyone point me in the right direction?  Thanks.

---

### Post by az on 2006-09-06
Maybe you inadvertently downloaded the alternate or the desktop cd?

You can still install the LAMP stack from any ubuntu install.  Just install 

apache2 php5-mysql libapache2-mod-php5 mysql-server

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Exactly what options do you get when you boot the cd?

---

### Post by divali on 2006-09-07
% Start or install Ubuntu.
% Start in safe graphics mode.
% Check cd for defects.
% Memory test.
% Boot from hard drive.


And that's it.

---

### Post by CzarAlex on 2006-09-18
Definately sounds like the Desktop installation CD to me. Azz is right though, you can easially install the same services that the LAMP installation does by installing the packages he listed for you.

---

### Post by The_Apprentice on 2006-09-18
I have to confess I gave up trying to configure them all seperately.

If you want a quick and easy install you can ot do better than XAMPP - [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Please note, though, that it will not be auto-updated/patched.

---

### Post by kuririkura on 2006-09-18
Hi, abit OOT

Can i use desktop version to install the LAMP server version, i want to limit the resource for server such as no graphical thing...
Or i must use  the server version????

---

### Post by mixmaster on 2006-09-18
You can put LAMP on the desktop version, but you will get all the graphics pacakges etc.  You will also have to configure the lamp stack yourself.

If you download and burn the server install CD you will get a text-only system.  I believe it also has a differently optimised kernel.  One of the options on the server CD install is to install a LAMP server.  This gives you all the packages pre-configured and works immediately after reboot.

---

