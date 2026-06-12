---
title: "error messages within installation"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by meanymoo on 2011-05-31
i'm new with [SIZE=2][COLOR=#000000][FONT=Ubuntu][COLOR=#6C6C6C]**Ubuntu 11.04**

[/COLOR][/FONT][/COLOR][/SIZE]
as im new with linux and ubuntu
i had this problem after installation of certain programs
after i install programs with a sudo apt-get install comand
i get this error messages
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does that mean?
is it okay?
or it disturb my installations?
and how do i deal with it
thanks b4 and i really appreciate your help please ;)

---

### Post by ivanovnegro on 2011-05-31
What program did you install.
Seems something happened in your sources list or something similar.
Could you post eventually back with this command to see it there is something wrong:

```
sudo cat /etc/apt/sources.list

```

---

### Post by meanymoo on 2011-05-31
i want to connect windows mobile 5 to ubuntu
this is the result with sudo cat /etc/apt/sources.list

[sudo] password for meanymoo: 
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ natty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty universe
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb [http://winff.org/ubuntu](http://winff.org/ubuntu) lucid universe
# deb-src [http://winff.org/ubuntu](http://winff.org/ubuntu) lucid universe
# deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) lucid main
# deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) lucid main

is it wrong in something?
thanks

---

### Post by meanymoo on 2011-05-31
any close way is this forum 
[http://stream-recorder.com/forum/showthread.php?t=5373](http://stream-recorder.com/forum/showthread.php?t=5373)
and i got that error messages after i tried to install that

can somebody help me please
thanks before

---

### Post by ivanovnegro on 2011-05-31
It seems ok to me.
Windows Mobile, not sure about it, if that really can coexist with Ubuntu.
Do you have  by any chance the two package managers open at the same time, like Synaptic and the Software Center, close one of them and try it again.

---

### Post by ivanovnegro on 2011-05-31
> **meanymoo said:**
> any close way is this forum 
[http://stream-recorder.com/forum/showthread.php?t=5373](http://stream-recorder.com/forum/showthread.php?t=5373)
and i got that error messages after i tried to install that

can somebody help me please
thanks before

Im not sure if Stream Recorder still exists, I dont use it, but on the forum it seems outdated because the instruction is for Karmic, Ubuntu 9.10. and you are on 11.04.

---

### Post by meanymoo on 2011-05-31
okay, yup i guess both open
thanks for that

---

### Post by meanymoo on 2011-05-31
> **ivanovnegro said:**
> Im not sure if Stream Recorder still exists, I dont use it, but on the forum it seems outdated because the instruction is for Karmic, Ubuntu 9.10. and you are on 11.04.

that's the only tutorial close to what i need right now probably
can i used that installation tutorial and changed one or two to be able to install it with 11.04
the only step i change is to change the command line Karmic with Lucid

---

### Post by ivanovnegro on 2011-05-31
I normally dont do it this way, it could work or not.
The question is why it does not exist a recent how to? Maybe its deprecated and you have to search for an alternative to this program.

---

### Post by meanymoo on 2011-05-31
ok thanks ivanov
i'll look and keep looking

---

### Post by meanymoo on 2011-05-31
solved
[https://help.ubuntu.com/community/PortableDevices/WindowsMobile](https://help.ubuntu.com/community/PortableDevices/WindowsMobile)
but still have this messages
Could not display "synce://handheld/"
Nautilus cannot handle "synce" locations.
do you know what's wrong?
do i have to look for program beside nautilus?

---

### Post by ivanovnegro on 2011-05-31
I think I have to pass now on this as I never synced phones to my computer. :)

---

