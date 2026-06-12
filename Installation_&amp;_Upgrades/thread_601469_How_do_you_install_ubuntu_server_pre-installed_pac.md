---
title: "How do you install ubuntu server pre-installed packages after running installation CD"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by obitori on 2007-11-03
I don't see the option screen where you select LAMP, samba and the other pre-configured Ubuntu server pacakges coming up when I install Gutsy off the CD I downloaded from ubuntu.com.

I have the base server install up and running.  Rather than reinstall, I am wondering if there is a way to install those pacakges from apt-get?  I don't think trying to "apt-get install" the various packages of mysql, php, apache will produce the same preconfigured setup.  

I previously used FreeBSD where you can invoke the installation cd menu by using the command:

sudo sysinstall

Is there something similar for Ubuntu server or is there a way that I can select these pre-configured packages with apt-get?

Many thanks!

Obitori

---

### Post by mikewhatever on 2007-11-03
Hope this will help [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by obitori on 2007-11-03
MikeWhatever:

Thanks for the link.  That certainly gets me up and running.  I am going to give it a try.

I am curious tho whether there is a way to go back and install the preconfigured packages that Ubuntu bundles with its server base install.  I suspect the tutorial that you provided the link for is not the same end result.  (That being said, it looks like a good approach, so I am going to give it a try.)

Obitori

---

### Post by obitori on 2007-11-05
So, there is no equivalent to the freebsd command:

sysinstall

to reenter the installation program and make configuration changes to the base installation?  That is too bad.  It would be nice to be able to add preconfigured LAMP and other packages that Ubuntu offers for the base server install.  Does anybody agree this is a good feature request for future installation CDs?

Obitori

---

