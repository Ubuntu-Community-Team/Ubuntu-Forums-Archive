---
title: "Error: Unable to correct problems, you have held broken packages"
date: 2018-03-05
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2018-03-05
Hello,

I've recently installed Ubuntu 16.04.4 (64-bit) while previously I was using 16.04.1 (32-bit).

It was a clean install and things are generally working fine. However, for some packages I am getting this error e.g., if I try to install VLC from default repositories I get this

```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
       Depends: libgles2-mesa (>= 7.8.1) but it is not going to be installed or
                libgles2
E: Unable to correct problems, you have held broken packages.
```

Similarly if I try to install Wireshark

```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wireshark : Depends: wireshark-qt but it is not going to be installed or
                      wireshark-gtk but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

There are other packages as well which are important to me but are failing to be installed because of this problem. I suspect that these packages have not yet been updated with the underlying Ubuntu distribution i.e., 16.04.4

Any suggestions / help please?

---

### Post by deadflowr on 2018-03-05
What does 
```
sudo apt update
```
show?
Any errors or fail to fetches?

---

### Post by anspectrum on 2018-03-05
Nah, no errors in there whatsoever. Here is the output:

> sudo apt update 
Hit:1 [http://ppa.launchpad.net/gns3/ppa/ubuntu](http://ppa.launchpad.net/gns3/ppa/ubuntu) xenial InRelease
Hit:2 [http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu) xenial InRelease
Hit:3 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:4 [http://ppa.launchpad.net/obsproject/obs-studio/ubuntu](http://ppa.launchpad.net/obsproject/obs-studio/ubuntu) xenial InRelease   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

---

### Post by deadflowr on 2018-03-05
Odd, you seem to be hitting a only a single Ubuntu repo.
What are your sources?
run 
```
cat /etc/apt/sources.list
```
and post the results.

---

### Post by anspectrum on 2018-03-05
@deadflowr, Thanks for the prompt reply. Here is the output:

```
cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

```

---

### Post by deadflowr on 2018-03-05
You need to enable -updates and -security repos.
Those should contain the updated packages you need,
[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab")
Look in Software Sources.

---

### Post by anspectrum on 2018-03-05
@deadflowr, Wow! You rock. Bang on.

I had not thought that disabling updates resources would create this problem. Thank you very much its fixed and all good now.

(Y)

---

### Post by sofiapara on 2018-06-07
@deadflower many thanks! that really solved the big pain :)

---

