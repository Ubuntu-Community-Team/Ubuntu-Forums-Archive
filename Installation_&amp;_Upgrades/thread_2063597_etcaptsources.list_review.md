---
title: "/etc/apt/sources.list review"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by mailc on 2012-09-27
Please have a look at  this  /etc/apt/sources.list   and tell me what needs removal or what else I should be done.  I see some duplicates and at least one 'debian'.

Thanks


    ```
 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha i386 (20120122)]/ precise main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://debian.anonymous-proxy-servers.net precise main
deb http://www.duinsoft.nl/pkg debs all
deb http://apt.bitcoins.sk/ precise main  
```

---

### Post by snowpine on 2012-09-27
Welcome to the forums! Are you having particular problems or errors that lead you to believe there is an error in your sources.list?

I see a few non-ubuntu sources at the end of your list, but I don't know what they do or why you added them. Can you clarify/explain these entries?

---

### Post by mailc on 2012-09-27
Updates are sometimes slow.
I see mirror.cc.columbia.edu  listed 14 times. Is this normal?

The 3  non-ubuntu sources at the end are fine.

Thanks

---

### Post by dino99 on 2012-09-27
you can use System Tools -> Preferences -> Software Sources

to:
- comment out the lines starting with deb-scr, if you never compile
- change to the main server or your local server, instead of your colombia mirror

---

### Post by mailc on 2012-09-27
> **dino99 said:**
>  ....
  if you never compile

  
What do you mean by '**Compiling**'?  How do I so that?

The last 3 are for updates for Java, Bitcoins and JonDo.

I got to mirror.cc.columbia.edu by running :

Synaptic->Settings->REpos-->Ubuntu  Software->Download from -->Other : said that columbia mirror is  fastest for me.
But does it need to be listed** 14 times**? Are they interfering with each other?

This should be easier to see:
```
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main universe restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main   
```

---

### Post by snowpine on 2012-09-27
Looks OK to me. It is normal to have several entries from the same mirror. If you look carefully, you'll see none are exact duplicates.

---

