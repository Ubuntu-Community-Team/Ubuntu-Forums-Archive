---
title: "64 bit updates for 32 bit install 12.04"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by drpaul on 2012-05-06
I have just done a 32 bit install of 12.04 keeping my old home partition.

Update Manager now wants to install Linux kernel image for version 3.2.0 on 64 bit x86 SMP.

Is this a screwup?

TIA

Paul

---

### Post by cepraksanta on 2012-05-07
Yeah, updated it... and it's nothing wrong. But i'm a little bit worried about it. Could anyone can give a bright explanation here...

---

### Post by cepraksanta on 2012-05-07
still confusing...

---

### Post by oldfred on 2012-05-08
Post this:

32 or 64 bit
```

uname -a

```
i386 or i686 = 32-bit
x86_64 = 64-bit

---

### Post by drpaul on 2012-05-09
32 bit install

uname -a
Linux paul-HP-Pavilion-dv6000-RG355UA-ABA 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

Paul

---

### Post by oldfred on 2012-05-09
Ok I am confused also.

Is there a line in  sources that has the wrong reference?

cat /etc/apt/sources.list

Post in code tags (# in edit panel).

---

### Post by drpaul on 2012-05-09
Here is my source.lst

```
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Pretty much standard 32 bit install.

Paul

---

### Post by Sef on 2012-05-09
> Update Manager now wants to install Linux kernel image for version 3.2.0 on 64 bit x86 SMP.


Could you take a pic of that message and post it.

---

### Post by drpaul on 2012-05-09
To busy to figure out screen capture. All you would see is the small window in Update Manager.

The Update Manager window has suggested updates for the kernel listed in the first post as well as the Generic kernel. Why would it try to install 2 kernels?

Paul

---

