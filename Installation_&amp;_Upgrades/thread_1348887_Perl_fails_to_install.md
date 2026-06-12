---
title: "Perl fails to install"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by klaus0009 on 2009-12-07
Hello,
 
I was trying to get a Perl app to run on one of my servers. It wouldn't run properly. The developer suggested I uninstall perl then re install it. I felt unsure about doing this, but for some reason went against my gut feeling.
 
apt-get purge perl
 
I cannot get perl to install now.
 
```
root@swahili:/home/droid# apt-get install perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  perl: Depends: perl-base (= 5.8.8-12ubuntu0.4) but 5.10.0-11.1ubuntu2 is to be installed
E: Broken packages
root@swahili:/home/droid#

```
 
I've updated and tried to apt-get -f install. No dice. 
 
My system configuration is as shown below
 
Linux ---- 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux
Ubuntu 8.10 \n \l
 
Please help! :confused:
 
Thanks

---

