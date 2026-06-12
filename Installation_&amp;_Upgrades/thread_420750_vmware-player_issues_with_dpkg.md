---
title: "vmware-player issues with dpkg"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by KyleYankan on 2007-04-23
Hi everyone. I'm having some troubles with vmware products. I had vmware-player working at one point but then tried to install vmware-server. I have to say, I thoroughly botched something up. Every time i use apt-get I get errors now. When I searched for a solution I was told to run "apt-get install -f" as su. This results in the same dpkg error. Any help?

```
root@Brandy:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
cp: cannot stat `/usr/lib/vmware-player/share/locations.dist': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Brandy:~# 

```

---

### Post by rbmorse on 2007-04-23
It's known issue with recent kernels.  But, check the vmware site.  I just (like a couple of minutes ago) received an announcement that Player 2.0 RC is available for evaluation (no cost).  

VMWorkstation 5.5 had the same problem but Workstation 6 RC installs easily on Feisty.I imagine Player 2.0 contains the same bug fix.

---

