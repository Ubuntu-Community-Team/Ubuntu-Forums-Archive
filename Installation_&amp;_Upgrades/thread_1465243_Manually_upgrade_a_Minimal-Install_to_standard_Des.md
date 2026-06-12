---
title: "Manually upgrade a Minimal-Install to standard Desktop"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by chappajar on 2010-04-29
Due to some CD burning/reading problems with the laptop I'm installing to, the only install disk that I have been able to get to work is a MinimalCD disk.

Unfortunately this only works if I don't ask it to install any extras at all, so I can install Ubuntu, but it is bare bones, and boots to a shell, no GUI or anything like that.

What packages do I need to apt-get to bring this minimal install up to the standard Ubuntu install?  Does anyone have a list of packages, or a site that will tell me which packages to install?

---

### Post by snowpine on 2010-04-29
One package:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by chappajar on 2010-04-29
Wow, really, that's it? 

So after that it will be indistinguishable from an install from a normal LiveCD?

---

### Post by snowpine on 2010-04-29
> **chappajar said:**
> Wow, really, that's it? 

So after that it will be indistinguishable from an install from a normal LiveCD?

Correct. For more info: [http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)

---

### Post by chappajar on 2010-04-29
> **snowpine said:**
> Correct. For more info: [http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)

Thanks snowpine.  I assume all those dependencies will be installed, but what about all the ''recommended'' packages?

I'm guessing they WON'T be installed?  Can I force them to be installed when I install ubuntu-desktop?

---

### Post by snowpine on 2010-04-29
> **chappajar said:**
> Thanks snowpine.  I assume all those dependencies will be installed, but what about all the ''recommended'' packages?

I'm guessing they WON'T be installed?  Can I force them to be installed when I install ubuntu-desktop?

I'm guessing they will :) give a try and write back if it doesn't work.

---

### Post by chappajar on 2010-04-29
> **snowpine said:**
> I'm guessing they will :) give a try and write back if it doesn't work.

Cheers snowpine!  Everything's looking great so far.

---

