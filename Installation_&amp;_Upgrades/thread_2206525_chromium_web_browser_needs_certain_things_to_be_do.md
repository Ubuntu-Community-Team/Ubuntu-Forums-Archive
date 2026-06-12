---
title: "chromium web browser needs certain things to be downloaded first"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by chillering on 2014-02-19
ubuntu 13.10 (64-bit)
I downloaded chrome for linux "google-chrome-stable_current_amd64" from chrome's website and used terminal commands but installation fails and gives error. 
Software center "chromium" webbrowser also gives an error. See the attachment and kindly help me solve the issue.

---

### Post by Ubi_one_2014 on 2014-02-19
try apt-get -f install from terminal

also pls post, as non-root
cat /etc/apt/sources.list

---

### Post by chillering on 2014-02-20
> **Ubi_one_2014 said:**
> try apt-get -f install from terminal

also pls post, as non-root
cat /etc/apt/sources.list

That is the output of apt-get -f install
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

and for cat/etc/apt/sources.list I got
```

deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy universe
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main

```

---

### Post by chillering on 2014-02-21
Need help here.

---

### Post by westie457 on 2014-02-21
Which terminal command did you use to install?

In the meantime you could give this a try ```
sudo dpkg --configure -a
```
Might be enough to fix this.

---

### Post by chillering on 2014-02-21
> **westie457 said:**
> Which terminal command did you use to install?

In the meantime you could give this a try ```
sudo dpkg --configure -a
```
Might be enough to fix this.

Typing this command did nothing.

---

### Post by westie457 on 2014-02-21
Did the command return to a blank line or were there errors?

Again, which terminal command did you use for the installation?

---

