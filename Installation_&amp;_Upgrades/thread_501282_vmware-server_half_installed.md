---
title: "vmware-server half installed"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by andytof47 on 2007-07-15
hi I have a problem and I have tried the fixes sugested in the forums but it only half works so i'm wondering if we can help a brother out.... vmware won't uninstall and won't install

i tried ```
dpkg -a
```
```
apt-get purge
```


and a few others but to no avail.......


I checked launchpad and the bug reports but my solution still hasn't been found and i am quickly going insane:)(nervous laugh)

here is my dpkg log
```
2007-07-15 17:08:20 status unpacked xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:08:20 status unpacked xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:08:20 status unpacked xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:08:20 status half-configured xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:08:20 status installed xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 status installed xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 remove xinetd 1:2.3.14-1ubuntu1 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 status half-configured xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 status half-installed xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 status config-files xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 status config-files xinetd 1:2.3.14-1ubuntu1
2007-07-15 17:11:05 install vmware-server <none> 1.0.3-1
2007-07-15 17:11:05 status half-installed vmware-server 1.0.3-1
2007-07-15 17:11:54 status not-installed vmware-server <none>
2007-07-15 17:11:54 install vmware-tools-kernel-modules-2.6.20-16 <none> 2.6.20.5-16.29
2007-07-15 17:11:54 status half-installed vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:11:54 status unpacked vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:11:54 status unpacked vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:11:54 install vmware-tools-kernel-modules <none> 2.6.20.16.28.1
2007-07-15 17:11:54 status half-installed vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:11:54 status unpacked vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:11:54 status unpacked vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:12:07 install vmware-server <none> 1.0.3-1
2007-07-15 17:12:07 status half-installed vmware-server 1.0.3-1
2007-07-15 17:12:13 status not-installed vmware-server <none>
2007-07-15 17:15:01 install vmware-server <none> 1.0.3-1
2007-07-15 17:15:01 status half-installed vmware-server 1.0.3-1
2007-07-15 17:15:05 status not-installed vmware-server <none>
2007-07-15 17:15:20 install vmware-server <none> 1.0.3-1
2007-07-15 17:15:20 status half-installed vmware-server 1.0.3-1
2007-07-15 17:18:49 status not-installed vmware-server <none>
2007-07-15 17:19:04 install vmware-server <none> 1.0.3-1
2007-07-15 17:19:04 status half-installed vmware-server 1.0.3-1
2007-07-15 17:19:11 status not-installed vmware-server <none>
2007-07-15 17:21:52 status unpacked vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:21:52 status half-configured vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:21:58 status installed vmware-tools-kernel-modules-2.6.20-16 2.6.20.5-16.29
2007-07-15 17:21:58 status unpacked vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:21:58 status half-configured vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:21:58 status installed vmware-tools-kernel-modules 2.6.20.16.28.1
2007-07-15 17:22:12 install vmware-server <none> 1.0.3-1
2007-07-15 17:22:12 status half-installed vmware-server 1.0.3-1
2007-07-15 17:22:13 status not-installed vmware-server <none>
2007-07-15 17:22:18 install vmware-server <none> 1.0.3-1
2007-07-15 17:22:18 status half-installed vmware-server 1.0.3-1
2007-07-15 17:22:31 status not-installed vmware-server <none>
2007-07-15 17:27:26 install vmware-server <none> 1.0.3-1
2007-07-15 17:27:26 status half-installed vmware-server 1.0.3-1
2007-07-15 17:27:44 status not-installed vmware-server <none>
```



I appreciate any help

---

### Post by Koybe on 2007-07-15
What if you remove it? 
```
sudo apt-get remove vmware-server vmware-tools-kernel-modules
```

or even purge (--purge before remove) it before reinstall ?

Maybe this is related with [http://ubuntuforums.org/showthread.php?t=501168](http://ubuntuforums.org/showthread.php?t=501168)

---

### Post by andytof47 on 2007-07-15
hmmmm. not sure why but it seems to working now----

I solved it by using synaptic and marked for complet removal.... I don't know why this worked but i'm also not complaining


cheers

---

