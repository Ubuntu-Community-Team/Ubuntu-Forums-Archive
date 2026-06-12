---
title: "New Userids Limited To Lowercase"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Kay-Sugg on 2007-09-05
_   I have just received a new laptop with Ubuntu installed. Unfortunately, the system refuses to accept my userid (Kay-Sugg) during the first startup. Please confirm the following :
1) that this is an intentional feature (lowercase userids required) of the Ubuntu distro; and 
2) that there isn't a workaround (other than switching to another distro).
[FYI - My SUSE 9.1 workstation (circa 2004) does not have this limitation.]
Thanks,
Kay-Sugg
P.S. I am NOT a worshiper of e e cummings.

---

### Post by wonk-o-matic on 2007-09-05
It's a feature of the GNOME interface in ubuntu.  When I use a root console and the adduser command, or the KDE interface, I can use uppercase.

---

### Post by Kay-Sugg on 2007-09-05
_   Thank you. I'll contact my supplier and either get Kubuntu or instructions on flipping my system over to KDE. I prefer KDE's Go-Nogo button order to Gnome's Nogo-Go.

---

### Post by Kay-Sugg on 2007-09-10
_   What worked - WebMin ([http://www.webmin.com/](http://www.webmin.com/)).
_   What didn't work : root and KDE.
_   I followed the instructions that I was given and installed the KDE desktop package (kubuntu-desktop.deb) but that left me with a nasty hybrid of Ubuntu and Kubuntu. [The Gnome garbage is still running my system even though I have the Kubuntu start-up splash.]

Final words : Bye bye Ubuntu/Kubuntu. Even after a second "dpkg-reconfigure kdm" and a re-boot I still didn't have the full KDE effect (kcontrol choices were not showing up). Tack on the insulting nag message that is a part of Ubuntu's "su" command and I went for the "rm --force -R *" command.

P.S. While I'm new to Ubuntu, I've spent quite a lot time with Mandrake 9 and SUSE 9.1.

---

