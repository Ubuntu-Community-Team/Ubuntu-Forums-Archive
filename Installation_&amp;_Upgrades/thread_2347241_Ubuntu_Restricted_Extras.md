---
title: "Ubuntu Restricted Extras"
date: 2016-12-22
forum: Installation &amp; Upgrades
---

### Post by newbieuser2 on 2016-12-22
Brand new to Ubuntu. I was downloading "ubuntu restricted extras" when the computer froze. I restarted the computer while frozen. Once restarted, my software center says it's installed, but when I try to open it or remove it, it gives the below warning:

The Package System is Broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:  The following packages have unmet dependencies:

libavcodec-extra: Depends: libavcodec-extra-54 but it is not installed


I'm brand new to this, but don't know how to fix it, since I can't even remove it without getting the same message. Your help is much appreciated.

---

### Post by ian-weisser on 2016-12-22
> **newbieuser2 said:**
> ...
Furthermore run the following command in a Terminal: apt-get install -f
...


Did you try the system's suggestion of how to fix the problem?

---

### Post by newbieuser2 on 2016-12-22
Great idea... and it worked. Im not used to this whole terminal thing. Where are some good resources to learn the lingo? And Thank You for the help! it works now!

---

