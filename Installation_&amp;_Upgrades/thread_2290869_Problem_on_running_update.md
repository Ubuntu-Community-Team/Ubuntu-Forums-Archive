---
title: "Problem on running update"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-08-16
Hi all

Ubuntu 14.04 desktop

On running
$ sudo apt-get update;```

....
Err http://ppa.launchpad.net trusty/main amd64 Packages                   
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_HK
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Pls advise how to fix this problem.  Tks

Regards
satimis

---

### Post by dino99 on 2015-08-16
if you use ppa(s) then i suppose you know how to check an url with your browser, dont you ?

the two first urls are incomplete, and makes no sense; worst they ask for both i386 & amd64 (an other no sense)
pmcenery is an oldish ppa no maintained since ages.
Do you really know why you are using those ppas ?
i suppose you need also to deactivate them are clean your system (ppa-purge) to avoid stupid conflicts/version mismatches

---

### Post by satimis on 2015-08-16
> **dino99 said:**
> if you use ppa(s) then i suppose you know how to check an url with your browser, dont you ?

the two first urls are incomplete, and makes no sense; worst they ask for both i386 & amd64 (an other no sense)
pmcenery is an oldish ppa no maintained since ages.
Do you really know why you are using those ppas ?
i suppose you need also to deactivate them are clean your system (ppa-purge) to avoid stupid conflicts/version mismatches

Hi,

Thanks for your advice.  This is a VM of VirtualBox

Previously I followed;
How To Tether Your iPhone to Your Linux PC
[http://www.howtogeek.com/68999/how-to-tether-your-iphone-to-your-linux-pc/](http://www.howtogeek.com/68999/how-to-tether-your-iphone-to-your-linux-pc/)

adding repository ppa:pmcenery/ppa to the source.list.

Now I can connect IPhone to the host and wouldn't pursue this topic further.  I'll remove this VM later.

Regards
satimis

---

### Post by Vladlenin5000 on 2015-08-16
As already commented. that PPA is unmaintained and very old. There's nothing for you there and you actually don't need anything else: iPhone support has been added since kernel 3.7. Just enable USB tethering on the phone then connect it. Done!

---

### Post by satimis on 2015-08-16
> **Vladlenin5000 said:**
> As already commented. that PPA is unmaintained and very old. There's nothing for you there and you actually don't need anything else: iPhone support has been added since kernel 3.7. Just enable USB tethering on the phone then connect it. Done!
Thanks

satimis

---

