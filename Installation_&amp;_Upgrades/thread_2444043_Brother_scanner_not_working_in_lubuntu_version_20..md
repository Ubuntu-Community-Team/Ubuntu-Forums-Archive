---
title: "Brother scanner not working in lubuntu version 20.04"
date: 2020-05-23
forum: Installation &amp; Upgrades
---

### Post by mhalfadl on 2020-05-23
Hi every one , 

I tried install lubuntu 20.04 very good performance but I found one issue with my Brother Scanner installation which it did not work in version 20.04 but it works in version 19.10 (without any change or install any script) . 

Can some one help me to solve the issue ???

---

### Post by Irihapeti on 2020-05-23
I have a Brother printer/scanner I was able to get to work in Xubuntu 20.04 by using the command
```

sudo ln -sfr /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane

```

That was in addition to installing the scanner driver and udev rule package from the Brother site.

Ref: [https://ubuntuforums.org/showthread.php?t=2439839](https://ubuntuforums.org/showthread.php?t=2439839)

---

