---
title: "How can I get rid of this update error?"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by kodachrome64 on 2007-01-07
How can I get rid of this update error?
I'm having problems updateing / upgrading to anything new. Using Synaptic Package Manager I get this error.

Synaptic Package Manager  : error

E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

The file the error references is located here. i have installed it and it seems to be working fine except for this error it produces via Synaptic Package Manager 

The file is located here.
/home/adam/Desktop/mfc4800lpr-1.1.2-1.i386.deb

I thought to resolve this by Upgrading to 6.10 Edgy but have similar errors

adam@ubuntu-macbook:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 71, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 749, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 599, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 716, in initCache
    self.cache._depcache.Init()
SystemError: E:The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.


How can i get rid of this update error?
I have tried

adam@ubuntu-macbook:~$ sudo apt-get -f remove
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.

&

adam@ubuntu-macbook:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
adam@ubuntu-macbook:~$


Help!

---

### Post by bapoumba on 2007-01-07
Hi,
may be these will help :
[http://www.ubuntuforums.org/showthread.php?t=92922]("http://www.ubuntuforums.org/showthread.php?t=92922")
[http://lists.debian.org/debian-user/2005/04/msg01317.html]("http://lists.debian.org/debian-user/2005/04/msg01317.html")

---

### Post by kodachrome64 on 2007-01-07
Thanks for the link. Seems to be the saem problem I have but the recomended fix didn't work for me.

I changed the "mfc4800lpr.postinst" file as noted and added the "exit 0" and commented out the other lines.

adam@ubuntu-macbook:/var/lib/dpkg/info$  cat mfc4800lpr.postinst
exit 0
#!/bin/sh
# ESP Package Manager v3.5.1
# /usr/local/Brother/inf/setupPrintcap MFC4800 -i USB
# /etc/init.d/lpd restart
adam@ubuntu-macbook:/var/lib/dpkg/info$

running "sudo apt-get remove --purge mfc4800lpr" still gets me the same error.

adam@ubuntu-macbook:/var/lib/dpkg/info$ sudo apt-get remove --purge mfc4800lpr
Reading package lists... Done
Building dependency tree... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
adam@ubuntu-macbook:/var/lib/dpkg/info$

What is it I'm doing wrong here?

---

### Post by kodachrome64 on 2007-01-07
OK,

I thnk I figured it out. I reinstalled the mfc4800lpr and then removed it.
I'm really new to this so I tried all kinds of other things and this simple solution worked for me in the end. I am now able to use Synaptic Package Manager and Update Manager with ut errors.

adam@ubuntu-macbook:/etc/init.d$ sudo dpkg -i /home/adam/Desktop/mfc4800lpr-1.1.2-1.i386.deb
(Reading database ... 78527 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using .../mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
Setting up mfc4800lpr (1.1.2-1) ...

adam@ubuntu-macbook:/etc/init.d$  sudo dpkg --purge mfc4800lpr
(Reading database ... 78526 files and directories currently installed.)
Removing mfc4800lpr ...
Purging configuration files for mfc4800lpr ...
adam@ubuntu-macbook:/etc/init.d$

---

