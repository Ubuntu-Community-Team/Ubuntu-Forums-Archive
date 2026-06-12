---
title: "7 packages to upgrade that won't upgrade"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-05
when i login, i get this output:

```
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-98-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

7 packages can be updated.
3 updates are security updates.
```

however when i do this script named "upgrade":

```
#!/bin/bash
apt-get update
apt-get -y upgrade
apt -y autoremove
```

nothing gets upgraded:

```
Script started on Sat May  5 08:00:40 2018
08:00:40 [3097] EXECUTING: 'upgrade'
Hit:1 http://nl.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://nl.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]                                              
Get:3 http://nl.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]                                            
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                                                               
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]                                               
Get:6 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [767 kB]   
Get:7 http://nl.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [708 kB]                           
Get:8 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [624 kB]                      
Get:9 http://nl.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [575 kB]                       
Fetched 2997 kB in 2s (1317 kB/s)                                                  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
[[ 0m25s real 25.026 - user 3.608 - sys 0.584 - 16.75% ]]
08:01:05 [3097] FINISHED - status = 0

Script done on Sat May  5 08:01:06 2018
```

anyone have an idea what i need to do?

---

### Post by mörgæs on 2018-05-05
sudo apt dist-upgrade

---

### Post by deadflowr on 2018-05-05
apt-get upgrade will never install any new packages or dependencies. It only updates packages already installed.
as well as posted above you can run
```
sudo apt-get dist-upgrade
sudo apt upgrade
sudo apt full-upgrade
```
notice that apt upgrade and apt-get upgrade are two different commands and do not run the same as the other.

Case in point here is the linux-generic (and subsequent linux-image-generic and linux-headers-generic packages) require new dependencies be installed.
Those dependencies being the new kernel version, which should be version 4.4.0-122.

---

### Post by Skaperen on 2018-05-05
i don't want the upgrade to go past 16.04.X LTS.  i just want to have the very latest of 16.04 LTS, especially security upgrades.

---

### Post by Bashing-om on 2018-05-05
Skaperen; Hello -
> 
<ubottu> A dist-upgrade will install new dependencies for packages already installed and may remove 
               packages if they are no longer needed. This will not bring you to a new release of Ubuntu,


deadflowr will not steer you wrong :)

[INDENT]just my 2 cents
[/INDENT]

---

### Post by deadflowr on 2018-05-05
> **Skaperen said:**
> i don't want the upgrade to go past 16.04.X LTS.  i just want to have the very latest of 16.04 LTS, especially security upgrades.

I would have been kind enough to tell you if any commands I posted would have upgraded the release to a new version of Ubuntu.
It would be mean not to.

As it is the 3 commands I posted do this per their man pages
apt-get dist-upgrade:
 > dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.

apt upgrade:
> upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           statisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the remove of an installed
           package the upgrade for this package isn't performed.

and apt full-upgrade:
> full-upgrade performs the function of upgrade but may also remove
           installed packages if that is required in order to resolve a
           package conflict.


and what the command apt-get upgrade does:
> upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

These are readily available to you in the man pages on your system
along with all the other known uses:
```
[man apt ]("http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html")
[man apt-get]("http://manpages.ubuntu.com/manpages/xenial/man8/apt-get.8.html")
```


To have actually upgrade releases you would either need to run Ubuntu's upgrader command
```
do-release-upgrade
```
^^^^This would upgrade versions of Ubuntu^^^^

or you would need to manually edit the repository codename in your sources.list file(s) and then
any of those apt commands would have begun the process of upgrading the release.


Hope this clears things up a little.

---

### Post by Skaperen on 2018-05-06
i did sudo apt-get dist-upgrade and it upgraded everything.  so i recoded my script to do that.  i run it about once a week and reboot (to be on the new stuff that evening) when i boot up for the evening (on my laptop).  i do it on my server if it runs OK on my laptop.

so, what are the fundamental differences among these?

```
sudo apt-get dist-upgrade
sudo apt-get upgrade
sudo apt upgrade
sudo apt full-upgrade
```

and should i do anything different in my regular updating/upgrading?

what command would do the incremental upgrade to the latest version (18.04)?  and can the version number be chosen (what if i want to upgrade to 17.04)?

---

