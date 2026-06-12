---
title: "Problem with Update Manager &amp; Add/Remove Software"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-01-12
A client of mine recently attempted to install Automatix on their own, but I think they downloaded a very very old version of it.  I noticed that it added software sources for version 5-something of Ubuntu.

Anyway, when he tries to run Update manager, it produces the following error:

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.'
```

And if I tried to run Add/Remove software, I get this:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

If I open Terminal, and type sudo apt-get install -f, it doesn't really appear to fix the problem, and the same errors are generated after trying to run Update manager or Add/Remove again.

How can this be fixed?

---

### Post by taurus on 2008-01-12
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by diablo75 on 2008-01-12
Here we go (please ignore the unnecessary \'s, they were inserted by accident by an e-mail php I use to send messages to myself quickly).

```
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the \'universe\'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the \'backports\'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse




# deb http://wine.sourceforge.net/apt/ binary/

# deb http://people.ubuntu.com/~doko/OOo2 ./

# deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
# deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi


deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
## created by arnieopera
```

---

### Post by PmDematagoda on 2008-01-12
Get a new sources.list file from [Source-O-Matic]("http://www.ubuntu-nl.org/source-o-matic/"), open Nautilus in root mode using:-
```
sudo nautilus
```
backup the old sources.list and replace the old sources.list with the new one from source-o-matic. After that is done, execute:-
```
sudo apt-get update
```
That should fix the problem.

---

### Post by SonicsDemon on 2008-01-13
Wow, I love Google. I've had this exact problem, and I am up late solving it. This helps fix things. Thank you:guitar:

---

