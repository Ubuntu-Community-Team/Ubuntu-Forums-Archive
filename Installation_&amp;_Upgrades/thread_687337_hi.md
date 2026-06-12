---
title: "hi"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by omlx2 on 2008-02-04
hi ..
when i try to update ubuntu7.4 ...it show me this msg
[http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

---

### Post by zvacet on 2008-02-04
```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn´ work 

```
cat /etc/apt/sources.list
```

and post it here.

---

### Post by omlx2 on 2008-02-18
i tried to update but nothing happen and i got
99% [6 Packages gzip 0] [Waiting for headers]                          60B/s 0s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
  Sub-process gzip returned an error code (1)
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages [1307kB]               
99% [7 Packages gzip 0]                                                60B/s 0s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
  Sub-process gzip returned an error code (1)
Fetched 102kB in 10s (10.1kB/s)                                                
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pumalite on 2008-02-18
Check your connection. Wired to the internet is best. Remember to comment out all third parties in your sources.list.
You could try this after all of the above:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

Change Servers just in case.

---

### Post by omlx2 on 2008-02-18
i did the upgrade and when i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

but when i run that code i got:
requested operation requires superuser privilege

---

### Post by omlx2 on 2008-02-18
i did the upgrade and when i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

but when i run that code i got:
requested operation requires superuser privilege

---

### Post by Pumalite on 2008-02-18
sudo dpkg --configure -a

---

