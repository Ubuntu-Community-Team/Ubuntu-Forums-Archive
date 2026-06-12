---
title: "Unityshell-rotated PPA broken?"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by CFJensen on 2013-01-07
Hi,

I've tried to install unityshell-rotated, as I would like my launcher at the bottom of the screen. However, when I add the ppa, I get the following:

```
gpg: keyring `/tmp/tmpapd1gp/secring.gpg' created
gpg: keyring `/tmp/tmpapd1gp/pubring.gpg' created
gpg: requesting key 4933B6AB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpapd1gp/trustdb.gpg: trustdb created
gpg: key 4933B6AB: public key "Launchpad PPA for Pavel Golikov" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```but then upon update:
```
W: Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```and then when trying to install, I naturally get:
```
XX@XXX:~$ sudo apt-get install unityshell-rotated
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unityshell-rotated

```Am I doing something wrong? Is the PPA broken? If yes, does anyone else know how I can move the unity launcher? I'm on a 12" screen, so vertical screen estate is quite valuable to me.

---

### Post by haqking on 2013-01-07
doesnt seem to be a quantal

[http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/](http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/)

[https://launchpad.net/~paullo612/+archive/unityshell-rotated](https://launchpad.net/~paullo612/+archive/unityshell-rotated)

---

### Post by Frogs Hair on 2013-01-07
AFIK it only worked on the version of Unity for Ubuntu 11.10 32 bit. The last build was almost a year ago. [https://launchpad.net/~paullo612/+archive/unityshell-rotated](https://launchpad.net/~paullo612/+archive/unityshell-rotated)

---

### Post by CFJensen on 2013-01-07
> **Frogs Hair said:**
> AFIK it only worked on the version of Unity for Ubuntu 11.10 32 bit. The last build was almost a year ago. [https://launchpad.net/~paullo612/+archive/unityshell-rotated](https://launchpad.net/~paullo612/+archive/unityshell-rotated)

Yeah, I don't know, the guide I found said 12.04 though. [http://ishouvik.com/move-unity-launcher-to-bottom-12-0411-10](http://ishouvik.com/move-unity-launcher-to-bottom-12-0411-10) 

Do you know a different way to move it?

---

### Post by haqking on 2013-01-07
> **CFJensen said:**
> Yeah, I don't know, the guide I found said 12.04 though. [http://ishouvik.com/move-unity-launcher-to-bottom-12-0411-10](http://ishouvik.com/move-unity-launcher-to-bottom-12-0411-10) 

Do you know a different way to move it?

I believe it is not supported after 11.10

[http://ubuntuforums.org/showthread.php?t=1976480](http://ubuntuforums.org/showthread.php?t=1976480)

see 58 [http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher](http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher)

---

### Post by CFJensen on 2013-01-07
> **haqking said:**
> doesnt seem to be a quantal

[http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/](http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/)

[https://launchpad.net/~paullo612/+archive/unityshell-rotated](https://launchpad.net/~paullo612/+archive/unityshell-rotated)

Too bad, but then again it should just be a native choice anyway.

---

### Post by CFJensen on 2013-01-07
> **haqking said:**
> I believe it is not supported after 11.10

[http://ubuntuforums.org/showthread.php?t=1976480](http://ubuntuforums.org/showthread.php?t=1976480)

see 58 [http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher](http://askubuntu.com/questions/33605/can-i-move-the-unity-launcher)

Looks like you're right. Shame. I read 58 before, and I just understood it as no native support in 12.04 and no intention to add it because no reason. After all, he says no official support, and paullo's was always unofficial.

---

