---
title: "Lucid 10.04 will not update fully"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by krt on 2010-05-13
When I click on "update" after running a series of updates, I get an error message that says: > "Failed to fetch [http://archive.ubuntu.com/dists/lucid/main/binary-i386/](http://archive.ubuntu.com/dists/lucid/main/binary-i386/)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead."  Yet if I go the address in Firefox, one step at a time from [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and continue one step at a time, there is indeed a Packages.gz that I can download, so what is wrong?

I do not see that repository listed in sources.list or in the update manager.

Thank you,

krt

---

### Post by Dayofswords on 2010-05-13
have you tried a different server?

---

### Post by krt on 2010-05-13
Yes, I have tried 3 different servers and I have also tried updating in synaptic and I get the same error message . . . ?

Just tried looking for the "best server" for me, tried that, and it was much worse than the main server which has always worked well for me speed-wise and gave me the same error message.

Thank you,

krt

---

### Post by plucky on 2010-05-14
> **krt said:**
> Yes, I have tried 3 different servers and I have also tried updating in synaptic and I get the same error message . . . ?

Just tried looking for the "best server" for me, tried that, and it was much worse than the main server which has always worked well for me speed-wise and gave me the same error message.

Thank you,

krt

Post your sources.list from a terminal ```
cat /etc/apt/sources.list
``` also ```
ls -l /etc/apt/sources.list.d/
``` maybe something you have missed.

---

### Post by krt on 2010-05-14
Well when I looked at sources.list, I finally noticed that one of the addresses (which do not show too much resemblance to the URL failure notice) did not have the "ubuntu" in [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/) and I had already discovered that the only way I could get that link to work was to start with [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and the next thing that came up was not "dists" but a folder "ubuntu", so I tried adding that to the URL in Firefox and the link then worked.  So I edited sources.list to add the "ubuntu" to the address that for some reason did not have the "ubuntu" following the ubuntu.com part, and now it works; both in the update manager as well as in synaptic.  How this could have happened is beyond me, but it *seems* to be working now (fingers crossed).

Thank you,

krt

---

### Post by krt on 2010-05-14
> maybe something you have missed. 
Yes, I am worried about that.  If you (or anyone else) could look at my sources.list and see how it compares with yours, I would greatly appreciate it because previously I *think* it checked 62 files and now it only checks 58 when I run the update thing.

```
~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.ubuntu.com/ubuntu lucid main 

```

and ```
ls -l /etc/apt/sources.list.d
total 16
-rw-r--r-- 1 root root 269 2010-05-13 22:23 medibuntu.list
-rw-r--r-- 1 root root 269 2010-05-13 22:23 medibuntu.list.save
-rw-r--r-- 1 root root  89 2010-05-13 22:23 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root  89 2010-05-13 22:23 ubuntu-tweak-stable.list.save

```

If you, or anyone else that has installed this would post your sources.list, I could print them out and compare them since just looking at them on the screen is something of a pain :)

Thank you,

krt

---

### Post by plucky on 2010-05-15
Just tried your sources.list on my system,got an error about duplicate sources.
I commented out the last line of your sources.list as that is a duplicate of the first line for the main repository,it then ran cleanly.

Try that and see if that works.

Good Luck

---

### Post by krt on 2010-05-15
Yes, that got me back where I was before!

I never got any error message about duplicates; where did you get that? And I wonder why doing the update, including the kernel messed up my sources?  My only error was the one I got before I "fixed" the last link.

Thank you very much, plucky,

krt

---

### Post by jackdale on 2010-05-16
Similar problem here with the following errors:

```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It all works well if I have none of the Security or Recommended Updates checked as well as none of the "Other Software" repos checked.  Are some of the servers down?

Not working with Main Server, Australian Server and Best Server.

---

### Post by krt on 2010-05-18
Sorry, I did not look back here again after marking the thread "resolved".

I have run into odd problems like that, and I find if you use the "main server" you can generally get everything down with all the repos checked.

krt

---

### Post by jackdale on 2010-05-22
Found my problem:

  DansGuardian/Squid is stopping access to the repos.

Solution:
  Unknown

Workaround:
  Disable proxy for updates

This happened to me before when I installed DansGuardian/TinyProxy, which was resolved when re-installed through Ubuntu CE.  However, I installed squid instead when I upgraded to lucid, which worked well.  I'm not sure why it is suddenly not liking the repos, but at least it is a simple workaround (albeit not the most satisfactory).  I guess I must have accidentally changed the settings somewhere somehow... :confused:

---

