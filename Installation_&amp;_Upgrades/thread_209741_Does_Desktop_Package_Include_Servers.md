---
title: "Does Desktop Package Include Servers"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by stephen67 on 2006-07-05
I want to set up a LAMP server but also have a user machine.

Am I better to install the desktop or the server package?

Is there a roadmap for where I am going?

The server will be on a private network behind a firewall.

Thank you!
Stephen

---

### Post by mscman on 2006-07-05
Just do a normal Desktop install and install the server packages later, since it seems you would also like to just run a regular desktop machine.  That's what I did on my web/file server. (and what many people on here will recommend...)

---

### Post by stephen67 on 2006-07-05
That was easy!

Thank you. All servers installed.

I just have to figure out the config problems with SMB.

I can see the Ubuntu machine in my network, but it won't allow a connection.

---

### Post by lulucamargo on 2006-07-06
I don't know anything about networking, but this seems similar to what I'm trying to do:
I have a Ubuntu Laptop and a Windows desktop, the latter connected to the internet and acting as router/gateway. No problems making the linux machine talk to the windows machine.

 How can I have the desktop running linux and acting as a gateway? Do I have to install these server packages? Where can I find these server packages? Can I install them from a repository or must I have the server instalation CD?

---

### Post by ds2719 on 2006-07-06
So how did you get the server pacages.  Did you install the "server" version on top of "desktop"?

---

### Post by az on 2006-07-06
[QUOTE=stephen67]I want to set up a LAMP server but also have a user machine.

Am I better to install the desktop or the server package?

Is there a roadmap for where I am going?

The server will be on a private network behind a firewall.

Thank you!
Stephen[/QUOTE]
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Install the LAMP packages from main:
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Then, set the mysql root password:

mysql -u root

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');


What web applications do you want to run?

---

### Post by az on 2006-07-06
[QUOTE=lulucamargo]I don't know anything about networking, but this seems similar to what I'm trying to do:
I have a Ubuntu Laptop and a Windows desktop, the latter connected to the internet and acting as router/gateway. No problems making the linux machine talk to the windows machine.

 How can I have the desktop running linux and acting as a gateway? Do I have to install these server packages? Where can I find these server packages? Can I install them from a repository or must I have the server instalation CD?[/QUOTE]
you don't need to run a LAMP server to share files or to share an internet connection.

Sharing a net connection is called IP masquerading and I think firestarter can do that for you.

[https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html)

Sharing files is done with Samba.  The samba client is already installed.  To allow other computers to share your files, install the samba server.

---

