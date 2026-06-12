---
title: "Local &quot;mirror&quot; problems"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by davmaz on 2007-06-26
Hi - I've downloaded a complete copy of an Ubuntu mirror to a USB2.0 drive. I can mount it (/media/disk) and it has the ubuntu/dists/feisty/main/binary-i386/Packages.gz and a corresponding ubuntu/pool/main/etc directories (it's got EVERYTHING!)...

However, I can't use apt-get because I can't find a way to enter this information into the /etc/apt/sources.list file in the "correct" way (so it goes to the USB drive RATHER than an http site). I don't have the machine connected to the Internet -- the reason I'm need a 'local' mirror.

Is there a straightforward way to configure my system so that it will find and install the packages I want?
Thanks!

---

### Post by olejorgen on 2007-06-27
Add this to sources.list (I think entries have decreasing priority (?))
```

deb file:/media/disk/<path to mirror>/ubuntu/ feisty main

```
You might want to arrange for a permanent mount point for the disk. (If you have multiple partitions, race conditions can cause partion 1 to be mounted on disk or disk-1)

---

### Post by davmaz on 2007-06-28
Hey - Thanks. I'm not able to try it in the next couple days, but I will next week. I can't believe it's that easy (and not documented somewhere)!  I know I tried deb file:**//**media/disk/ububntu ... but that didn't work -- it must have been the // that tripped it up.

---

### Post by olejorgen on 2007-06-28
Actually it is :P
```

man sources.list

```

but it should be an option for adding a local repository in the "sources gui"

---

