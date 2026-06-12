---
title: "Perl module errors using CPAN"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Crucinator on 2006-07-19
I am trying to install [HoTTProxy]("http://www.hottproxy.org/"), and in order to do so I need to install a bunch of perl modules by using CPAN.  I tried follow the instructions from the HoTTProxy site ([http://www.hottproxy.org/articles/LinuxEtc.html](http://www.hottproxy.org/articles/LinuxEtc.html)) and from the Ubuntu Help site ([https://help.ubuntu.com/community/HoTTProxy)](https://help.ubuntu.com/community/HoTTProxy)), but both produced errors.  I documented which errors I got [here]("http://www.v710.org/forums/showthread.php?t=5258"), but that forum is quite dead so I figured someone here may be able to help.

Since then, I no longer get the "HTTP::Server::Simple::CGI" error, but I found out I was having trouble installing LWP and the HTTP-Daemon.  As "make install" was running for both modules, I would get many "FAIL" messages.  Also, the first time I tried to install the modules I was doing so as a standard user; so I tried again as root.  Now when I try and run "perl HoTTProxy_Admin.pl", I get the following response.

```
Can't locate Date/Calc.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at HoTTProxy/UI.pm line 5, <DATA> line 16.
BEGIN failed--compilation aborted at HoTTProxy/UI.pm line 5, <DATA> line 16.
Compilation failed in require at HoTTProxy_Admin.pl line 4, <DATA> line 16.
BEGIN failed--compilation aborted at HoTTProxy_Admin.pl line 4, <DATA> line 16.

```

Installing these modules is driving me nuts.  Can anyone help me out?

---

### Post by ginbas on 2007-07-18
I'm having the exact same issue. It runs fine on ubuntu 6.06.

---

### Post by ginbas on 2007-07-18
Found a resolution at this [http://ubuntuforums.org/showthread.php?t=485144](http://ubuntuforums.org/showthread.php?t=485144)

---

