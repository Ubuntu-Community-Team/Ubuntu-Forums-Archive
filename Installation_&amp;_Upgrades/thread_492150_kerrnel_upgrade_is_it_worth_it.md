---
title: "kerrnel upgrade is it worth it?"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by snkiz on 2007-07-04
hi all i notice in the package manager there is a i686 kernnel, it says use "for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV."  I have a p3 so should I get this? will it help? and how do I install it?? thx

---

### Post by snkiz on 2007-07-04
anybody??:-\"

---

### Post by az on 2007-07-04
The linux-686 and linux-image-686 packages are obsolete.

If you look at the contents of the package, they point to the generic kernel image.

It used to be that the kernel was compiled with different optimisations for certain hardware.  Those options are now run-time options on the generic kernel.  When you run the generic kernel, whatever optimisations are available for your processor are used.

---

### Post by snkiz on 2007-07-04
thanks for saving me alot of headake Ive already messed up my install twice expermenting I do not want to go through that again. why don't they remove the package if its obsolete??

---

### Post by az on 2007-07-04
> **snkiz said:**
> thanks for saving me alot of headake Ive already messed up my install twice expermenting I do not want to go through that again. why don't they remove the package if its obsolete??

Because some people will have installed it when they were running an older version of Ubuntu and if there is not a newer version of that package, they will not get the new kernel installed (it will keep the latest version of the old kernel).  It's there for legacy purposes.

---

