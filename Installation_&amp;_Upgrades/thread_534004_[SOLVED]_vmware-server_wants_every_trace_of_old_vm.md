---
title: "[SOLVED] vmware-server wants every trace of old vmware gone"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by howbag on 2007-08-24
Hello world!

I've been trying a lot making vmware work, and I've installed vmware player once on my machine, then removed it because I wanted to install the server edition, but the installation menu tells me that I have to purge (completely remove) the old version of vmware first!

I have gone through synaptic and selected "complete removal" on all vmware packages, but it doesn't help! :(

All installations were done with Synaptic package manager.

---

### Post by forestpixie on 2007-08-25
Sometimes there are files left behind, this will get rid of any in /etc

```
sudo rm -r /etc/vmware
```

then search for any other

```
 sudo find / -name vmware
```

and delete them 

Have a look at [this]("http://ubuntuforums.org/showthread.php?t=516916") thread

---

### Post by howbag on 2007-08-25
Ah, that and a reboot helped. Now xp is runing smooth, just got to get myself some vmware-tools ;)

Thank you!

---

### Post by Mach1US on 2007-09-15
Any idea how to reinstall or remove vmware tools ?

---

