---
title: "x2go update stalls"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by stever3 on 2014-04-03
I have used x2go for over a year on an ubuntu 12.04 pc.  Today, when applying updates the process hung on installing/upgrading x2goserver (4.0.1.14-0~842~ubuntu12.04.1).  The last line of the details is "*Cleaning up stale X2Go sessions.".  It stayed at this state for over 2 hours.  I killed the update rebooted and apt removed x2goserver.  I then attempted to install x2goserver again and failed at the same point.  I have been unable to find any solutions on  web.

---

### Post by shaun_ on 2014-04-03
same here. not sure what to do about this one as I've removed all the session files in ~/.x2go with no luck.

---

### Post by stever3 on 2014-04-03
I found another reference to this same problem at [http://www.openmutual.org/2014/04/broken-upstart-causes-internal-error-no-file-name-for-udev/](http://www.openmutual.org/2014/04/broken-upstart-causes-internal-error-no-file-name-for-udev/) .  Will be watching to see if a solution shows up there.

---

### Post by shaun_ on 2014-04-03
stopping the update leaves the packages unconfigured so ran

```

sudo dpkg --configure -a

```

```
978 pts/1    S+     0:00      \_ sudo dpkg --configure -a
 1038 pts/1    S+     0:00          \_ dpkg --configure -a
 1039 pts/1    S+     0:00              \_ /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/x2goserver.postinst configure 4.0.1.13-0~814~ubuntu12.04.1

```

Stalls there, killing the perl process just leaves it unconfigured as before.

EDIT:

OK, I've managed to get this sorted out now.

The x2goserver post installation script invoked the x2goserver daemon script in /etc/init.d.
This in turn invokes x2gocleansessions.

```

ps afx | grep x2goclean
 2880 ?        S      0:09 /usr/bin/perl /usr/sbin/x2gocleansessions
 5835 pts/1    S      0:09 /usr/bin/perl /usr/sbin/x2gocleansessions
27465 ?        S      0:08 /usr/bin/perl /usr/sbin/x2gocleansessions
 1109 pts/1    S      0:08 /usr/bin/perl /usr/sbin/x2gocleansessions
  863 pts/0    S+     0:00      |       |   \_ grep --color=auto x2goclean
10278 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions
13994 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions
15773 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions
24345 pts/0    S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions
24866 pts/0    S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions
  509 pts/2    S+     0:00 /usr/bin/perl /usr/sbin/x2gocleansessions

```

I killed the process with PID 509 (just one picked at random - I may have got lucky and just picked the right one)

```

sudo kill 509

```

This stopped the upgrade process for x2goserver.

Subsequently running sudo apt-get update followed by sudo apt-get upgrade, seemed to run through the upgrade without any problems.

---

### Post by indik on 2014-04-04
> **shaun_ said:**
> stopping the update leaves the packages unconfigured so ran  ```
 sudo dpkg --configure -a 
```  ```
978 pts/1    S+     0:00      \_ sudo dpkg --configure -a  1038 pts/1    S+     0:00          \_ dpkg --configure -a  1039 pts/1    S+     0:00              \_ /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/x2goserver.postinst configure 4.0.1.13-0~814~ubuntu12.04.1 
```  Stalls there, killing the perl process just leaves it unconfigured as before.  EDIT:  OK, I've managed to get this sorted out now.  The x2goserver post installation script invoked the x2goserver daemon script in /etc/init.d. This in turn invokes x2gocleansessions.  ```
 ps afx | grep x2goclean  2880 ?        S      0:09 /usr/bin/perl /usr/sbin/x2gocleansessions  5835 pts/1    S      0:09 /usr/bin/perl /usr/sbin/x2gocleansessions 27465 ?        S      0:08 /usr/bin/perl /usr/sbin/x2gocleansessions  1109 pts/1    S      0:08 /usr/bin/perl /usr/sbin/x2gocleansessions   863 pts/0    S+     0:00      |       |   \_ grep --color=auto x2goclean 10278 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions 13994 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions 15773 ?        S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions 24345 pts/0    S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions 24866 pts/0    S      0:00 /usr/bin/perl /usr/sbin/x2gocleansessions   509 pts/2    S+     0:00 /usr/bin/perl /usr/sbin/x2gocleansessions 
```  I killed the process with PID 509 (just one picked at random - I may have got lucky and just picked the right one)  ```
 sudo kill 509 
```  This stopped the upgrade process for x2goserver.  Subsequently running sudo apt-get update followed by sudo apt-get upgrade, seemed to run through the upgrade without any problems.    Thank you this, did the trick for me. I only had 2 /usr/sbin/x2gocleansessions running so killed them both and boom update/upgrade worked. Cheers.

---

### Post by stever3 on 2014-04-04
This solution worked for me as well - thanks.

---

