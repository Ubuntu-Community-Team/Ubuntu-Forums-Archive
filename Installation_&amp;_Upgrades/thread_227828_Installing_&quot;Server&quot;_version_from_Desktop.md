---
title: "Installing &quot;Server&quot; version from Desktop CD?"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by Jabran Asghar on 2006-08-02
Hi,

Using Dapper Desktop Live CD, is it possible to install server version (Just the simple text based server install, if LAMP not possible)? I assume that most of the server packages will already be includded in the Desktop CD.

I checked startup parameters when Booting from the CD, but apparently, could not find any server install options.


Thanks for any hints.

Jabran

---

### Post by az on 2006-08-02
The live cd does not have the option.  It is a previeously installed system that has been transplanted to disk and the installer transplants it back to your hard disk. 

The alternate cd as well as the server cd is different.  It is a package repository and an installer which installs those packages one-by-one.  That's why you get more options.

You can install the desktop and then 
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

and run a server.  This is against best-security practices, so don't use it in a production environment, but the packages do not interact or interfere/conflict with each other.  LAMP won't even know that a desktop is running and vice versa.

---

### Post by Jabran Asghar on 2006-08-02
Thanks for the reply. I guess I shall download the Server CD.

Thanks. :-)

---

