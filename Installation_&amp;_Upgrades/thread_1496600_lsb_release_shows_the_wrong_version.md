---
title: "lsb_release shows the wrong version"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by mondo1287 on 2010-05-29
I'm running Ubuntu Server and I'm trying to update it.  The system was originally running 8.10.  Right now the system still thinks it's on 8.10, so update-manager-core is trying to update it to 9.04.  However, every package on the system is the 9.04 version, so it doesn't update anything, and I can't get to anything newer.

How can I convince the system that it is really running 9.04 and not 8.10?

**apt-cache policy libc6**
libc6:
  Installed: 2.9-4ubuntu6.2
  Candidate: 2.9-4ubuntu6.2
  Version table:
 *** 2.9-4ubuntu6.2 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
        500 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) jaunty-updates/main Packages
        100 /var/lib/dpkg/status
     2.9-4ubuntu6 0
        500 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) jaunty/main Packages

**lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

 **uname -a**
Linux Lampuntu 2.6.28-18-server #60-Ubuntu SMP Fri Mar 12 05:41:54 UTC 2010 i686 GNU/Linux

---

### Post by mondo1287 on 2010-05-29
I finally got this resolved.  I manually edited /etc/lsb_release and /etc/issue to reflect 9.04.  I'm now able to upgrade to Karmic.

---

### Post by iWarior on 2010-06-14
In my point of view - it's not good solution...

I have this problem in my Ubuntu 8.10.

After I **do-release-upgrade** to 9.04 **lsb_release -a** showed 8.10. But kernel, sources.list and packages versions - from jaunty ...

This situation was repeated again when I upgraded to karmic..

Reinstalling **lsb-release** doesn't take effect.

How to fix it? :0)

---

### Post by realTHK on 2010-12-19
I had an Ubuntu 10.04, which I upgraded to 10.10.

It is basically OK, **lsb_release -a** shows 10.10 Maverick, but if I select System/About Ubuntu, that dialog shows 
*"You are using **Ubuntu 11.04** - the Natty Narwhal -** released in April 2011** and supported until October 2012." *  
:confused:

I wonder how that About Ubuntu works...

---

### Post by vandamme on 2011-01-24
"This version (Natty Narwhal) was released in April 2011, so its version number is 11.04."
 
I wondered about that, too. Apparently the help file was teleported back from the future. Too bad we can't get the full 14.10 version, which runs all Windows 8 programs.  :popcorn:

---

