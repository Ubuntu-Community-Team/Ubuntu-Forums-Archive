---
title: "Psybnc Installation"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by TekZonz on 2005-06-06
Hello,

I am trying to install psyBNC on my home server which is running Ubuntu. The only problem is that I get the following error when I try to "make menuconfig":

tekzone@server:~/psybnc $ make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
make: gcc: Command not found
make: *** [menuconfig] Error 127

How do I get PsyBNC to work?

Thanks in advance,

Antoine "TekZone" Benkemoun

---

### Post by TekZonz on 2005-06-06
Also, I tried to install another IRC Bouncer software named Night Light IRC Proxy and go the following error with I tried to "./configure"

[email]tekzone@server:~/ircproxy-1.2.41d.pl[/email]4 $ ./configure
*-----------------------------------------------------------------------------
* Night Light IRC Proxy system configuration script
* Copyright (C) 2001-2003 Jonas Kvinge <jonas@night-light.net>
*-----------------------------------------------------------------------------
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

It's obviously a compiler error but I have no idea of how to fix it.

Thanks in adavance

---

### Post by TekZonz on 2005-06-08
Help me plz :'(

---

### Post by madmonk3y on 2007-06-12
[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

