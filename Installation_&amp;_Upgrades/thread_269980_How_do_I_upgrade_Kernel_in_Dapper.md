---
title: "How do I upgrade Kernel in Dapper"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by Monkus on 2006-10-02
Hi,
I would like to upgrade my kernel to 2.6.17. I am trying to get my Palm Pilot to sync. I thought I could use the Edgy CD to upgrade, but when I put it in and set it as a repository, all is shows is 2.6.15. Am I missing something? Any help would be greatly appreciated. Thanks.

---

### Post by Rui Pais on 2006-10-02
hi,
why you just dont don't get the debs from the cd or from [here]("http://packages.ubuntu.com/edgy/base/linux-generic"), and install with:
```
sudo dpkg -i linux-generic*.deb
```

linux-generic is the name for the kernel (2.6.17) on Edgy. 
For 686... the 386 stills named as linux-386)

---

### Post by Monkus on 2006-10-02
Hey thanks. I'll try that.

---

