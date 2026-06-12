---
title: "sources.list error"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2008-03-05
I'm trying to add a new link to the sources.list using a terminal: "**sudo gedit /etc/apt/sources.list**".
After writing the link: **deb [http://ftp.fr.debian.org/debian](http://ftp.fr.debian.org/debian) **into the list and making the update in writing "**sudo apt-get update**" I get the message: **E: Malformed line 59 in source list /etc/apt/sources.list (dist)**.
Also trying putting the repository with the menu option System -Administration Software Sources -Third-Party Software - Add the pop-up menu doesn't allow me to add the source.

If I write "**sudo apt-get update**" I get an error:

Reading package lists... Done
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

W: You may want to run apt-get update to correct these problems

thks for help.

---

### Post by kellemes on 2008-03-05
Please post /etc/apt/sources.list

---

### Post by drumanart on 2008-03-05
**Here is the list:**

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy multiverse main universe restricted
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-updates multiverse main universe restricted
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
##deb [http://ftp.fr.debian.org/debian](http://ftp.fr.debian.org/debian)

## From bock of Wiliam von Hagen

# deb-src [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx

## Pd repositories
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
## deb [http://ftp.fr.debian.org/debian](http://ftp.fr.debian.org/debian)



# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security multiverse
# Line commented out by installer because it failed to verify:

---

### Post by taurus on 2008-03-05
It is extremely bad idea to mix repos in /etc/apt/sources.list.  Therefore, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove these lines from it.

```

## Pd repositories
deb http://www.debian-multimedia.org stable main
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
## deb http://ftp.fr.debian.org/debian

```
Then, remove the # in front of these lines that start with deb & deb-src.

```

# Line commented out by installer because it failed to verify:
# deb http://ad.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ad.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://ad.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ad.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://ad.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://ad.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://ad.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://ad.archive.ubuntu.com/ubuntu/ gutsy-updates universe

```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```
And if you need to install codes, try Medibuntu, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by drumanart on 2008-03-05
**I get the same error:**
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

**The new list:**

# Line commented out by installer because it failed to verify:
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy multiverse main universe restricted
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-updates multiverse main universe restricted
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
martin@martin-desktop:~$ 

## From bock of Wiliam von Hagen

deb-src [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx


##deb [http://ftp.fr.debian.org/debian](http://ftp.fr.debian.org/debian)



# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security universe
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://ftp.udc.es/ubuntu/](http://ftp.udc.es/ubuntu/) gutsy-security multiverse
# Line commented out by installer because it failed to verify:

---

### Post by drumanart on 2008-03-05
**Sorry the failer is here:**
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
martin@martin-desktop:~$

---

### Post by kellemes on 2008-03-05
> **drumanart said:**
> **Sorry the failer is here:**
W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
martin@martin-desktop:~$


Change the following line..
```
deb-src http://mirror3.ubuntulinux.nl/ dapper-seveas freenx
```
to
```
# deb-src http://mirror3.ubuntulinux.nl/ dapper-seveas freenx
```

Now see how it works..

Clean up the sources.list, have it all work and then you can add 3-rd party repositories like Seveas'
You should have used "deb-src [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) gutsy-seveas freenx" anyhow. ;-)

---

### Post by drumanart on 2008-03-05
great it works, but still it is impossible to put a link in **System**- **Adminidtration ** -**[B]Software **Sources [/B]-** Third-Party Software**- **Add **- the   add source botton keeps desactivated.

---

### Post by kellemes on 2008-03-05
> **drumanart said:**
> great it works, but still it is impossible to put a link in **System**- **Adminidtration ** -**[B]Software **Sources [/B]-** Third-Party Software**- **Add **- the   add source botton keeps desactivated.

Can't help you with this since I never go this way.. I tend to edit the files directly..

---

### Post by zvacet on 2008-03-05
Let it look like this again

deb-src [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx

and after you saved and closed file type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 49A120FD1135D466
gpg --export --armor 49A120FD1135D466 | sudo apt-key add -

```
sudo apt-get update
```

---

### Post by drumanart on 2008-03-05
**[B]thks**a lot for the help.[/B]

---

