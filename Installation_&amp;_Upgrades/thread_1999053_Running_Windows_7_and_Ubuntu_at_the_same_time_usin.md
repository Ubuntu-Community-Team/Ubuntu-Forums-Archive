---
title: "Running Windows 7 and Ubuntu at the same time using Wubi?"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by vcrewchief on 2012-06-07
I'm installing Linux for the first time, with Ubuntu Unleashed as my guide, and they recommend using Wubi if my main OS is Windows, but I'd like to be able to run them both--one on each screen. I've done this with MacOS and Windows, but I partitioned and used a VM. Should I partition and use Microsoft VM or is there a way to make this work using Wubi?

---

### Post by wilee-nilee on 2012-06-07
> **vcrewchief said:**
> I'm installing Linux for the first time, with Ubuntu Unleashed as my guide, and they recommend using Wubi if my main OS is Windows, but I'd like to be able to run them both--one on each screen. I've done this with MacOS and Windows, but I partitioned and used a VM. Should I partition and use Microsoft VM or is there a way to make this work using Wubi?

You need a virtual then, if you want both running.

Try virtuabox from the Oracle website.

---

### Post by vcrewchief on 2012-06-07
> **wilee-nilee said:**
> You need a virtual then, if you want both running.

Try virtuabox from the Oracle website.

Thanks for the help!

---

### Post by mparillo on 2012-06-07
> **wilee-nilee said:**
> You need a virtual then, if you want both running.

Try virtuabox from the Oracle website.

I would also try VMWare Player. For me (also on Win7), after installing VMWare Tools, I found the fonts, mouse, and panel re-sizing, just seemed better on VMWare Player than Oracle VM VirtualBox.

---

### Post by vcrewchief on 2012-06-08
Virtualbox is awesome. Thanks for the help guys. Here's a little [Ubuntu on virtualbox tutorial]("http://www.psychocats.net/ubuntu/virtualbox") for anybody that might stumble on this thread:

---

### Post by vcrewchief on 2012-06-08
> **vcrewchief said:**
> Virtualbox is awesome. Thanks for the help guys. Here's a little [Ubuntu on virtualbox tutorial]("http://www.psychocats.net/ubuntu/virtualbox") for anybody that might stumble on this thread:

Also, when using virtualbox, there's no need to partition ahead of time. It just creates a giant file and calls it a drive.

---

