---
title: "LAMP on Ubuntu Desktop without Internet"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by jorgerosa on 2007-02-12
This question is very simple, and is one big question in all community,
but with no valid answers.

**[COLOR="Red"]1)[/COLOR]** I installed [COLOR="Sienna"]Ubuntu Desktop[/COLOR] - Because all of the GUI. (For Noobs) Now...
**[COLOR="Red"]2)[/COLOR]** I want to install a [COLOR="Sienna"]LAMP Server[/COLOR] (NO Xampp - it´s easy, but i prefer the native LAMP Ubuntu Server)
**[COLOR="Red"]3)[/COLOR]** I have [COLOR="Sienna"]NO internet connection[/COLOR] avaible (I have but i want to install all this WITHOUT using it, all i want its put all this stuff working using ONLY all this software in previous recorded CDs)

Please note: This big question it´s NOT only mine but thounsands of people in the community.
Simple answers will help me, i thanks for that, but you will be also helping lots of people.
Also note, for example, is this excellent tutorial: [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)
Here is a similar solution (very well explained and documented by the author).
BUT you install the LAMP, then the GUI (ubuntu desktop) and you must have internet connection avaiable. This is NOT the case that my question is about.

THANKS TO ALL.

---

### Post by kidders on 2007-02-12
Hi there,

I may not be understanding you correctly, but unless something has changed since the last time I installed Ubuntu, you _don't_ need an internet connection to do it.

---

### Post by jorgerosa on 2007-02-12
Thx. Kidders. Thats great! So, i should... how?... yes?... :confused:

---

### Post by kidders on 2007-02-12
Hey again,

Are you having some kind of problem with the installation?

---

### Post by jorgerosa on 2007-02-12
Hi kidders.
No i´m not. I´m just trying create here a step-by-step simple guide from who has the knowledge for that, installing in that order (first post). Will be usefull for me and lots of people. Thx for ask.

---

### Post by kidders on 2007-02-12
Ohhh, so it's not the actual installation you're worried about ... you're wondering about configuring things like web servers without support software like Webmin?

The way to configure applications like iptables, apache2, postfix, php, mysql, etc. is pretty standardised across most distributions. The developers' sites usually describe what's involved in far greater detail than I could. In each case, you need to be familiar with how any configuration files are formatted though, since you'll often have to edit them yourself.

---

### Post by jorgerosa on 2007-02-12
"web servers without support software like Webmin"
No, it´s not. Of course i´ll need Webmin and/or phpMyAdmin, etc. (im new on linux and configurating a server). But that is not the question about. Thx.

---

### Post by kidders on 2007-02-13
> **jorgerosa said:**
> Of course i´ll need Webmin and/or phpMyAdmin, etc.Afaik you can't have them without an internet connection. :confused:

If you're referring specifically to LAMP installation, following existing HOWTOs should walk you through it. As far as I remember (it's been a little while), you just boot from the CD, answer a few questions, and you're done.

If there is something specific I can help with, I'd be glad to though. Perhaps there is some software you feel is essential, that isn't on the CD.

---

### Post by jorgerosa on 2007-02-13
"some software you feel is essential, that isn't on the CD" - **Right!**
If i have Ubuntu **desktop** CD, i haven´t Server Software on this CD.
So i´ve installed the Desktop. Now i want install LAMP from Ubuntu Server CD, what should i do?

---

### Post by jorgerosa on 2007-02-14
Please, can anyone help on this topic? Thx.

---

### Post by kidders on 2007-02-14
Ahhh. I've had trouble understanding exactly what you're looking for in this thread. My fault ... sorry. Now I think I'm with you. :-)

If you want LAMP *and* desktop-style software together on the same machine, and you don't have ready access to an internet connection, installing the desktop version from CD first is probably the easier option. That way, there is less software you need to worry about getting hold of. You basically have two options:

**I - Use a friend's internet connection**
Linux software is heavily modularised. In practice, applications tend to share bits of eachother, so there is very little duplication of function, tremendous stability/security, and post-install updates are very quick & easy. The downside (and it's a major one!) is that installing an application is almost never as simple as double-clicking an installer app.

To install PHP/MySQL/Apache by downloading the .debs at a net cafe, or a friend's house, you need to make sure that you have the relevant packages _and their dependencies_.

**II - Use the Ubuntu LAMP install disc**
Ubuntu's LAMP installer obviously has PHP/MySQL/Apache & dependencies on it already. If you have both the desktop & server install discs handy, you can use the .debs from one to fill in the blanks in the other.

In either case, the following might be useful. Say I wanted to install Horde (something I don't already have and can therefore try out myself), a useful server app...

```
$ sudo apt-get install horde3 -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  php-db php-http php-log php-mail php-net-smtp php-net-socket php-pear php-xml-parser php4-common php4-pear
Suggested packages:
  imp4 turba2 php4-cli gollem webcpp chora2 xlhtml ppthtml wv source-highlight rpm php4-mhash php4-sqlite php5-sqlite php-mdb2
Recommended packages:
  php-file php-date php-mail-mime php-services-weather php4-gd php5-gd php4-gd2 php4-mcrypt php-auth-sasl
The following NEW packages will be installed:
  horde3 php-db php-http php-log php-mail php-net-smtp php-net-socket php-pear php-xml-parser php4-common php4-pear
0 upgraded, 11 newly installed, 0 to remove and 56 not upgraded.
Inst php-pear (5.1.6-1ubuntu2.1 Ubuntu:6.10/edgy-security)
Inst php-db (1.7.6-2 Ubuntu:6.10/edgy)
Inst php-http (1.3.6-2 Ubuntu:6.10/edgy)
Inst php-mail (1.1.6-2 Ubuntu:6.10/edgy)
Inst php-net-socket (1.0.6-2 Ubuntu:6.10/edgy)
Inst php-net-smtp (1.2.6-2 Ubuntu:6.10/edgy)
Inst php-xml-parser (1.2.6-2 Ubuntu:6.10/edgy)
Inst php4-common (4:4.4.2-1.1 Ubuntu:6.10/edgy)
Inst php4-pear (4:4.4.2-1.1 Ubuntu:6.10/edgy)
Inst php-log (1.9.6-1 Ubuntu:6.10/edgy)
Inst horde3 (3.1.3-1 Ubuntu:6.10/edgy)
Conf php-pear (5.1.6-1ubuntu2.1 Ubuntu:6.10/edgy-security)
Conf php-db (1.7.6-2 Ubuntu:6.10/edgy)
Conf php-http (1.3.6-2 Ubuntu:6.10/edgy)
Conf php-mail (1.1.6-2 Ubuntu:6.10/edgy)
Conf php-net-socket (1.0.6-2 Ubuntu:6.10/edgy)
Conf php-net-smtp (1.2.6-2 Ubuntu:6.10/edgy)
Conf php-xml-parser (1.2.6-2 Ubuntu:6.10/edgy)
Conf php4-common (4:4.4.2-1.1 Ubuntu:6.10/edgy)
Conf php4-pear (4:4.4.2-1.1 Ubuntu:6.10/edgy)
Conf php-log (1.9.6-1 Ubuntu:6.10/edgy)
Conf horde3 (3.1.3-1 Ubuntu:6.10/edgy)
```
This is a pretty clear list of everything my specific machine would need access to, were I to actually install it. Whatever source I chose to use, I would now have a complete list of everything I needed.

---

### Post by jorgerosa on 2007-02-14
"If you have both the desktop & server install discs handy, you can use the .debs from one to fill in the blanks in the other." <-- Its this i want!

BIG THANKS KIDDERS! im trying your code now... :)

---

### Post by kidders on 2007-02-14
Yikes... sorry it took me so long to answer your question! :lolflag: @ me!

---

### Post by flardi on 2007-11-02
Check this out. It does exactly what you want.

[http://fslog.com/2006/12/01/setting-up-lamp-on-your-ubuntu-desktop/]("http://fslog.com/2006/12/01/setting-up-lamp-on-your-ubuntu-desktop/")

:) FL

---

