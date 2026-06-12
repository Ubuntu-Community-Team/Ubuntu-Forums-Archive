---
title: "Installing Applications"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by novavon on 2007-03-10
I rebooted the computer two times and restarted xserver few times,
but this application updater keeps on crashing every time it checks for available applications.
I took a screen shot right before it crashed and exited.
I would appreciate any comment regarding this issues, thanks.

Questions:
What could be the problem?
In what circumstances could cause such a problem?
Why would even crash without warning?

---

### Post by joselin on 2007-03-10
Do the following:
```
sudo apt-get update
```Then:
```
sudo apt-get upgrade
```

With those command you upgrade all your system packages.

And then, try to launch it again.

---

### Post by novavon on 2007-03-10
It didn't work...
I don't understand why.
These are the outputs from the console after the commands, "apt-get update" and "apt-get upgrade".

Is there an alternative to upgrade all of the system packages?

```

sudo apt-get update
Password:
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA
Get:2 http://ca.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_CA
Get:3 http://ca.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-updates/restricted Translation-en_CA
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-updates/multiverse Translation-en_CA
Get:4 http://ca.archive.ubuntu.com edgy-backports Release.gpg [191B]
Hit http://security.ubuntu.com edgy-security Release  
Ign http://ca.archive.ubuntu.com edgy-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com edgy-backports/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com edgy Release 
Hit http://ca.archive.ubuntu.com edgy-updates Release
Hit http://ca.archive.ubuntu.com edgy-backports Release             
Hit http://security.ubuntu.com edgy-security/main Packages          
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://ca.archive.ubuntu.com edgy/main Packages
Hit http://ca.archive.ubuntu.com edgy/restricted Packages
Hit http://ca.archive.ubuntu.com edgy/multiverse Packages
Hit http://ca.archive.ubuntu.com edgy/restricted Sources
Hit http://ca.archive.ubuntu.com edgy/main Sources
Hit http://ca.archive.ubuntu.com edgy/multiverse Sources
Hit http://ca.archive.ubuntu.com edgy/universe Sources
Hit http://ca.archive.ubuntu.com edgy/universe Packages
Hit http://ca.archive.ubuntu.com edgy-updates/main Packages
Hit http://ca.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com edgy-updates/main Sources
Hit http://ca.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com edgy-backports/main Packages
Hit http://ca.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://ca.archive.ubuntu.com edgy-backports/universe Packages
Hit http://ca.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com edgy-backports/main Sources
Hit http://ca.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://ca.archive.ubuntu.com edgy-backports/universe Sources
Hit http://ca.archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done

```

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by joselin on 2007-03-11
With apt-get update you receive the lists of packages from the different repositories. With apt-get upgrade, you upgrade all the system packages and you ensure that you have the latest version of all you have installed.
With those commands you did the same as with the update manager but on the command line. I said you to do it, because i thought that there were a new version of update manager available. But seems that i'm wrong.

---

### Post by zvacet on 2007-03-11
Do you have all repositories open?Did you install language support?Maybe I´m wrong but I think that is what give you trouble.

---

