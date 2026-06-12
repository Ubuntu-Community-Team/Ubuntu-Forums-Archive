---
title: "problem in installing  libfyba0"
date: 2022-06-24
forum: Installation &amp; Upgrades
---

### Post by yueli7 on 2022-06-24
Hello,

I have problem in installing libfyba0.

Thank you in advance for great help!

Best,

Yue


```
li@li-ThinkStation-P330:~$ sudo apt-get install libfyba0[sudo] password for yueli: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libice6:i386 libsm6:i386 libxt6:i386
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libfyba0
0 upgraded, 1 newly installed, 0 to remove and 176 not upgraded.
Need to get 113 kB of archives.
After this operation, 327 kB of additional disk space will be used.
Err:1 http://cn.archive.ubuntu.com/ubuntu focal/universe amd64 libfyba0 amd64 4.1.1-6build1
  Connection failed [IP: 91.189.91.38 80]
E: Failed to fetch http://cn.archive.ubuntu.com/ubuntu/pool/universe/f/fyba/libfyba0_4.1.1-6build1_amd64.deb  Connection failed [IP: 91.189.91.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by Impavidus on 2022-06-24
You have 176 upgrades waiting. Those are bugfixes. Best to install them right away. If that's too much for you, you can disable upgrades from the -updates repository, but keep at least -security enabled. If you install something now, that could trigger a whole series of upgrades of dependencies and reverse dependencies of those. If you now disable -updates but have already installed software from there, you may get dependency problems when you install something later. So, best to simply install all those updates.

That's not the cause of your problem. There appears to be a connection problem. Maybe it's temporary; then you can try again later. Or you can change to a different server. Maybe you have to check firewall settings.

Normally those lib* packages get automatically pulled in as a dependencies of either the application you wish to install or of the lib*-dev package you need to compile something yourself, but it's OK.

---

