---
title: "VMware Server"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by ljones on 2006-04-19
I recently tired to put on VMware Server Beta.  I downloaded the tar file, did the whole tar xzf blah blah blah...

Anyway, when I went to install the vmware-install.pl it got through the End User Agreement, and then it kicked out of the installer.  When I went back and tried to re-run the vmware-install.pl I get the error : "A previous installation of VMware software has been detected".  When I try to uninstall vmware I get the error : &#8220;Uninstalling the tar installation of VMware Management Interface.  Unable to find the answer INSTALLDIR in the installer database (ect/vmware-mui/locations).  You may want to re-install VMware Management Interface.  Execution aborted."

Any idea on what actually happened and how to get rid the vmware installation??
	
Thanks,
Luke

---

### Post by hvar on 2006-05-03
Hi Luke.

This should do the trick
```
sudo /usr/bin/vmware-uninstall.pl
```

---

### Post by jbaloul on 2006-05-11
Take a look at this:
HowTo Install VMware Server on Ubuntu

[http://howtoforums.net/viewtopic.php?t=5](http://howtoforums.net/viewtopic.php?t=5)

Enjoy!

---

### Post by bobc on 2006-06-26
Love the search in this bbs :mrgreen: 

This should do the trick
Code:

sudo /usr/bin/vmware-uninstall.pl

Worked wonderfully, thanks ;)

---

