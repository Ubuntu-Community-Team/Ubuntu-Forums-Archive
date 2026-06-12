---
title: "404  Not Found [IP: 91.189.91.14 80]"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by Krishna_Reddy_Seel on 2014-08-08
While updating my Ubuntu 13.04, throwing below error. Couldn't able to proceed.
```

  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
```

This is my first post in our forum, please help me.

---

### Post by claracc on 2014-08-08
Ubuntu 13.04 reached its end of life in January, the repositories are removed from the server, and for this reason update manager doesn't find the software packages.

I recommend you back up your /home files and install a supported release as 12.04 or 14.04.

---

### Post by varunendra on 2014-08-08
> **claracc said:**
> I recommend you back up your /home files and install a supported release as 12.04 or 14.04.

+1.

But if you can't upgrade right now, and need to install something on 13.04 (just running an update is meaningless for an EOL release), you can change your software sources to the "old-releases" repository. A single command to do that automatically -
```
sudo sed -i 's/archive.ubuntu/old-releases.ubuntu/' /etc/apt/sources.list
```
..followed by an update -
```
sudo apt-get update
```

---

### Post by Krishna_Reddy_Seel on 2014-08-08
I have replaced source.list with below text, resolved my issue.













# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise main
deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise main


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates main
deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates main


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
# deb-src [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

---

### Post by varunendra on 2014-08-08
Please mark the thread as [SOLVED] then.

And upgrading to 12.04.4 or 14.04.1 still makes a lot more sense than solving problems on an EOL version.

---

### Post by coffeecat on 2014-08-08
> **Krishna_Reddy_Seel said:**
> I have replaced source.list with below text, resolved my issue.

You edited a 13.04 sources.list and replaced all instances of raring with precise? I very much doubt that this will resolve your issue - it is more likely to introduce much bigger problems. Do not be surprised if you get irresolvable dependency issues.

If that was my system I would back up all personal data and make a fresh install of 14.04.

---

