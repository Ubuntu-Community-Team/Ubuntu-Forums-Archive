---
title: "Installing intel gma ubuntu 13.04 problem please any solutions?"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by vincanity84 on 2013-09-27
[COLOR=#000000]I have a problem installing intel gma on my dell latitude atg d630. Ubuntu runs very slow i think its duo the lack of a graphic drivers. I red this page[/COLOR]
[http://www.ubuntugeek.com/how-to-ins...ntu-13-04.html]("http://www.ubuntugeek.com/how-to-install-intelr-linux-graphics-drivers-on-ubuntu-13-04.html")

[COLOR=#000000]and after instaling deb package x86 intel gma i try to run a command in terminal [/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Tahoma]

intel-linux-graphics-installer

but it fails after a couple of seconds and it gives me this

[/FONT][/COLOR][/COLOR][COLOR=#000000]Error running transaction: GDBus.Error[/COLOR]:eek:[COLOR=#000000]rg.debian.apt.TransactionFailed: error-dep-resolution-failed: The following packages have unmet dependencies:[/COLOR]


[COLOR=#000000]libgles1-mesa: Depends: libglapi-mesa (= 9.0.3-0ubuntu1) but 9.1.3-0ubuntu0.3 is to be installed[/COLOR]
[COLOR=#000000]libgles2-mesa: Depends: libglapi-mesa (= 9.0.3-0ubuntu1) but 9.1.3-0ubuntu0.3 is to be installed[/COLOR]


[COLOR=#000000]What should I do? How can I install that drivers?[/COLOR]

[COLOR=#000000]Tnx[/COLOR]

---

### Post by ibjsb4 on 2013-09-27
> [COLOR=#000000]libgles1-mesa: Depends: libglapi-mesa (= 9.0.3-0ubuntu1) [/COLOR]

This is a Quantal package and not available in Raring.

[http://packages.ubuntu.com/quantal-updates/libglapi-mesa](http://packages.ubuntu.com/quantal-updates/libglapi-mesa)

You can try replacing it, but ..

 [COLOR=#ff0000]**Warning:- After installing these drivers your system may be unusable so install them with your own risk**[/COLOR]

Thats from your driver link.  I think your in the process of opening up a can of worms. In other words, I would first look for other options.

How much ram do you have?  Ubuntu 12.04 has a 2d mode, you may be better off going that route.  

Wait for other to reply that have driver experience with your graphics (I do not).

Good luck and welcome to the forums :)

---

### Post by vincanity84 on 2013-09-27
Tnx for the fast answer:) I have a 3gb of ram. But when i press on home button it opens very slow. Its dual core processor, and should be faster I think:)

---

