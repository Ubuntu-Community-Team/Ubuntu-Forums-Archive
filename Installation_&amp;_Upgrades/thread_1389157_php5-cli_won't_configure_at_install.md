---
title: "php5-cli won't configure at install"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by I Forgot My Username on 2010-01-24
I've had problems getting php5-cli installed, here's the output from the terminal.  All other packages I've tested have worked fine.
```

tyler@tyler-laptop:~$ sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cli
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,596kB of archives.
After this operation, 5,784kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com karmic-updates/main php5-cli 5.2.10.dfsg.1-2ubuntu6.4 [2,596kB]
Fetched 2,596kB in 21s (121kB/s)                                               
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package php5-cli.
(Reading database ... 157276 files and directories currently installed.)
Unpacking php5-cli (from .../php5-cli_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb) ...
Processing triggers for man-db ...
Setting up php5-cli (5.2.10.dfsg.1-2ubuntu6.4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

