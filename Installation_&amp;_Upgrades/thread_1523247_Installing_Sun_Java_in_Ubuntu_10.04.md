---
title: "Installing Sun Java in Ubuntu 10.04"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by boaty on 2010-07-03
Hey everyone,

For the last hour, I've been trying to install Sun's Java 6.  I've looked up everything on it, but can't find a solution that works.  I've tried sudo apt-get install java everything that I could find, but nothing worked.

As of now, I've done
```

sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"

```
and uninstalled the OpenJDK and all affiliated java with that.

So, who knows how to do this?

Thanks in advance everyone.

---

### Post by wojox on 2010-07-03
Try this [http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)

---

### Post by boaty on 2010-07-03
Thank you; it appears to be working.  If only google would display that page >,<

Edit:
Worked like a charm; now even chrome can run java applets.  Thanks a lot :D

---

### Post by wojox on 2010-07-03
Your welcome.

---

### Post by dbhatt on 2010-07-03
Hey everyone,
I tried the solution listed on the website and it worked just fine, but I wanted to install JDK 5 instead of 6. I need the code I'm writing to be JDK 5 compliant, and I tried changing the 6's to 5's in the commands on the website, but it didn't work. Any ideas on how I could get JDK 5 installed?

---

