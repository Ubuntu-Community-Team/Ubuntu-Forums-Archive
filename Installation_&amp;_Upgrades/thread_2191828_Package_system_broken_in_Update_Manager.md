---
title: "Package system broken in Update Manager"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by 13eriksson on 2013-12-04
I have a bunch of updates I'm trying to make in Update Manager, but I can't because the package system is broken. I already disabled my third party repositories, and that didn't change anything. I'm running 12.04. These are the details:
The following packages have unmet dependencies:

python2.7: Depends: python2.7-minimal (= 2.7.3-0ubuntu3.2) but 2.7.3-0ubuntu3.4 is installed
           Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.4 is installed
           Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
           Depends: libncursesw5 (>= 5.6+20070908) but 5.9-4 is installed
           Depends: libreadline6 (>= 6.0) but 6.2-8 is installed
           Depends: libsqlite3-0 (>= 3.5.9) but 3.7.9-2ubuntu1.1 is installed


Any help is appreciated!

---

### Post by Frogs Hair on 2013-12-04
Hello and Welcome  

Run the following command and look for further command suggestions in the output .  ```
sudo apt-get update
``` The output may suggest one of the following.```
 sudo apt-get -f install
``````
sudo dpkg --configure -a
```

---

### Post by 13eriksson on 2013-12-05
I tried sudo apt-get update, which seemed to do a lot of things, and as far as I could tell it didn't produce any error messages. But Update Manager was still full of updates and gave me the same error. I tried the other two suggestions and I got the following:

> apt-get install -f
balder@balder-Aspire-3000:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
balder@balder-Aspire-3000:~$

> balder@balder-Aspire-3000:~$ sudo dpkg --configure -a
[sudo] password for balder: 
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.3-0ubuntu3.2); however:
  Version of python2.7-minimal on system is 2.7.3-0ubuntu3.4.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.3-0ubuntu3.2); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.7
 libpython2.7



---

### Post by Frogs Hair on 2013-12-05
Permission was denied on the the first command because sudo wasn't used . Try the following and report back.  ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 13eriksson on 2013-12-05
Here's what I got:

> Fetched 2,227 kB in 5s (386 kB/s)                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python2.7 : Depends: python2.7-minimal (= 2.7.3-0ubuntu3.2) but 2.7.3-0ubuntu3.4 is installed
E: Unmet dependencies. Try using -f.
 

So I ran sudo apt-get -f install, and I got this:
 > 
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.3-0ubuntu3.2); however:
  Version of python2.7-minimal on system is 2.7.3-0ubuntu3.4.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.3-0ubuntu3.2); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python2.7
 libpython2.7
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by fantab on 2013-12-06
Try:
```
 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get dist-upgrade

```

Report back with errors, if any.

---

### Post by 13eriksson on 2013-12-06
I still get the same error

---

