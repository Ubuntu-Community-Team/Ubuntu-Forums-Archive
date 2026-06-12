---
title: "Recently Upgraded To Na:tty - PPA Issues..."
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by ZachGretzinger on 2011-04-27
First off - I apologize if this has been asked 42,000 times before...

Anyway - my question:

I recently upgraded from Maverick to Natty... During the upgrade I was notified that Natty was going to disable my 3rd party PPA's for the upgrade. I clicked "ok", not realizing that I have no freaking clue as to how to re-enable them... 

I went to the Software Sources thingy and re-checked all of the unchecked repositories but that doesn't seem to have done anything. They still have comments stating they were "disabled by Natty" or something. 

Any ideas?

EDIT: sorry, forgot something: when I upgrade via terminal I get 4 or 5 404 messages. Not sure if that's related or not :X

---

### Post by wilee-nilee on 2011-04-27
run in the terminal
sudo update-grub

If you have burg use 
sudo update-burg

If you clicked those repos on you have to run update grub to get them available. Check to that they are all set as Natty by the cat list readout, or from software sources

If you want to see the apt source list here is the read not write to command.
cat /etc/apt/sources.list

If you want to actually modify it be very careful and run this command to bring it up
sudo gedit /etc/apt/sources.list

Here is my cat list as a reference for you.
 ```
cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
# deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
# deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu maverick main
## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
# deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free

```

---

### Post by garvinrick4 on 2011-04-27
> EDIT: sorry, forgot something: when I upgrade via terminal I get 4 or 5 404 messages. Not sure if that's related or not :X A lot of PPA's and medibuntu do not have natty's open at this time, either wait a day and see if they are open or change them to maverick
in 
```
gksudo gedit /etc/apt/sources.list
```
change hit save and done.

* Now below you see I just commented out (#)  in natty for medibuntu, makes it out of play.
and just added a medibuntu maverick without the (#)  and it is in play.
The one with natty would have gotten the 404 message if I would have taken out the comment sign.
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-backports restricted main multiverse universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

---

### Post by ZachGretzinger on 2011-04-28
> **wilee-nilee said:**
> run in the terminal
sudo update-grub

If you have burg use 
sudo update-burg

If you clicked those repos on you have to run update grub to get them available. Check to that they are all set as Natty by the cat list readout, or from software sources

If you want to see the apt source list here is the read not write to command.
cat /etc/apt/sources.list

If you want to actually modify it be very careful and run this command to bring it up
sudo gedit /etc/apt/sources.list

Here is my cat list as a reference for you.
 ```
cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
# deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
# deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
# deb-src http://extras.ubuntu.com/ubuntu maverick main
## Depôt MultiSystem
deb http://liveusb.info/multisystem/depot all main
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
# deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free

```



Thanks a lot man!

Lol that actually fixed another issue I was having trouble with (being able to download and install from playdeb.net)

---

