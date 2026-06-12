---
title: "gutsy upgrade to hardy behind proxy"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by pooyaplus on 2008-07-20
Hi, I have googled all possible variants of this thread to make sure that there are no duplicate of this anywhere else. If there please let me know.

Anyway, I have been trying to upgrade to hardy from gutsy using the alternative disk multiple times. I am connected to the Internet via a proxy server that requires authentication. I tried either not to get updates from the Internet and also opted to get them with no success when the upgrade process asks. 

The global proxy setting in gnome and the synaptic network proxy setting are set and everything is working fine regarding the updates and Internet connectivity. 

Is there any workarounds for this issue?

---

### Post by pooyaplus on 2008-07-20
Bump :-|

---

### Post by pooyaplus on 2008-07-20
Besides, the interesting point is the number of available updates shown in the notification icon after the incomplete upgrade procedure, it shows more than 6 hundred updates are available. And when attempting to open the update manager it pops up a warning message saying: "Not all updates can be installed" (obvious fact)  and continues: "Run a partial upgrade to install as much updates as possible" and prompts for a partial upgrade!

---

### Post by bapoumba on 2008-07-20
Have you managed to enable the proxy and install the updates ? (the partial update message is probably due to an incomplete sources.list file).

---

### Post by pooyaplus on 2008-07-20
> **bapoumba said:**
> Have you managed to enable the proxy and install the updates ? (the partial update message is probably due to an incomplete sources.list file).

As I said, the proxy is enabled and everything from the update manager to the terminal apt-get etc. is working fine. The only strange thing is that why the proxy authentication is not functioning for the upgrade procedure. I suppose they share the same settings with the synaptic regarding the network settings and configurations. Right?

---

### Post by bapoumba on 2008-07-20
Up to gutsy, I used to declare the proxy in the **/etc/apt/apt.conf** file: [http://linux.die.net/man/5/apt.conf]("http://linux.die.net/man/5/apt.conf"). The Acquire Group is what you are looking for. The syntax should be:
```
[noparse]ACQUIRE {
http://[[user][:pass]@]host[:port]/
};[/noparse]
```
With hardy, I do not need it any longer.

Is this an ISA proxy ? (if so, the procedure may be different).

---

### Post by pooyaplus on 2008-07-21
Hi, 
I used to use the acquire thing in the 7.04 to get the terminal Internet connectivity. But in gutsy I just set the global gnome proxy and synaptic proxy settings.

---

### Post by bapoumba on 2008-07-21
Hmm, then please post the output to :
```
sudo apt-get update
```
and your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by pooyaplus on 2008-07-22
Hi, I have been trying to get rid of unwanted hardy updates in my gutsy by reloading the repository after removing the hardy keys form the repository settings.

There are lots of hardy repos in the sources.list. I tried removing them from the file.
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/ feisty main restricted
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
#deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://archive.ubuntu.com/ubuntu/ hardy universe

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
# deb http://ir.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ir.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main universe multiverse #Added by software-properties
#deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
#deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main universe multiverse #Added by software-properties

#deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe multiverse

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/ feisty main restricted
# deb http://packages.medibuntu.org/ feisty free non-free



deb http://archive.ubuntu.com/ubuntu/ gutsy main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted

```

---

### Post by pooyaplus on 2008-07-22
It seems that the manual removal of the hardy keys and repos form the sources.list did remove the 600 updates. But I still can not upgrade to hardy with alternate CD 8.0.4.01

---

### Post by bapoumba on 2008-07-22
> **pooyaplus said:**
> It seems that the manual removal of the hardy keys and repos form the sources.list did remove the 600 updates. But I still can not upgrade to hardy with alternate CD 8.0.4.01
If you want to upgrade from the CD, you need to uncomment (remove the #) the corresponding line in your sources.list, ie this one:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
```
**and** comment (add a #) to the gusty repos, the three last lines.
So you keep only the CD line uncommented, then run:
```
sudo apt-get update
sudo apt-get dist-upgrade

```

Once upgraded, you can comment again the CDrom line, and uncomment the hardy repos only. In addition, when everything will be running fine, you should delete the feisty and gutsy repos.

---

### Post by pooyaplus on 2008-07-22
Then what would be the point? It wont proceed due to that proxy authorization problem.

---

### Post by bapoumba on 2008-07-22
Even with only the CDrom repo active in the sources.list?
Edit: have you been using some other proxy (like anon) ?

---

### Post by pooyaplus on 2008-07-22
Yes, it's been from the very first hours of the release of the hardy I have been trying to upgrade it. The proxy is CMS, I guess. I do not understand why the upgrade app does not follow the proxy instructions of the synaptic and global gnome settings.:mad:

---

### Post by bapoumba on 2008-07-22
please look in your .bashrc, /etc/bash.bashrc, /etc/environment if you have anything about the proxy there.
If you leave only the CDrom in /etc/apt/sources.list, remove the proxy from the environment and do not have it set up anywhere else, you should be able to upgrade from the CD (I've done it on a laptop that ran out of battery during an upgrade and had no network whatsoever after, but still a partly functional recovery mode).

---

### Post by pooyaplus on 2008-07-23
Will give it a try. Thanks.

---

### Post by akaihola on 2008-08-05
One of the problems might be [this bug]("https://bugs.launchpad.net/ubuntu/+bug/245219").

---

