---
title: "can't install or uninstall arson"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by MarkHn on 2006-04-20
Any ideas how to get rid if this package. I tried to install it using apt-get install arson.    It didn't install properly. Now I can't remove it either. using apt-get remove.
Now every time I run apt-get upgrade I get the following error.

root@Amilo:/home/ted# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up arson (0.9.8beta2-4.2ubuntu1) ...
No theme index file in '/usr/share/icons/locolor'.
If you really want to create an icon cache here, use --ignore-theme-index.
dpkg: error processing arson (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 arson
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Amilo:/home/ted#

---

### Post by sbassett on 2006-04-21
[QUOTE=the_matador0]I tried with your code and this happened:
W: No se puede leer la lista de paquetes fuente [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No existe el fichero o el directorio)
W: No se puede leer la lista de paquetes fuente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No existe el fichero o el directorio)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/QUOTE]


Mark -

I experienced the same issue. However arson seems to have installed fine for me, the only thing I use it for, however, is ripping CDs. Uninstall seems to work from synaptic, also have you tried:

```
sudo dpkg -r arson
```

?????

---

### Post by MarkHn on 2006-04-21
No I tried that and it didn't work. It's the 64 bit version if that makes any difference.

ted@Amilo:~$ sudo dpkg -r arson
Password:
(Reading database ... 199401 files and directories currently installed.)
Removing arson ...
No theme index file in '/usr/share/icons/locolor'.
If you really want to create an icon cache here, use --ignore-theme-index.
dpkg: error processing arson (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 arson
ted@Amilo:~$

---

### Post by ebtech on 2006-04-21
I have the same problem and that fix didn't help?? any other suggestions????? thanx

---

### Post by sbassett on 2006-04-22
OK, A really cheesy work-around.

```
cd /usr/share/icons/locolor/
```

then

```
sudo ln -s ../hicolor/index.theme .
```

I am fairly sure this will create an almost useless locolor theme set, but I never used that theme anyway, and arson installs fine.
Of course, if a REAL fix comes around, this link  /usr/share/icons/locolor/index.theme can always be removed.

---

### Post by ebtech on 2006-04-23
thankyou this helped me a lot.  I want to learn how to do these work arounds and things too but just can't seem to find out a way to learn all this programming without having to pay a lot of money.  I am married with 4 kids and would luv to be programming for a living instead of working at a meat packing plant. :( If anyone can tell me of a way to take lessons on linux programming without having to pay a fortune since I can't afford regular schooling, I would be much appreciative.  thankyou.

---

### Post by sbassett on 2006-04-23
ebtech -

There would be one great place to start.

[http://www.linuxtopia.org/index.html]("http://www.linuxtopia.org/index.html")

This has a great collection of online books. It's not a be all end all replacement for education ($$$), but it is a great start. Lot's of good stuff there.

---

### Post by MarkHn on 2006-04-23
Thanks for the fix, it worked great. 
Maybe part of the problem was that arson is a KDE package and I'm using GNOME. It's finally uninstalled now and there are lots of other cd ripping programs that work with gnome.
 
ebtech, 
it just depends on how interested you are in learning programming. It doesn't have to cost much at all. I presume you already have a computer and internet access, that's the biggest expense over. I have a BEng. in software engineering and an MEng in computers but sometimes I still get stuck on little things like that bug. Nobody knows everything, but that's what fourms are for: to share knowlwdge and solve problems. 
That is an excellent link above for learning LINUX.
I recommend a good book on C or C++ and a computer networking (tcp/ip) book for background information. Any book by 'Andrew Tanenbaum' or 'William Stallings' are excellent books, they are standard university text books in computer science courses. Schildt, 'A Beginners Guide to C++", is a very good introduction to C++ he also has one for C. 
Some of newest editions of some of these books can be expensive, $50 to $120. I buy a lot of books on Amazon or ebay that are used or are the older editions. There is almost no difference between the newest edition and older editions except price. You can get most of them for $10 to $20.
It really just comes down to putting in the time and work. It can be tough at times, but if you like working with computers, it's worth it. 
Good Luck!

---

### Post by siucdude on 2006-04-23
this worked thank you

---

