---
title: "updating, kernel errors ?"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by weasel fierce on 2006-03-01
When trying to run apt-get upgrade on the wife's laptop, I get this

"WARNING: Module /lib/modules/2.6.12-10-386/kernel/drivers/video/aty/radeonfb.ko is not an elf object
There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 11
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.12-10-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot."

There's a LONG list of the "is not an elf object" errors, in front of this.

What gives and what can I do to fix it ?

---

### Post by stryderjzw on 2006-06-16
I have the same error.  :(

---

