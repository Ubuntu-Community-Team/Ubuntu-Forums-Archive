---
title: "can't install pkg-config on hirsute"
date: 2022-12-29
forum: Installation &amp; Upgrades
---

### Post by itaysk on 2022-12-29
```

&#10095; sudo apt install pkg-config              
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  pkg-config
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
Need to get 46.2 kB of archives.
After this operation, 195 kB of additional disk space will be used.
Err:1 http://archive.ubuntu.com/ubuntu hirsute/main amd64 pkg-config amd64 0.29.2-1ubuntu1
  404  Not Found [IP: 185.125.190.36 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.29.2-1ubuntu1_amd64.deb  404  Not Found [IP: 185.125.190.36 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

&#10095; sudo apt install pkg-config --fix-missing
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  pkg-config
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
Need to get 46.2 kB of archives.
After this operation, 195 kB of additional disk space will be used.
Err:1 http://archive.ubuntu.com/ubuntu hirsute/main amd64 pkg-config amd64 0.29.2-1ubuntu1
  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.29.2-1ubuntu1_amd64.deb  404  Not Found [IP: 185.125.190.39 80]
E: Internal Error, ordering was unable to handle the media swap


```


I noticed the following exists at the server "http://archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/pkg-config_0.29.2-1ubuntu3_amd64.deb"
I don't know what it means but probably will help troubleshoot. The installer requests "ubuntu1" but what's available is "1ubuntu3".

```

&#10095; uname -a                                 
Linux ubuntu-hirsute 5.11.0-49-generic #55-Ubuntu SMP Wed Jan 12 17:36:34 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by tea for one on 2022-12-29
Hirsute Hippo (Ubuntu 21.04) reached End of Life in January 2022.
Any reason not to download and install Ubuntu 22.04 LTS?

---

### Post by Holger_Gehrke on 2022-12-29
'Hirsute' ? That's 21.04, which should have gone out of support at the beginning of 2022 (non-LTS releases get 9 months IIRC). So if you look in "http://archive.ubuntu.com/ubuntu/pool/main/p/pkg-config/" you'll find the package "pkg-config_0.29.2-1ubuntu3_amd64.deb" isn't there anymore. I'd say it's time for a do-release-upgrade, but 21.10 is out of support too by now, so you'd be trying to upgrade from one out-of-support release to another to get to a still supported release (22.04 is an  LTS, but you can't just go straight to that from 21.04).

Holger

---

### Post by itaysk on 2022-12-30
Got it. I wasn't aware packages are removed for older versions. I will upgrade then. Thanks

---

