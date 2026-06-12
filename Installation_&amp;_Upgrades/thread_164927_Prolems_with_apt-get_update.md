---
title: "Prolems with apt-get update"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by codypumper on 2006-04-23
sudo apt-get update returns a bunch of errors, upgrade returns a message telling me to apt-get update...

---

### Post by aysiu on 2006-04-23
Can you post the error you get?

---

### Post by codypumper on 2006-04-23
Yeah, here:
> 
'pumpers@ubuntu:~$ sudo apt-get update
Password:
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Get:1 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://theli.free.fr](http://theli.free.fr) ./ Packages
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [46.1kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [14.6kB]
Get:15 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [32.0kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:23 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:27 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:28 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:29 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Fetched 281kB in 27s (10.1kB/s)
Reading package lists... Done
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures were invalid: BADSIG A506E6D4DD4D5088 Jonathan Riddell <jriddell@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures were invalid: BADSIG E8DDB29170188C3B Osmo Salomaa (Osmo Salomaa's GPG key) <otsaloma@cc.hut.fi>
W: You may want to run apt-get update to correct these problems
pumpers@ubuntu:~$

---

### Post by Fredde on 2006-04-23
[QUOTE=codypumper]upgrade returns a message telling me to apt-get update...[/QUOTE]

did you try sudo apt-get update?

edit: I missread

---

### Post by codypumper on 2006-04-23
Yes I did, that's where the error is coming from!

---

### Post by Fredde on 2006-04-23
I apologies. Have you tried with synapatic and reload?

---

### Post by codypumper on 2006-04-23
Yes, why?

---

### Post by codypumper on 2006-04-23
Yes, that gives me another error

---

### Post by Fredde on 2006-04-23
Do you have any backups of your source.list?

---

### Post by codypumper on 2006-04-23
I don't have any backups


Synaptic gives me the error:
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures were invalid: BADSIG A506E6D4DD4D5088 Jonathan Riddell <jriddell@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures were invalid: BADSIG E8DDB29170188C3B Osmo Salomaa (Osmo Salomaa's GPG key) <otsaloma@cc.hut.fi>

---

### Post by codypumper on 2006-04-23
No, I don't have any backups

---

### Post by Fredde on 2006-04-23
[QUOTE=codypumper]No, I don't have any backups[/QUOTE]

Make a backup and try if this source.list works.
```
# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
```

---

### Post by codypumper on 2006-04-23
How do you make a backup?

---

### Post by Fredde on 2006-04-23
You copy it, by the way, do you use kubuntu? if so, I don't think you can use that source.list.

---

### Post by codypumper on 2006-04-23
No, I have plain old gnome

---

### Post by codypumper on 2006-04-23
What do you mean copy it? (sorry)

---

### Post by Fredde on 2006-04-23
This is for ubuntu 5.10, so I hope you use it.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
```
sudo gedit /etc/apt/sources.list
```
```
# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
```
```
sudo apt-get update
```

---

### Post by codypumper on 2006-04-23
My source list code:
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arnielistenadded

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted

---

### Post by Fredde on 2006-04-23
relpace your source.list with
```
# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
```
```
sudo apt-get update
```

---

### Post by codypumper on 2006-04-23
The first code gives me an error.
My source list is above.
It won't let me edit my source list

---

### Post by Fredde on 2006-04-23
you have to
```
sudo gedit /etc/apt/sources.list
```

---

### Post by codypumper on 2006-04-23
It still gives me at the end:
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
pumpers@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

And when I reload synaptic I get:
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Fredde on 2006-04-23
[QUOTE=codypumper]pumpers@ubuntu:~$ apt-get update[/QUOTE]
it should be
```
sudo apt-get update
```

---

### Post by codypumper on 2006-04-23
What do you mean it should be?

---

### Post by Fredde on 2006-04-23
you wrote
```
apt-get update
```
it has to be
```
sudo apt-get update
```

---

### Post by codypumper on 2006-04-23
I know!

---

### Post by Fredde on 2006-04-23
[QUOTE=codypumper]I know![/QUOTE]
and how did it turn out?

---

### Post by codypumper on 2006-04-23
It still gives me at the end:
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
pumpers@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by Fredde on 2006-04-23
[http://files.upl.silentwhisper.net/upload3/apt.png](http://files.upl.silentwhisper.net/upload3/apt.png)
left you and right me.

---

### Post by codypumper on 2006-04-23
no comment

---

### Post by codypumper on 2006-04-23
Hey Fredde I "fixed" the problem.
I changed all the "breezy"s in source.list to "dapper"
(a big risk)
It works!

---

### Post by jpeirce on 2006-04-23
I am getting a similar error starting today with a bad GPG signing from us.archive.ubuntu.com:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

sources.list:
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/



edit: after using a mirror other than us.archive.ubuntu.com it works without fail.

---

