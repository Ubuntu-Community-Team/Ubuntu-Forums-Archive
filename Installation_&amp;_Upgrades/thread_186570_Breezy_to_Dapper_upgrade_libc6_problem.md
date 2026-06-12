---
title: "Breezy to Dapper upgrade: libc6 problem"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by emreakbas on 2006-06-02
Hi all, 
   I tried to upgrade my breezy to dapper but encountered some problems.  
   I first, changed all the "breezy"s to "dapper"s  in the distribution column of /etc/apt/sources.list   and then apt-get update   & apt-get upgrade.  
   Some packages were removed and some were installed succesfully  until I got the error message:

[FONT="Courier New"]The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6-0ubuntu20 is installed
  ubuntu-minimal: Depends: pcmciautils but it is not installed
                  Depends: wpasupplicant but it is not installed
[/FONT]

What can I do to solve the problem?

---

### Post by pedstunite on 2006-06-03
I'm trying to install the libc6.dev, and have encountered a similar problem...

pedro@CPE0015f291de83-CM001404927a76:~$ sudo apt-get install build-essential gcc gcc-3.4
Password:
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages
pedro@CPE0015f291de83-CM001404927a76:~$ apt-get install libc6
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
pedro@CPE0015f291de83-CM001404927a76:~$ su
Password:
root@CPE0015f291de83-CM001404927a76:/home/pedro# apt-get install libc6 Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@CPE0015f291de83-CM001404927a76:/home/pedro# apt-get install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is to be installed
E: Broken packages
root@CPE0015f291de83-CM001404927a76:/home/pedro#
root@CPE0015f291de83-CM001404927a76:/home/pedro#

---

### Post by ubuntu_demon on 2006-06-04
Both of you should fully read and understand my guide here :
HOWTO fix problems regarding broken dependencies
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

emreakbas one of the things to try is :
$sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

pedstunite try something like :
$sudo apt-get remove -f libc-dev --purge
$sudo apt-get -f install libc6-dev=2.3.6-0ubuntu20

pedstunite please start your own thread if this doesn't solve it.

---

### Post by ubuntu_demon on 2006-06-05
solved ?

---

### Post by emreakbas on 2006-06-05
Yes, solved. As far as I understood the problems was locale related. I am using the Turkish locale which is tr_TR.UTF8. 

When I tried to force-install libc6, ubuntu complained about the newly upgraded locales were not configured properly. So, I tried to configure locales with "dpkg --configure" but I only succeeded when I set my locale to "en_US", it didn't configure the locales when I am in tr_TR.UTF8. 

After configuring and force-installing libc6, the upgrade to Dapper has been done successfully. 

Thanks.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=emreakbas]Yes, solved. As far as I understood the problems was locale related. I am using the Turkish locale which is tr_TR.UTF8. 

When I tried to force-install libc6, ubuntu complained about the newly upgraded locales were not configured properly. So, I tried to configure locales with "dpkg --configure" but I only succeeded when I set my locale to "en_US", it didn't configure the locales when I am in tr_TR.UTF8. 

After configuring and force-installing libc6, the upgrade to Dapper has been done successfully. 

Thanks.[/QUOTE]
So now you are using en_US instead of  tr_TR.UTF8 ?

Here's a solution to problems with locales did you try that :
[http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8)

---

### Post by emreakbas on 2006-06-05
No. I'm using tr_TR.UTF8 now, there is no problem.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=emreakbas]No. I'm using tr_TR.UTF8 now, there is no problem.[/QUOTE]
Could you please elaborate on your solution ? Because it might help others.

thnx!

---

### Post by emreakbas on 2006-06-05
Ok, here is what I did/encountered step-by-step: 
[LIST]
[*]While upgrading from breezy to dapper, the upgrade process stopped because libc6 could not be installed. 
[*]I tried to install libc6  with "apt-get install -f" but it didn't succeed. 
[*]I investigated for a possible reason and found (in the log window of adept) that the "locales" package were not configured properly.  My original locale was "tr_TR.UTF8". 
[*]I tried to configure "locales" by "dpkg --configure -a" but it didn't work. 
[*]Only for the purpose of configuring "locales" I changed the locale of my terminal to "en_US" temporarily (by [FONT="Courier New"]export LC_ALL=en_US; export LANG=en_US[/FONT])
[*]Then, "locales" package was configured successfully by "dpkg --configure -a"
[*]I continued the upgrade process by issuing "apt-get install -f libc6" and then "apt-get update"  in a new terminal of which locale is "tr_TR.UTF8"
[*]After the upgrade finished, the system has been working flawlessly. I am using the locale "tr_TR.UTF8" 

[/LIST]

---

### Post by ubuntu_demon on 2006-06-05
> **emreakbas]Ok, here is what I did/encountered step-by-step: 
[LIST]
[*]While upgrading from breezy to dapper, the upgrade process stopped because libc6 could not be installed. 
[*]I tried to install libc6  with "apt-get install -f" but it didn't succeed. 
[*]I investigated for a possible reason and found (in the log window of adept) that the "locales" package were not configured properly.  My original locale was "tr_TR.UTF8". 
[*]I tried to configure "locales" by "dpkg --configure -a" but it didn't work. 
[*]Only for the purpose of configuring "locales" I changed the locale of my terminal to "en_US" temporarily (by [FONT="Courier New"]export LC_ALL=en_US said:**
> )
[*]Then, "locales" package was configured successfully by "dpkg --configure -a"
[*]I continued the upgrade process by issuing "apt-get install -f libc6" and then "apt-get update"  in a new terminal of which locale is "tr_TR.UTF8"
[*]After the upgrade finished, the system has been working flawlessly. I am using the locale "tr_TR.UTF8" 

[/LIST]
thnx!

---

### Post by Cafulcura on 2006-07-17
> $sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

I've got a same problem for a days...I've read and I've try a lot...
So... only this command resolve the problem!!!

Could you create a How To lib6 problem ? for another users...

Thank you so much!

---

