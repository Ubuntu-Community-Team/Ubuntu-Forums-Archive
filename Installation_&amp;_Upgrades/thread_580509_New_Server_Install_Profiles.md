---
title: "New Server Install Profiles?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by thelorax on 2007-10-18
So I see that one of the new highlights of 7.10 is additional server install profiles - file server, mail server, etc.  Does anyone know what's actually included in any of these profiles?  It seems rather odd that they advertise it in the "tour" on the main ubuntu site, but don't really tell you anything about it.  I'm interested in setting up a samba file server.

---

### Post by hEKiM13 on 2007-10-19
I am also very interested in finding out what is installed with the Samba File Server. I installed it last night, but because I'm a real newbie I have no idea how to set up the Samba server and users without the GUI. I'd really like to learn how to set up the server without the GUI, so any help would be greatly appreciated. Thanks!

---

### Post by thelorax on 2007-10-20
Well I gave it a shot - basically you can now pick which server(s) you want installed - DNS, LAMP, SSH, File Server, Postgre Database, Print and Mail - you can select one or more, so it's not an either/or choice.  I did SSH, Print and File Server and it installed just fine.  It is a no-frills install, so don't expect any GUI stuff (but then it's supposed to be a server, so makes sense - you could do this with your desktop install too though).  If you aren't an experienced user, I would highly recommend installing Webmin so you can have a (web based) GUI to help you along.  

I installed Webmin as follows:
(Borrowed from [http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html") and [http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html]("http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html"))

Make sure you've got some pre-requisites taken care of:
```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

Then grab the latest version of Webmin from their website - [http://www.webmin.com/download.html](http://www.webmin.com/download.html) - you'll want the .deb one.  Right now the latest one is webmin_1.370_all.deb Your new Ubuntu server doesn't have a browser, so grab it with wget
```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb
```

Finally install the package:
```
sudo dpkg -i webmin_1.370_all.deb
```

And you're all set.  You can now access Webmin by going to [https://[serverIP]:10000](https://[serverIP]:10000) (that's port 10,000) You should be able to log in as the user you created during install.

If you want to change the webmin password to be different than your administrative user account, run
```

sudo /usr/share/webmin/changepass.pl /etc/webmin root [desired password]
```

If you want to have a slicker looking theme, I'd suggest the "Stress Free" them from [www.stress-free.co.nz/webmin-theme]("http://www.stress-free.co.nz/webmin-theme")

How about for 8.04 Ubuntu adds an option to install Webmin right in the server install routine - give it a nice Ubuntu theme and with little effort Ubuntu server setup becomes a lot easier for non-experts.

-----------
Note to any totally new people trying to setup their first Samba file server, you'll need to create the desired shares AND setup the desired Samba users - just creating a normal unix user isn't enough, you'll need a matching samba user before you can actually connect your Windowx PC. As mentioned, check out Webmin if you're totally lost - it can help you with both tasks.

---

