---
title: "Synaptic Packet Manager Help"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Mosp on 2007-08-17
When I try to start the packet manager I get this error message:

E: Malformed line 38 in source list ect/apt/sources.list (URI parse)
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open()failed, please report.

I'm still pretty new to Ubuntu, so please help.

---

### Post by mikewhatever on 2007-08-17
Can you post the output of the following command from the Terminal
> cat /etc/apt/sources.list

---

### Post by Bachstelze on 2007-08-17
You certainly have a typo in your sources.list. Please apste the contents of the file :

```
cat /etc/apt/sources.list
```

EDIT : pwn3d :[

---

### Post by Pumalite on 2007-08-17
Post 'cat /etc/apt/sources.list'

---

### Post by Mosp on 2007-08-17
randy@randy-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb <a title="http://hendrik.kaju.pri.ee/ubuntu" href="http://hendrik.kaju.pri.ee/ubuntu">http://hendrik.kaju.pri.ee/ubuntu</a> feisty screenlets
randy@randy-desktop:~$

---

### Post by mikewhatever on 2007-08-17
Open the sources file for editing with > gksudo gedit /etc/apt/sources.list
Delete the last line, save and exit.

---

### Post by merlinus on 2007-08-17
Comment out this line and see what happens:

deb <a title="http://hendrik.kaju.pri.ee/ubuntu" href="http://hendrik.kaju.pri.ee/ubuntu">[http://he](http://he) ndrik.kaju.pri.ee/ubuntu</a> feisty screenlets


-merlin

---

### Post by Pumalite on 2007-08-17
That's funny: error says line 38, but you only have 35. I'll let the Gurus help you. I'm sure they can do a better job than I.

---

### Post by Mosp on 2007-08-17
Took out that last line, but there is no difference.

---

### Post by merlinus on 2007-08-17
Try this:

```

sudo apt-get update

```

and then try Synaptic again.

-merlin

---

### Post by Mosp on 2007-08-17
randy@randy-desktop:~$ sudo apt-get update
Password:
E: Malformed line 38 in source list /etc/apt/sources.list (URI)
randy@randy-desktop:~$

---

### Post by Mosp on 2007-08-17
Anyone have any idea how to fix it?

---

### Post by merlinus on 2007-08-17
Backup your current /etc/apt/sources.list, and then use mine:

> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


-merlin

---

### Post by Mosp on 2007-08-18
Thank you merlin. Using your source code fixed it.

---

