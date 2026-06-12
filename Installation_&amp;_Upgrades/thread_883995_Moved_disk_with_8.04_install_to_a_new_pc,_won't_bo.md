---
title: "Moved disk with 8.04 install to a new pc, won't boot"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by neander on 2008-08-08
I needed to move a 8.04 installation to another pc, and simply tried to boot the disk on the new box. The hardware is pretty different so not surprisingly it's not happy with me. There are msgs re x11 and xorg; I'm guessing video subsystem? Or are there going to be a lot of issues? If this going to be hopeless to get going again, I can reformat. There's no data to be lost, it's just the reconfig I'd like to skip.

---

### Post by mikjp on 2008-08-08
boot into recovery mode, and try 

```
dpkg-reconfigure xserver-xorg
```

greetings,

mikko

---

### Post by neander on 2008-08-08
I can't believe it worked, but it did! Thanks!

---

### Post by neander on 2009-03-28
I moved the hdd to the orig box now. Got the same x11 failure and went through the process suggested above twice. It still fails.

Any suggestions? After reconfig I've been rebooting, I'm sure that's ok? I could probably start x windows via command line but rebooting ought to be equiv?

At first it says failed to start x server. Detail is...well not sure if there is any useful info to report if I chose that option.

Oh. and while the orig post I made states 8.04, it's really installed on 7.04.

---

### Post by tommcd on 2009-03-28
> **neander said:**
> 
Oh. and while the orig post I made states 8.04, it's really installed on 7.04.

Ubuntu 7.04 is not supported anymore; and Ubuntu 7.10 will reach end of life on 4-19-09:
[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)
You would be better off using your time to install the current version, which is Ubuntu 8.10.

---

### Post by neander on 2009-03-28
I think you're right <g>

---

