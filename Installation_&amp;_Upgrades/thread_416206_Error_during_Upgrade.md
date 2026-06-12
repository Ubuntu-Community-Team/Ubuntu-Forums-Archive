---
title: "Error during Upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by adityakavoor on 2007-04-20
When I go to Applications -> Add / Remove.. I get the following error message

[B]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/B]

Then I loaded the terminal with the following code..  **sudo apt-get update**

Now I get this  message..

**E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list**


Please help

---

### Post by mlentink on 2007-04-21
Did you manually edit your sources file in some way? Add a repository perhaps?

---

### Post by jdong on 2007-04-21
Can you post us the contents of your /etc/apt/sources.list file?

Copy and paste the output of ```
ls -al /etc/apt/sources.list; sudo cat /etc/apt/sources.list
``` at a terminal. Please make sure to wrap it in [CODE] tags

---

### Post by adityakavoor on 2007-04-21
I loaded the terminal with the following code.. sudo apt-get update

Now I get this message..

E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list


Contents of **/etc/apt/sources.list** file..

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
“deb http://www.getautomatix.com/apt edgy main”

```

---

### Post by adityakavoor on 2007-04-21
didnt manipulate any sources.... added repositories though

---

### Post by Wicca on 2007-04-21
Just remove the "" from the last line in your sources.list:

```
deb http://www.getautomatix.com/apt edgy main
```

Save, and do *sudo apt-get update* again. You'll be fine.

Edit:
You better remove the the line completely, since it's a remainder of Edgy and I can't imagine you installed automatix this way on Feisty.

---

### Post by adityakavoor on 2007-04-21
thanks Wicca .... problem solved

By the way i'm still a beginner and fiesty is my first linux distro

---

### Post by Wicca on 2007-04-21
> **adityakavoor said:**
> By the way i'm still a beginner and fiesty is my first linux distro

Welcome on board adityakavoor. I hope you will enjoy Ubuntu as much as I am. Just take your time learning, and don't hesitate to ask a question on these wonderful forums.

---

