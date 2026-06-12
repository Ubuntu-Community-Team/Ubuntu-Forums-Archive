---
title: "Just deleted my /etc/modules"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by robertobech on 2005-04-14
I just made something really stupid: deleted my /etc/modules. In fact, I copied another file on top of modules. I've installed the system yesterday but have already upgraded somethings... so how can I recover my /etc/modules to the original state of an ubuntu hoary installation?

Thanks...

---

### Post by alastair on 2005-04-14
This is what I have - I think it is pristine and might be ~OK for you :

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
 
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```

---

### Post by Dracontopes on 2005-04-14
And here is mine if that may help...

```

# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

sd_mod
sr_mod
psmouse
mousedev
amd74xx
ide-core
ide-cd
ide-disk
ide-generic
sbp2
lp
fglrx

```

---

### Post by farnsworth on 2005-04-14
Just don't add fglrx or amd74xx unless you need them.  fglrx is for ATI graphics cards, and I assume amd74xx is AMD processor support (Dracontopes: does this give a noticable performance boost?)

---

### Post by robertobech on 2005-04-14
Thanks everybody for your help. In fact, I just booted ubuntu from the live CD and copied it's modules file, I guess I now have it as it was before. Thanks again...

---

