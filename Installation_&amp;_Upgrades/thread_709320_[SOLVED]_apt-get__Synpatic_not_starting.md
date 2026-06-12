---
title: "[SOLVED] apt-get / Synpatic not starting"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by adityakavoor on 2008-02-27
I am not able to install anything using apt-get or synaptic

```

aditya@ubuntu:~$ sudo apt-get install vlc
Password:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
aditya@ubuntu:~$ 

```

Any Idea ?? :confused::confused:

Please Help :(

---

### Post by skippi90 on 2008-02-27
> **adityakavoor said:**
> I am not able to install anything using apt-get or synaptic

```

aditya@ubuntu:~$ sudo apt-get install vlc
Password:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
aditya@ubuntu:~$ 

```

Any Idea ?? :confused::confused:

Please Help :(


Open your /etc/apt/sources.list 

and check if they urls have been commented out. If so, remove the #'s and save.

---

### Post by adityakavoor on 2008-02-27
My sources.list

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by taurus on 2008-02-27
Maybe you need to run the update first?

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by skippi90 on 2008-02-27
Add this line to /etc/apt/apt.conf:


APT::Cache-Limit "8388608";

---

### Post by adityakavoor on 2008-02-27
> **taurus said:**
> Maybe you need to run the update first?

```
sudo apt-get update
sudo apt-get install vlc
```

Thanks mate ..  

It worked :popcorn:  :popcorn: :)

---

