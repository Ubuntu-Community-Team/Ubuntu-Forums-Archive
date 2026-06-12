---
title: "Apt and empty file error"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by idn on 2007-10-16
HI

I cannot seem to install any new packages / upgrade etc, I keeping getting an empty file error ith mythtv:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/apt_0.7.6ubuntu14_i386.deb (--unpack):
 files list file for package `mythtv-themes' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/apt_0.7.6ubuntu14_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I cannot even remove or purge the mytv package causing the trouble, i just get the same errors. Any ideas anyone!

Thanks!

---

### Post by Sef on 2007-10-16
Are you using mythtv?

---

### Post by idn on 2007-10-17
Don't think so, heres the output in apt:

```

iu  mythtv                          - A personal video recorder application (cli
iBA mythtv-backend                  - A personal video recorder application (ser
p   mythtv-backend-master           - Metapackage to setup and configure a "Mast
iBA mythtv-common                   - A personal video recorder application (com
iuA mythtv-database                 - A personal video recorder application (dat
p   mythtv-doc                      - A personal video recorder application (doc
iB  mythtv-frontend                 - A personal video recorder application (cli
i   mythtv-themes                   - Additional themes for MythTV              
iBA mythtv-transcode-utils          - Utilities used for transcoding MythTV task
p   mythtvfs                        - userspace filesystem client for MythTV    
p   ubuntu-mythtv-frontend          - Metapackage to setup and configure a "Fron

```

However I cannot actually add or remove *anything* as I keep getting the empty filename error.

---

### Post by idn on 2007-10-18
sorry to bump this, but atm i cannot install or remove any software through apt :(

---

### Post by mlissner on 2007-10-26
I think the package name is a red herring. I am having the same problem, only with a totally different package...

---

