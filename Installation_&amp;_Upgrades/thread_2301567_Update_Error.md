---
title: "Update Error"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2015-11-03
First off I'm on Ubuntu 15.10 and this is the first time I've noticed this error.  I had this little red triangle looking icon up on the upper right hand corner and when i pressed on it it said Update, Open Ubuntu Software Center and various things much to the same.  So I pressed Update and it started downloading, but at the end I got the following error.  Maybe it's nothing because it happened last night and today the triangle warning icon is gone today!     Failed to fetch [http://ppa.launchpad.net/yofel/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/yofel/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/yofel/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/yofel/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by howefield on 2015-11-03
You probably have a file relating to the yofel ppa in /etc/apt/sources.list.d, remove it with something like..

```
sudo mv /etc/apt/sources.list.d/yofel-ubuntu-off-ppa-xenial.list ~/Documents
```

That command will move the file to your Documents folder in case you need it again. I'm guessing at the file name, so substitute with the file name of your file, it certainly won't have xenial in it :)

---

### Post by shane_faulkinbury2 on 2015-11-03
Thanks!  :D

---

