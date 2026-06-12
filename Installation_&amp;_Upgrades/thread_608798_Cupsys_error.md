---
title: "Cupsys error"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by indianballer24 on 2007-11-10
I am completely new and I would appreciate your help.

I installed gutsy and the first thing I did was upgrade. At the end of the upgrade I got a message saying that there was an error updating cupsys. Now everytime I try to install somthing I get an error about cupsys. Can someone please help me?

I am using a persistent installation on a usb drive.

---

### Post by bpazolli on 2007-12-02
I have the exact same problem and was about to start a new thread. I tried reinstall cupsys and no help. It is also giving me this error if I put apt-get update
```
W: GPG error: http://http.us.debian.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

```

Any help please

---

### Post by bpazolli on 2007-12-02
I don't think the error I posted above is related but here is a related error when I try install anything I get this error "E: cupsys: subprocess post-installation script returned error exit status 1"

---

### Post by aselya1 on 2007-12-14
I was getting something similar on a persistent Xubuntu 7.10 install. It turned out to be this bug: [https://bugs.launchpad.net/bugs/131976](https://bugs.launchpad.net/bugs/131976) which was fixed with ```
sudo aa-complain cupsd
```
When you attempt the installation in Synaptic, check the details of the installation for this: > cannot apply additional memory protection after relocation If its there, it might be the same problem. Basically, AppArmor doesn't work nicely with stacked filesystems.

---

### Post by aselya1 on 2008-01-14
I've tried Persisten Live USB 8.04 daily builds and none of them have this problem, so it appears to be fixed for Hardy! Sweet!

---

### Post by readyartbrut on 2008-05-06
I have the same issue as this and pasted sudo aa-complain cupsd into terminal and the problem is still there, any help would be appreciated.

I am on gutsy and havent upgraded anything, this problem appeared yesterday.

---

### Post by atomkind on 2008-05-25
Has anyone had any luck with this?
This is what I'm getting:
```
Setting up cupsys (1.3.2-1ubuntu7.7) ...
Reloading AppArmor profiles : done.
Error in `/usr/share/doc-base/cupsys', line 1: the first line does not contain valid `Document' field
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

