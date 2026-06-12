---
title: "Callweaver on 7.10 not installable ?"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by friedli on 2007-12-22
Hi all

I've been trying for the last 2 days to get T38 (Callweaver) working - using this helpsite:

[http://www.callweaver.org/wiki/CallWeaver+on+Ubuntu](http://www.callweaver.org/wiki/CallWeaver+on+Ubuntu)

But - all I get are messages such as

running aclocal ...
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'

The problem appears when I want to compile callweaver. It starts when I ./bootstrap it with messages such as:

configure.ac:610: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.ac:610: warning: AC_COMPILE_IFELSE was called before AC_AIX

Finally error 1 and no file is compiled and installed. I use:

Ubuntu server 7.10 without GUI (for safety reasons) on a Compaq Proliant Server
spandsp 0.0.4
callweaver rc-15
Hylafax

the newest versions.

I know there is some hints on the net but no real indication on where the error sits. 

Note: I don't have a modem installed yet and the machine is quite old, but nevertheless it should properly install.

This is the T38 part - Hylafax could be installed without problems.

Thanks for help - I'm a newbie on this. The final goal is to get the faxservice working under CommuniGate with Outlook Connector (THAT part is properly functioning for over 6 months now).

Jurg

---

