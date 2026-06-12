---
title: "downgrading libx11"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by spacefizzicist on 2007-04-23
Hi guys, I did an update of the x-server and the libX11 and many of the programs are broken (IDL or the interactive data language, can't open openoffice attachments ?!! etc.).
I was trying to get the workaround mentioned here to get rid of the segfault by downgrading ...
[http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177)
 How do I downgrade the x-server? I can't remember the version number, but this upgrade happened in the last week or so. So the version prior to that would be fine. I clean my cache sometimes, so I don't seem to have the debs. This is what I did:
```
$ sudo dpkg -i libx11-6_1.0.3-6_i386.deb
dpkg: regarding libx11-6_1.0.3-6_i386.deb containing libx11-6, pre-dependency problem:
 libx11-6 pre-depends on x11-common (>= 1:7.0.0)
  x11-common is installed, but is version 7.0.0-0ubuntu45.
dpkg: error processing libx11-6_1.0.3-6_i386.deb (--install):
 pre-dependency problem - not installing libx11-6
Errors were encountered while processing:
 libx11-6_1.0.3-6_i386.deb 
```

So I would like to downgrade from the current x11-common to the previous version. Btw, I am running Ubuntu Dapper. 
```
 $ dpkg --list x11-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  x11-common     7.0.0-0ubuntu4 X Window System (X.Org) infrastructure 
```

```
$ dpkg --list libx11-6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libx11-6       1.0.0-0ubuntu9 X11 client-side library
```

Thanks for your time and help!
/rk

---

### Post by floke on 2007-04-23
Not sure exactly how you do it, but you can get hold of the packages here...

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Also, for future reference you can try this to backup all your repository files - makes it easy to restore them.

[http://ubuntuforums.org/showthread.php?t=419466](http://ubuntuforums.org/showthread.php?t=419466)

---

### Post by alberto.m.vasquez on 2007-04-25
Hey!

Another space phycisist here.

I just posted in the Ubuntu formums seeking for help on the same issue
(IDL cant make TVs or SHADE_SURFs anymore!). According to this user bug report:
[https://bugs.launchpad.net/debian/+source/libx11/+bug/107732](https://bugs.launchpad.net/debian/+source/libx11/+bug/107732)
we should go back to libx11-6 (2:1.0.3-0ubuntu4)

I really do not know the package name or how to force this donwgrade with a  
aptitude or apt-get line. do you?

just in case, my email: [email]alberto.m.vasquez@gmail.com[/email]

thanks for any help, let you know if I solve it too.
Alberto.

---

### Post by alberto.m.vasquez on 2007-04-25
hey,
problem solved.
I went to [http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177),
dowloaded the package:  libx11-6_1.0.3-6_i386.deb
and then from the dir where that package is I did as
root the usual debian command:
 dpkg -i libx11-6_1.0.3-6_i386.deb

and now IDL can do all the graphs!

cheers!
Alberto.

---

