---
title: "Step by Step, Checklist for Server 10.04 Install"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by macmike on 2010-05-09
Is there such a thing as a step by step - Ubuntu 10.04 Lamp Server install procedure? I started out installing Ubuntu Desktop wanting a graphic interface to install with rather than command line. I guess was a mistake. I am wanting to setup a Web Server for 2 websites - [www.wilmingtoncoc.com]("http://www.wilmingtoncoc.com") and [www.mikealrhughes.com]("http://www.mikealrhughes.com") and 1 mailman mailing list. Can someone provide me a step by step and do these settings to get the thing running and get FTP and some kind of control panel going? I also want to use WordPress for the wilmingtoncoc.com site. Any help appreciated. Wished I had an Ubuntu expert close at hand. This install is all that will be on this box. 

Mike Hughes

---

### Post by utnubuuser on 2010-05-09
Try the turnkeylinux site. Preconfigured Ubuntu servers and good documentation.

---

### Post by garry.donnelly on 2010-05-10
Installing Ubuntu server is easy.  [Thirty Screenshots to Install Ubuntu 10.04 Lucid Lynx Server]("http://www.greatwhiteit.com/web/guest/technology-blog/-/blogs/thirty-screenshots-to-install-ubuntu-10-04-lucid-lynx-server").  Along the way you can install the LAMP stack then you can install the Ubuntu GUI (Gnome) if you wish once the server is up and running.  There are good instructions to install Wordpress on the LAMP stack on the wordpress.org site.  For better performance you can try running Ubuntu in a headless configuration.

---

### Post by boon4376 on 2010-05-11
I have a step by step process of installing a lamp server on an Ubuntu machine 10.04 Lucid Lynx to be exact. Pictures for every step included. (phpmyadmin install instructions included)

[How to install a LAMP server on Ubuntu 10.04]("http://alilknowhow.com/2010/05/11/the-easiest-way-to-install-a-lamp-server-in-ubuntu/")

This will get everything running exactly the way you need it to in order to download a copy of wordpress and get it running. I guarantee no errors or troubleshooting :D

Enjoy :)

---

### Post by phillw on 2010-05-14
> **boon4376 said:**
> I have a step by step process of installing a lamp server on an Ubuntu machine 10.04 Lucid Lynx to be exact. Pictures for every step included. (phpmyadmin install instructions included)

[How to install a LAMP server on Ubuntu 10.04]("http://alilknowhow.com/2010/05/11/the-easiest-way-to-install-a-lamp-server-in-ubuntu/")

This will get everything running exactly the way you need it to in order to download a copy of wordpress and get it running. I guarantee no errors or troubleshooting :D

Enjoy :)

Please just use tasksel for installing LAMP, that's what it's there for. Putting on phpmyadmin with syanaptic also ensures that it is seemlessly integrated. No ypos, copying & pasting required. the third part of that thread deals with a couple of differences with the 10.04 version of php.ini as shipped.

[http://forum.phillw.net/viewtopic.php?f=4&t=4](http://forum.phillw.net/viewtopic.php?f=4&t=4)

Regards,

Phill.

---

### Post by drdos2006 on 2010-05-14
Try this.
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

I found it really useful.
regards

---

