---
title: "Problem loading and getting new updates."
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by bobalooba on 2012-08-08
I want to upgrade to 12.04 but everytime I check for new updates this message shows up. "W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead." 

It tells me to check my internet connection when I am connected just fine. I want to get this problem fixed before I upgrade so that everthing runs smoothly. What do I do to fix this?

---

### Post by Old_Grey_Wolf on 2012-08-08
What version of Ubuntu are you using? Those repositories listed in the error messages are for Edgy Elf, 6.10. Edgy Elf, 6.10, has not been supported since April 2008.

Enter this command in a terminal and post the output so we can see the version of Ubuntu you are using. ```
cat /etc/lsb-release
```

Enter this command in a terminal and post the output so we can see the repositories you are using. ```
cat /etc/apt/sources.list
```

---

### Post by bobalooba on 2012-08-08
john@john-T6211:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
john@john-T6211:~$ 




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
john@john-T6211:~$

---

### Post by Old_Grey_Wolf on 2012-08-08
Comment out the last 2 lines in the sources.list file. Comment out these lines. ```
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
```

Then update and upgrade again.

Edit: I am going to sleep now; however, someone should be able to help you from here if this doesn't work.

---

### Post by bobalooba on 2012-08-08
What do you mean comment out?

---

### Post by Old_Grey_Wolf on 2012-08-08
> **bobalooba said:**
> What do you mean comment out?

In a terminal, enter ```
gksudo gedit /etc/apt/sources.list
```

Then put a # at the beginning of those 2 lines at the bottom. Then save the file.

---

### Post by bobalooba on 2012-08-08
It Worked! Thank you for everything.

---

### Post by eoswins on 2013-01-26
Having the same issue; if someone could help.

Errors:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.7.102-0ubuntu3.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.7.102-0ubuntu3.5_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.7.102-0ubuntu3.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.7.102-0ubuntu3.5_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.7.102-0ubuntu3.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.7.102-0ubuntu3.5_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.7.102-0ubuntu3.5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.7.102-0ubuntu3.5_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq-dev_9.1.6-0ubuntu12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq-dev_9.1.6-0ubuntu12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.6-0ubuntu12.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.6-0ubuntu12.04.1_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/dh-apparmor_2.7.102-0ubuntu3.5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/dh-apparmor_2.7.102-0ubuntu3.5_all.deb) 404  Not Found [IP: 91.189.91.15 80]


cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
e0s@EternalSilence:~$ 



 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) natty main # disabled on upgrade to natty
# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) natty main # disabled on upgrade to natty


#manually added below:
# deb [http://archive.scrapy.org/ubuntu](http://archive.scrapy.org/ubuntu) natty main # disabled on upgrade to natty

---

### Post by Old_Grey_Wolf on 2013-01-26
Try updating the package list with ```
sudo apt-get update
```Then upgrade the packages with ```
sudo apt-get upgrade
```

---

### Post by eoswins on 2013-01-26
That worked, thanks.

---

### Post by yragnos on 2013-03-03
Make sure you run 

"sudo apt-get update"
 

to update PPA information. It looks like that PPA changed. I had the same issue, ran sudo apt-get update and then reran this and it worked.

---

### Post by theAvengers on 2013-05-09
I am facing the same issue. It would be great if someone can help.


Errors:

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources
  Connection failed [IP: 91.189.92.176 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe amd64 Packages
  Connection failed [IP: 91.189.92.201 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages
  Connection failed [IP: 91.189.91.13 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages
  Connection failed [IP: 91.189.91.15 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en
  Connection failed [IP: 91.189.91.13 80]
Fetched 198 B in 31s (6 B/s)                             
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  Connection failed [IP: 91.189.92.176 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages)  Connection failed [IP: 91.189.92.201 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Connection failed [IP: 91.189.91.13 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Connection failed [IP: 91.189.91.15 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Connection failed [IP: 91.189.91.13 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.



cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner

---

### Post by Old_Grey_Wolf on 2013-05-09
> **theAvengers said:**
> 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"



11.10 went end of life today. It is no longer supported.

---

### Post by jrkrideau on 2013-05-09
seem to be having a similar problem to the ones described here. I am a relatively new Ubuntu user and just don't know what repositories change or add.  Any suggestions gratefully recieved.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

**Error returned from software manager**

Failed to download repository information
check your internet connection
**DETAILS**
W:Failed to fetch [http://ppa.launchpad.net/lyx-outline-devel/lyx-stable/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/lyx-outline-devel/lyx-stable/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/lyx-outline-devel/lyx-stable/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/lyx-outline-devel/lyx-stable/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gottcode/gcppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/gottcode/gcppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gottcode/gcppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/gottcode/gcppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

**sudo apt-get update**
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages  404  Not Found

**cat /etc/apt/sources.list**

john@john-K53U:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
# deb [http://cran.skazkaforyou.com/bin/linux/ubuntu](http://cran.skazkaforyou.com/bin/linux/ubuntu) quantal/ # disabled on upgrade to quantal
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) quantal main # disabled on upgrade to quantal
# deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) quantal main # disabled on upgrade to quantal
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by cookf on 2013-06-01
I'm not sure if this is closed thread, but I have the same problem and I don't know the relevance of the library not found. Running sudo apt-get update provides a long list of which I have copied the last few lines in the quote below. It appears to me a single library can't be found. Can it be commented out? Any help is much appreciated. 

> Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en_GB
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en
Fetched 968 kB in 34s (28.4 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

