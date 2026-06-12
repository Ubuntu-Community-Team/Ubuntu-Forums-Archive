---
title: "How to clean up GRUB menu after updates?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2010-01-07
After I updated my system, grub shows about 2 extra options on the boot menu. They seem to be different kernel versions. How do I clean up the menu and uninstall the older kernel versions?

---

### Post by kansasnoob on 2010-01-07
Please post the output from terminal of:

```
grub-install -v
```

That will tell us what version of grub you have as the process is different for 0.97 and 1.97.

---

### Post by mahela007 on 2010-01-07
grub-install (GNU GRUB 1.97~beta4)

---

### Post by drs305 on 2010-01-07
You can remove older kernels from your system via synaptic. Search for "linux-image-2.6.31-....." I'd keep at least one older kernel you know works at least for a while.  Removing them via synaptic will remove them from your menu as well. You can also remove the same version of "linux-headers-..."

You can hide the recovery mode by removing the comment # in front of this line in /etc/default/grub (or making the value "true" if you previously made it "false". Think twice about this unless you know how to get to the recovery mode by editing the normal entry.
> 
GRUB_DISABLE_LINUX_RECOVERY="true"


If you remove the kernels via synaptic, it will automatically run "update-grub".

If you make changes to /etc/default/grub, run this command afterward to update the menu:
```
sudo update-grub
```

If you really want to tweak you menu, you can create a custom menu (40_custom is in /etc/grub.d/) or tweak the menu. For the latter, see the link in my signature line about G2 Title Tweaks. Caution geek alert if you go look.

---

### Post by mahela007 on 2010-01-08
thanks for the great post... 
umm.. what are linux headers?

---

### Post by drs305 on 2010-01-08
> **mahela007 said:**
> thanks for the great post... 
umm.. what are linux headers?

In short: The header files define structures and constants that are needed for building most standard programs. The header files are also needed for rebuilding the kernel.

But I'm not a computer science major.

---

### Post by mahela007 on 2010-01-09
thanks.

---

