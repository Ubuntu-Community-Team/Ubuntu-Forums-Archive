---
title: "Problems when checking for updates"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by sarina on 2012-02-29
Hi Friends,

I made some mistake when downloading and installing dansguardian, tinyproxy and firehol.  After setting up the firewalls now I get error messages when getting updates. I tried researching the forum regarding this error and tried some things but nothing worked. Any help will be greatly appreciated. :) (Working on Ubuntu 11.10)

Thanks!,
Sarina


*******
Error message from Update Manager:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2012-02-26' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntuce.list'

*******

Error message from Synaptic:

E: Type '--2012-02-26' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntuce.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


*******

Ubuntuce.list file:

--2012-02-26 14:39:49--  [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list)
Resolving ubuntuce.com... 199.187.126.218
Connecting to ubuntuce.com|199.187.126.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54 [text/plain]
Saving to: `lucid_i386.list'

     0K                                                       100% 2.36M=0s

2012-02-26 14:39:55 (2.36 MB/s) - `lucid_i386.list' saved [54/54]


*******

sources.list file

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110426)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security universe main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe main

---

### Post by sarina on 2012-02-29
Forgot to add the lucid_i386 file created in my /home/sarina directory. 

#deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) lucid_i386/


Thanks for your assistance!

Sarina

---

### Post by plucky on 2012-02-29
Post output from a terminal for ```
cat /etc/apt/sources.list.d/ubuntuce.list
```

Your sources.list file is mixing Natty and Oneiric Repositories which is not a good idea.

Go [Here](http://repogen.simplylinux.ch/) and generate a sources.list for your oneiric install.

> Forgot to add the lucid_i386 file created in my /home/sarina directory.

#deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) lucid_i386/


What does that mean?

Is it supposed to be a repository?

What is it supposed to do?

> E: Type '--2012-02-26' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntuce.list


The **Ubuntuce.list** is incorrect.

---

### Post by sarina on 2012-02-29
I included the ubuntuce.list data in my original post: 

--2012-02-26 14:39:49--  [http://ubuntuce.com/repos/Ubuntu_CE/lucid_i386/]("http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list")
Resolving ubuntuce.com... 199.187.126.218
Connecting to ubuntuce.com|199.187.126.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54 [text/plain]
Saving to: `lucid_i386.list'

     0K                                                       100% 2.36M=0s

2012-02-26 14:39:55 (2.36 MB/s) - `lucid_i386.list' saved [54/54]


Ubuntu CE is a Christian Edition of Ubuntu. I do not care for that distro. I just wanted to get a gui for dansguardian and it messed up my sources.list.  I don't know why it created the lucid_i386.list in my home directory. 

I did what you suggested and generated a source.list for my current Ubuntu version (11.10). Replaced it but keep getting the same error message stated above. It seems that the app (update manager/synaptic) is trying to get the sources from the Ubuntu CE repository, bypassing the sources.list. I'm not sure what's going on. I'm still researching. 

Thanks.

---

### Post by sarina on 2012-02-29
:D

Thanks for your assistance. I replaced the sources.list file with the one  generated by [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/), deleted ubuntuce.list and backup  from sources.list.d directory and added the gpg keys. Now updates and installations are working  fine.

Your assistance was invaluable. Thanks a lot!!

Regards, 
Sarina

---

