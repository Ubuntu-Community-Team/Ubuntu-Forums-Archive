---
title: "Installing Process messed up"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by maxyman3400 on 2014-11-20
Around 3-4 days ago I posted about having help install 14.04. It worked and it was working but I had a power surge and a computer crash mid install. Now when ever I try to open update manager this happens
[http://imgur.com/GCz3FQu](http://imgur.com/GCz3FQu)
It freezes and it just will never load. I can not reinstall becuase the disk version refuses to work and when I try to update in terminal it gives me this error message
max@max-Alienware-X51-R2:~$ do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,146 kB]                                                  
Fetched 1,146 kB in 0s (0 B/s)                                                 
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'
[sudo] password for max: 

Reading cache

Checking package manager

Unable to get exclusive lock 

This usually means that another package management application (like 
apt-get or aptitude) already running. Please close that application 
first. 

And then when I run this command
max@max-Alienware-X51-R2:~$ ^C
max@max-Alienware-X51-R2:~$  sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
max@max-Alienware-X51-R2:~$ 

Please help because I can't reinstall to try to fix what that surge did. PLEASE HELP!


[COLOR=#333333][FONT=Ubuntu][FONT=monospace][/FONT][/FONT][/COLOR]

---

### Post by yancek on 2014-11-20
The messages you posted indicate that you have multiple instances open for upgrading, using apt-get from a terminal and not stopping and then trying the Software Center or vice versa or just multiple apt-get instances.  Have you tried logging out and rebooting?  If you've done that already then it's another problem but there may be some way to force the upgrade to continue.

---

### Post by maxyman3400 on 2014-11-21
Yes that was the first thing I tried. Also it seems anything with updating software does not work.

---

### Post by maxyman3400 on 2014-11-21
Ok so steam just deleted all local files and things are starting to randomly pop up? Any help?

---

