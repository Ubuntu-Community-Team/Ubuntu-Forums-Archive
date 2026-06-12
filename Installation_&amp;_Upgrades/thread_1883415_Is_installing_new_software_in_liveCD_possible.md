---
title: "Is installing new software in liveCD possible?"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by rahggupt on 2011-11-19
I am using ubuntu liveCD. I want to use a software which is needed to be installed.  Is it possible to use the software without actually installing the ubuntu .

---

### Post by BillyBoa on 2011-11-19
The application you need is called Reconstructor

```
sudo apt-get install reconstructor
```

You can create your own Live CD based on Ubuntu.

---

### Post by davetv on 2011-11-19
apt-get will work fine in a live CD environment. I think Billy misunderstood the question.

---

### Post by raja.genupula on 2011-11-19
> **rahggupt said:**
> I am using ubuntu liveCD. I want to use a software which is needed to be installed.  Is it possible to use the software without actually installing the ubuntu .

+1 
I have one thing , create a live usb with persistence 
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

from this you can carry your Ubuntu any where in the Pen drive.

---

### Post by sanderd17 on 2011-11-19
Installing from a live CD is possible, as long as it fits in your RAM. A live CD will never touch your Hard Disk (unless you really ask for it), so everything it downloads will need to be in your RAM. That also means it will be gone when you reboot.

+1 for the Live USB with persistence.

---

### Post by BillyBoa on 2011-11-19
> **davetv said:**
> apt-get will work fine in a live CD environment. I think Billy misunderstood the question.

Thank you so much for your remark dear friend. You are surprisingly polite.

---

