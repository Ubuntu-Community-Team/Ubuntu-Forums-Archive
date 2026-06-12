---
title: "Unable to update after power failure"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by hariprs on 2008-06-04
Hi,

Today i received some updates. Update download went smooth, Unfortunately the power went off during the installation of the update. After reboot i tried to continue the installation but i received the below error.

Error
```
E: /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_amd64.deb: files list file for package `linux-libc-dev' contains empty filename
```


I though this could have happen due to corrupted download files. So i cleared the dir /var/cache/apt/archives/ and tried again but no use. Please help me.

---

### Post by hariprs on 2008-06-04
I managed to solved it by doing the following

```

sudo rm /var/lib/dpkg/info/linux-libc-dev.list
sudo rm /var/lib/dpkg/info/linux-libc-dev.md5sums
sudo dpkg --configure -a
sudo rm /var/lib/dpkg/info/vala-awn-trunk.list
sudo rm /var/lib/dpkg/info/vala-awn-trunk.md5sums
```

---

