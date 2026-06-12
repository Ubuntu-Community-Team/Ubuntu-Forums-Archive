---
title: "GRUB2 and Kernel Update (thru update manager)"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by CONCORAN on 2009-12-07
When software update manager updates kernel from one small sub version to the next, is there a way for it to automatically use the newer kernel when it boots next time?
So far, everytime there is a new kernel, I update GRUB2 files manually and update-grub to use new kernel.

---

### Post by presence1960 on 2009-12-07
> **CONCORAN said:**
> When software update manager updates kernel from one small sub version to the next, is there a way for it to automatically use the newer kernel when it boots next time?
So far, everytime there is a new kernel, I update GRUB2 files manually and update-grub to use new kernel.

during the update did you get a message asking if you want to use the package maintainer's version or the one installed? Always choose the package maintainer's version.

---

### Post by CONCORAN on 2009-12-07
If I recall correctly, it asked me only once if I wanted to use package maintainers' version or mine. I chose package maintainers'. But after that it hasn't.
Is there a way to turn that switch on, if I've somehow switched it off?

---

### Post by outerspacerace on 2009-12-07
[http://ubuntuforums.org/showthread.php?p=8459578#post8459578](http://ubuntuforums.org/showthread.php?p=8459578#post8459578)

Sorry to hijack but I've just experienced a similar problem and would also like to know what I can do to use the package maintainers version.

Am thinking that might help me out.

---

### Post by presence1960 on 2009-12-07
> **CONCORAN said:**
> If I recall correctly, it asked me only once if I wanted to use package maintainers' version or mine. I chose package maintainers'. But after that it hasn't.
Is there a way to turn that switch on, if I've somehow switched it off?

It should only ask you each time you upgrade a kernel.

---

