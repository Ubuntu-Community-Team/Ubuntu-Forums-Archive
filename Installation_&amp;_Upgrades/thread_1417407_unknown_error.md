---
title: "unknown error"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by mcbelisle on 2010-02-27
everytime I restart my system there is some error that comes up and it's too fast to see it. is there a command to allow me to see that error

---

### Post by s.fox on 2010-02-27
Hello,

Open up a terminal and run this command to view the boot log.

```
dmesg
```

I would also add that logs can be found in this directory:

```
/var/log
```

Hope this helps,

-Silver Fox

---

### Post by mcbelisle on 2010-02-27
ok. i did that and this is that error:

 mmc0: Unknown controller version (2). You may experience problems
Registered led device: mmc0::
[   12.078152] mmc0: SDHCI controller on PCI [0000:01:04.2] using DMA

just did search. i guess it's a known problem and there is no fix for it

---

### Post by s.fox on 2010-02-27
> **mcbelisle said:**
> ok. i did that and this is that error:

 mmc0: Unknown controller version (2). You may experience problems
Registered led device: mmc0::
[   12.078152] mmc0: SDHCI controller on PCI [0000:01:04.2] using DMA

just did search. i guess it's a known problem and there is no fix for it

Hello,

I am glad you were able to get the error message from the log.

[This]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159/comments/13") post suggests that the card reader may be fully functional despite the error message.  Is this true for you?

-Silver Fox

---

### Post by n0dix on 2010-02-27
What is your Ubuntu version?
The last post in this [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159"), said that the Ubuntu 9.10 fix the problem.

---

### Post by mcbelisle on 2010-02-27
yeah it works just the error shows up

---

### Post by n0dix on 2010-02-27
Ignore ;)

---

