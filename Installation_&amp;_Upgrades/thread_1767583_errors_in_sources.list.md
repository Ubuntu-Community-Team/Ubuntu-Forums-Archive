---
title: "errors in sources.list"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by roshanbernard on 2011-05-25
hi, 

i was trying to install korena language pack.i was following this instructions from this link.

[http://ubuntuforums.org/showthread.php?t=30981](http://ubuntuforums.org/showthread.php?t=30981)

However, i deleted all the # from **sources.list(/etc/apt)-gedit**

Now when i wanna update my system in terminal i get this error message

[HTML]rosh@roshan:~$ sudo apt-get update
E: Type 'See' is not known on line 4 in source list /etc/apt/sources.list
E: The list of sources could not be read.[/HTML]

and i am not able to open synaptic manager...

can anyone copy paste their source.list and give me...( i hope that works)..

since i was new bee in linux..i messed up..

---

### Post by matt_symes on 2011-05-25
Hi

Copy and paste your existing /etc/apt/sources.list file here (between code tags) and we will help you fix that one. That way there will be no version issues.

Kind regards

---

### Post by roshanbernard on 2011-05-26
hi the gedit list shows the following info

[HTML]deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties

See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
newer versions of the distribution.
deb http://mirror.de.leaseweb.net/ubuntu/ natty main restricted
deb-src http://mirror.de.leaseweb.net/ubuntu/ natty restricted main multiverse universe #Added by software-properties

Major bug fix updates produced after the final release of the
distribution.
deb http://mirror.de.leaseweb.net/ubuntu/ natty-updates main restricted
deb-src http://mirror.de.leaseweb.net/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
team. Also, please note that software in universe WILL NOT receive any
review or updates from the Ubuntu security team.
deb http://mirror.de.leaseweb.net/ubuntu/ natty universe
deb http://mirror.de.leaseweb.net/ubuntu/ natty-updates universe

N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
team, and may not be under a free licence. Please satisfy yourself as to 
your rights to use the software. Also, please note that software in 
multiverse WILL NOT receive any review or updates from the Ubuntu
security team.
deb http://mirror.de.leaseweb.net/ubuntu/ natty multiverse
deb http://mirror.de.leaseweb.net/ubuntu/ natty-updates multiverse

Uncomment the following two lines to add software from the 'backports'
repository.
N.B. software from this repository may not have been tested as
extensively as that contained in the main release, although it includes
newer versions of some applications which may provide useful features.
Also, please note that software in backports WILL NOT receive any review
or updates from the Ubuntu security team.
deb http://kr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://kr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://mirror.de.leaseweb.net/ubuntu/ natty-security main restricted
deb-src http://mirror.de.leaseweb.net/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
deb http://mirror.de.leaseweb.net/ubuntu/ natty-security universe
deb http://mirror.de.leaseweb.net/ubuntu/ natty-security multiverse

Uncomment the following two lines to add software from Canonical's
'partner' repository.
This software is not part of Ubuntu, but is offered by Canonical and the
respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

This software is not part of Ubuntu, but is offered by third-party
developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main[/HTML]


i deleted all the #..i was really dumb...:-(

---

### Post by matt_symes on 2011-05-26
Hi

You have removed all the # signs from infront of the comments as well as the repositories.

To fix the file open it with root privileges

```
gksudo gedit /etc/apt/sources.list
```Put a # in front of every line that DOES NOT START with the word deb or deb-src.

Then save the file.

Kind regards

---

### Post by roshanbernard on 2011-05-26
thanks a lot for ur help.It solved it....:-)

---

