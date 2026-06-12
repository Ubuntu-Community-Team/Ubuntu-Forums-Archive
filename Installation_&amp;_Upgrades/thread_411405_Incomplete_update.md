---
title: "Incomplete update"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by blamecanada on 2007-04-16
I was installing some updates when the machine locked up, and I had to reboot. Now when I run update-manager i get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and the hung installation is:

linux-image-2.6.20-15-386

It says I need to reinstall, but obviously this has to be done through the command line, what should I type to do this? I've been looking through the dpkg manual and can't come to any conclusions.

---

### Post by computerease on 2007-04-16
Similar issue to yours:  [http://www.linuxquestions.org/questions/showthread.php?t=361965](http://www.linuxquestions.org/questions/showthread.php?t=361965)

---

### Post by blamecanada on 2007-04-16
My /var/lib/dpkg/updates is empty.

---

### Post by NeoLithium on 2007-04-16
Have you tried to do as it asked, and run:
```

sudo dpkg --configure -a

```

When I have a few incidents and shut down during an upgrade it fixes my stuff all right up.

---

### Post by blamecanada on 2007-04-16
> **NeoLithium said:**
> Have you tried to do as it asked, and run:
```

sudo dpkg --configure -a

```

When I have a few incidents and shut down during an upgrade it fixes my stuff all right up.

I get this when I enter that:

dpkg: error processing linux-image-2.6.20-15-386 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 linux-image-2.6.20-15-386

Any ideas?

---

### Post by NeoLithium on 2007-04-16
Try
```

sudo aptitude reinstall linux-image-2.6.20-15-386

```
And see if that helps.

---

### Post by blamecanada on 2007-04-17
Ok it seems the problem was there was a batch of 7 updates, and 2 of them were for the update manager itself.  Apperently it always tried to install those first, which it couldn't do w/ a hung installation, so I just unchecked those 2, installed the Linux Images again, and then those would install.

---

