---
title: "Printer Driver Installation Problems Operator Error"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by Votlon on 2014-01-30
Sorry if i posted this question in the wrong forum, this is my first post ever for ubuntu :3 

None the less i'm having an issue with my CANNON MG5420 PIXMA printer. I downloaded the mg5400 seires printer driver from the [cannon website]("http://support-au.canon.com.au/contents/AU/EN/0100467602.html") (at the very bottom it says download). I have unpackaged the tar.gz file and used the install.sh to install the printer but nothing happens. 

This is probably a noob question but I am new to linux in general so any help would be really appreciated!

---

### Post by efflandt on 2014-01-30
Did you get any error when you tried to run the install.sh? Most likely you need to do it as root by using sudo, and the install.sh is not in your $PATH, so you need a "./" prefix to run it from current directory.

**cd** to the directory containing install.sh and then do:```
sudo ./install.sh
```

---

### Post by Votlon on 2014-02-04
I did the ./install.sh and i got this error log

> ==================================================

Canon Inkjet Printer Driver
Version 3.80
Copyright CANON INC. 2001-2012
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.80-1_amd64.deb
dpkg: error processing ./packages/cnijfilter-common_3.80-1_amd64.deb (--install):
 cnijfilter-common: 3.80-1 (Multi-Arch: no) is not co-installable with cnijfilter-common:i386 3.80-1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.80-1_amd64.deb
Command executed = sudo dpkg -P cnijfilter-common
dpkg: warning: there's no installed package matching cnijfilter-common


---

### Post by Votlon on 2014-02-05
Still no one know? :(

---

