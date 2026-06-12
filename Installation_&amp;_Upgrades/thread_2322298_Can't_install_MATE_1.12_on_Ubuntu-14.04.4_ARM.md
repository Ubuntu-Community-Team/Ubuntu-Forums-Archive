---
title: "Can't install MATE 1.12 on Ubuntu-14.04.4 ARM"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by mickpf on 2016-04-27
Hi ...,

can somebody explain, why it's not possible?
I don't see this version neither in synaptic nor in aptitude!
Even it is available in ports.ubuntu.com and my repo is actual ('apt-get update').

Kind Regards,
Michael

---

### Post by RobGoss on 2016-04-27
Hello and welcome, 

Your message is not clear what are you asking for help with?

---

### Post by QLee on 2016-04-27
> **mickpf said:**
> can somebody explain, why it's not possible?
I don't see this version neither in synaptic nor in aptitude!
Even it is available in ports.ubuntu.com and my repo is actual ('apt-get update').

The repos hold installation candidates for more version than just 14.04. Here is the mate-desktop installation candidate for 14.04 from my 14.04 system. 

```
QLee@Atlas:~$ apt-cache policy mate-desktop
mate-desktop:
  Installed: (none)
  Candidate: 1.6.2-1
  Version table:
     1.6.2-1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
```

I don't have mate-desktop installed but as you can see it would pick version 1.6.2-1,.

Now, you might be able to download the one you mention and install it, but you should probably stick with letting the APT system pick the appropriate version.

---

