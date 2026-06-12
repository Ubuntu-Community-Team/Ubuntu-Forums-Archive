---
title: "'dpkg --configure -a' error stuck from vmware"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by novus721 on 2007-04-17
Hey all

I am a week into ubuntu 6.1 and I LOVE it, minus these 'growth opportunities' - but here it is - my vmware install has gotten all messed up for some reason, I want to get rid of it and all of its commands but I can't seem to make that quite happen.  More importantly, every time I try to download something we get this error ```
you must manually run 'dpkg --configure -a' to correct the problem. 

```

and when i do that in root i get

```
root@ubuntu-desk:~# dpkg --configure -a
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.38.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

```

AND IT NEVER STOPS!

I just want to be able to download from SYNAPTIC which is blocked with this error and I have heard the vmserver is better than the player so I will install that but I CANT GET RID OF THIS! Please, any help would be GREATLY appreciated! Thank you!

---

### Post by novus721 on 2007-04-17
problem moderately fixed by doing apt-get update, i now have been able to download and work other things, however, every time i download and/or install something i get an error that not all packages have been acted upon successfully, showing vmplayer - I tried to get rid of it through the package manager but it did not want to be deleted...any ideas??

---

### Post by starlily on 2007-05-21
This should fix the problem:
[http://ubuntuforums.org/showthread.php?t=426198](http://ubuntuforums.org/showthread.php?t=426198)

Lily

---

