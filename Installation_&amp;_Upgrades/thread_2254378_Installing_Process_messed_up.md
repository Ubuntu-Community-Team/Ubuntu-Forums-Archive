---
title: "Installing Process messed up"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by maxyman3400 on 2014-11-26
Around 3-4 days ago I posted about having help install 14.04. It worked  and it was working but I had a power surge and a computer crash mid  install. Now when ever I try to open update manager this happens
[http://imgur.com/GCz3FQu](http://imgur.com/GCz3FQu)
It freezes and it just will never load. I can not reinstall becuase the  disk version refuses to work and when I try to update in terminal it  gives me this error message
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

After around a week of no responce im reposting this. Again please help

---

### Post by ibjsb4 on 2014-11-26
Boot the live DVD and open 'gparted'.  Use this to remove the ubuntu partition on the hard drive (leave it as free space).  Then start the ubuntu installer.  You will be given the option to install ubuntu to the free space.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

---

### Post by grahammechanical on 2014-11-26
The command do-release-upgrade will upgrade 14.04 to 14.10 and I do not think that is your intention. Upgrading even to 14.04.1 from a Ubuntu that is broken will result in a failed upgrade.

The problem with Update Manager is this

> [COLOR=#000000]Unable to get exclusive lock [/COLOR]

[COLOR=#000000]This usually means that another package management application (like [/COLOR][COLOR=#000000]apt-get or aptitude) already running. Please close that application [/COLOR][COLOR=#000000]first. [/COLOR]

You can try this

At the Grub boot menu select Advanced Options for Ubuntu and then select Recovery mode.

At the Recovery menu select Network. That will get an Internet connection and put the file system in read/write mode both of which are necessary for updating.

When back at the recovery menu select Root. You will now be at a Linux command Line where you can run commands like

```
apt-get -f install
dpkg --configure -a
apt-get update
apt-get upgrade

```

when finished, to get back to the recovery menu type exit. And then at the recovery menu select Resume. That will load to a desktop using llvmpipe as a fall back video driver. It will seem a little slow to what you are used to. A restart will load the usual video driver.

Doing this avoids the problem caused Update Manager not closing correctly due the mains power surge for by using recovery mode we are accessing Linux before Ubuntu and its desktop environment has even loaded.

Your thread title is causing us to think that the problem is with installing Ubuntu and not an incomplete install of an application due to a power surge.

Oh, I nearly forgot to mention. Recovery mode has an option called dpkg. It repairs broken packages.

Regards

---

### Post by maxyman3400 on 2014-11-30
> **grahammechanical said:**
> The command do-release-upgrade will upgrade 14.04 to 14.10 and I do not think that is your intention. Upgrading even to 14.04.1 from a Ubuntu that is broken will result in a failed upgrade.

The problem with Update Manager is this



You can try this

At the Grub boot menu select Advanced Options for Ubuntu and then select Recovery mode.

At the Recovery menu select Network. That will get an Internet connection and put the file system in read/write mode both of which are necessary for updating.

When back at the recovery menu select Root. You will now be at a Linux command Line where you can run commands like

```
apt-get -f install
dpkg --configure -a
apt-get update
apt-get upgrade

```

when finished, to get back to the recovery menu type exit. And then at the recovery menu select Resume. That will load to a desktop using llvmpipe as a fall back video driver. It will seem a little slow to what you are used to. A restart will load the usual video driver.

Doing this avoids the problem caused Update Manager not closing correctly due the mains power surge for by using recovery mode we are accessing Linux before Ubuntu and its desktop environment has even loaded.

Your thread title is causing us to think that the problem is with installing Ubuntu and not an incomplete install of an application due to a power surge.

Oh, I nearly forgot to mention. Recovery mode has an option called dpkg. It repairs broken packages.

Regards
Thank you so much!. This has helped me so much! Thanks

---

