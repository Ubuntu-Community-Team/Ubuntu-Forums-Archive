---
title: "LDAP Server on Ubuntu 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by bstear on 2009-11-17
I went through the process of doing an apt-get install slapd ldap-utils and setup my password.

Following the documentation at : [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html#openldap-server-installation](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html#openldap-server-installation) 

when I do a LDAPSEARCH I get the following error : ldap_result: Can't contact LDAP server (-1). 

I have been looking at this error for 2 days now. Most people online say to make sure that you have slapd running which it is. I also do not see any log for ldap even though within slapd.conf I made the log_level 256. 

I would appreciate any help because I am really at a loss for what it could be.  Thanks!

---

### Post by fbonjour on 2009-11-18
Yes, for some reason when you install slapd, apt-get does not prompt for the LDAP password (it should):

fbonjour@vm1 7 $ sudo apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,601kB of archives.
After this operation, 4,268kB of additional disk space will be used.
Get:1 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) karmic/main slapd 2.4.18-0ubuntu1 [1,601kB]
Fetched 1,601kB in 4s (368kB/s)  
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 43907 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.18-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up slapd (2.4.18-0ubuntu1) ...
  Creating new user openldap... done.
  Creating initial slapd configuration... done.
Starting OpenLDAP: slapd.

---

### Post by bstear on 2009-11-18
Thank you for your reply but I have setup the LDAP password. 

I ran dpkg-reconfigure slapd and set that up. 

Any other suggestions? Is there anything I need to do with DNS or the host file on my system? 

I don't currently have DNS setup but I am running the ldap-search on the system that I installed LDAP on.

---

### Post by fbonjour on 2009-11-18
This was answered several times:

[http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)
[http://ubuntuforums.org/showthread.php?p=8161118](http://ubuntuforums.org/showthread.php?p=8161118)
[http://ubuntuforums.org/showthread.php?p=8154148](http://ubuntuforums.org/showthread.php?p=8154148)

Somebody should fix the doc, though:

[https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)

---

### Post by bstear on 2009-11-18
Thank you. I did a search for LDAP on here but didn't really find anything. Guess I didn't use the right KEYWORDS when searching. 

I will look through these posts. That should help out alot.

All the how-to's make it seem very straight forward but as I see from the other posts it is anything but.

---

### Post by sameer9900 on 2009-11-19
Hi,

I was trying to install slapd and ldap-utils (as mentioned in the instruction) on ubuntu. But when I run this command: apt-get install slapd ldap-utils I get following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package slapd


Please note I was running the above command as root. If I run only apt-get install ldap-utils, I get following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ldap-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ldap-utils has no installation candidate


Can anyone help please

---

### Post by TotoTron on 2009-12-30
Sameer,

A new installation requires you to update the repository by running apt-get update before apt-get will work.

Cheers.

---

### Post by mech7 on 2010-03-17
Hmmm i try di recongifure and it still not ask for password.. only about purge database and then closes... Any other way to set this?

---

