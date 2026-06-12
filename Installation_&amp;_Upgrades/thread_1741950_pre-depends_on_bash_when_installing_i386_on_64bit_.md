---
title: "pre-depends on bash when installing i386 on 64bit 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by partyk1d24 on 2011-04-28
Here is a copy of what shows on by screen (I used sudo -s because I thought it might be an environment issue). Not sure what to do here Bash seems to be installed and if I run bash I get no errors. I did just upgrade to 11.04.

```
root@jackie-Latitude-E6410:~/Downloads/SametimeStandardClient/sametimeclient.standalone/Linux# dpkg --force-architecture -i sametime-connect-8.5.1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding sametime-connect-8.5.1.i386.deb containing sametime-connect:i386, pre-dependency problem:
 sametime-connect:i386 pre-depends on bash
dpkg: error processing sametime-connect-8.5.1.i386.deb (--install):
 pre-dependency problem - not installing sametime-connect:i386
Errors were encountered while processing:
 sametime-connect-8.5.1.i386.deb

```

Thanks guys

Jackie

---

### Post by partyk1d24 on 2011-04-28
It threw me exceptions for both xterm and bash, however, anyone else trying to install sametime should note it works if you just ignore dependancies.

```
root@jackie-Latitude-E6410:~/Downloads/SametimeStandardClient/sametimeclient.standalone/Linux# dpkg --force-architecture --force-depends -i sametime-connect-8.5.1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding sametime-connect-8.5.1.i386.deb containing sametime-connect:i386, pre-dependency problem:
 sametime-connect:i386 pre-depends on bash
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding sametime-connect-8.5.1.i386.deb containing sametime-connect:i386, pre-dependency problem:
 sametime-connect:i386 pre-depends on xterm
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 185535 files and directories currently installed.)
Unpacking sametime-connect:i386 (from sametime-connect-8.5.1.i386.deb) ...
dpkg: dependency problems prevent configuration of sametime-connect:i386:
 sametime-connect:i386 depends on libx11-6.
 sametime-connect:i386 depends on libxt6.
 sametime-connect:i386 depends on libxext6.
 sametime-connect:i386 depends on libc6.
 sametime-connect:i386 depends on libgcc1.
 sametime-connect:i386 depends on libgtk2.0-0.
 sametime-connect:i386 depends on libxkbfile1.
 sametime-connect:i386 depends on libglib2.0-0.
 sametime-connect:i386 depends on libstdc++6.
 sametime-connect:i386 depends on xterm.
 sametime-connect:i386 depends on bash.
 sametime-connect:i386 depends on bash.
 sametime-connect:i386 depends on xterm.
dpkg: error processing sametime-connect:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sametime-connect:i386

```

Despite all the uglyness works great!

---

