---
title: "Error while installing prozilla in ubuntu 12.10"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by xxsmarty on 2013-02-07
I am trying to install prozilla from a ppa:
But i have this error:
```

arun@arun-Inspiron-5520:~$ sudo apt-get install prozilla 
[sudo] password for arun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  prozilla
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/137 kB of archives.
After this operation, 519 kB of additional disk space will be used.
(Reading database ... 254964 files and directories currently installed.)
Unpacking prozilla (from .../prozilla_2.0.4~quantalbuild1-0tahutek1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/prozilla_2.0.4~quantalbuild1-0tahutek1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/locale.alias', which is also in package locales 2.13+git20120306-3
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Processing triggers for lintian ...
Errors were encountered while processing:
 /var/cache/apt/archives/prozilla_2.0.4~quantalbuild1-0tahutek1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Can anyone help ?
I am seriously troubled....:evil:

---

