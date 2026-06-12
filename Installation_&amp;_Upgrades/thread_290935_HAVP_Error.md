---
title: "HAVP Error"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by PrinceArithon on 2006-11-01
Ok I have a problem with my havp package.  When I download something I get and error, in this error it talks about something or another as a possibility to do to fix it, and tried it and it still doesn't work.  I'll show you all in a second.  The thing is this.  Sometimes when I download something, it downloads, and sometimes it doesn't.  So I don't like this.  Can anyone help me out??  Here is what it looked like as I tried to download and install Thunderbird.

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main mozilla-thunderbird 1.5.0.7-0ubuntu1 [10.7MB]
Fetched 10.7MB in 5m9s (34.7kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 128498 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb) ...
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open logfiles!
Invalid permissions? Maybe you need: chown havp /var/log/havp
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mozilla-thunderbird (1.5.0.7-0ubuntu1) ...

Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
admin@Fingolfin:~$ chown havp /var/log/havp
chown: changing ownership of `/var/log/havp': Operation not permitted



Anyway can anyone help me??

---

### Post by NetworkGuy on 2006-11-01
Maybe put sudo in fromt of that command

sudo chown havp /var/log/havp

---

### Post by PrinceArithon on 2006-11-01
Hey thanks for the suggestion...didn't work though..well the error report looks different now.  Here it is.

Reading package lists... Done
Building dependency tree... Done
dnsmasq is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open logfiles!
Invalid permissions? Maybe you need: chown havp /var/log/havp
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)


Again I need a bit of some help

---

### Post by NetworkGuy on 2006-11-01
Do you have ClamAV installed?  This HAVP is an antivirus proxy used by ClamAV.  I am running thunderbird but not CLamAV and didn't run into this.

Maybe remove ClamAv (and HAVP).  Install Thunderbird and then try to reinstall ClamAV.

---

### Post by PrinceArithon on 2006-11-02
Actually it's not HAVP it's havp.  I do not have this antivirus program installed at all.  It has to do with downloading and installing packages this one.

also as for the ClamAV I don't have it either.



EDIT: Actually I do have ClamAV and this is all part of what is going on.  My question is how do I remove it safely??  I really don't want to mess something up, because I don't know how this program digs into the system.

---

