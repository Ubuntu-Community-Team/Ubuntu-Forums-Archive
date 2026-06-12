---
title: "Size mismatch erro"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by xxsmarty on 2011-11-29
When i try to install updates from update managerin ubuntu 11.10 it says :
Failed to download package files
Check internet connection
```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb Size mismatch



```

What is this Size mismatch error ! Please help!!

And when i typed sudo apt-get upgrade in terminal
 it says:
```

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-core_3.4.4-0ubuntu1_i386.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.15.901-1ubuntu2.1_i386.deb  Size mismatch


```


Please give the solution to the problem.

---

### Post by Hakunka-Matata on 2011-11-29
Have you tried this?


```

sudo apt-get install -f
sudo apt-get update --fix-missing

```

---

