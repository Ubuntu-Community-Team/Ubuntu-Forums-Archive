---
title: "can not upgrade from 9.10 (kernel 2.6.32.22) to 10.04"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by timonner on 2010-06-04
Hello to all!
I can not upgrade from 9.10 (kernel 2.6.32.22) to 10.04, may be because my kernel is from distrib 10.04?
I don't know which log should to post here. When I'm trying to upgrade, Update Manager says, that I can to update only part of software

---

### Post by dino99 on 2010-06-04
Press ALT+F2, a dialog will pop up. Type:

gksudo "update-manager -c"

---

### Post by timonner on 2010-06-04
to [dino99]("http://ubuntuforums.org/member.php?u=129712"): thanks for your answer, but after execute this command I received the same result: update manager says, that I can update only part of software, because there are problems. After that I choosed "to update part of software", updater reading cache, building tree of packages, and it doing this few minutes (long time, earlier this process was faster). After that I received thios message: 
An unresolvable problem occurred while calculating the upgrade
 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

---

### Post by kansasnoob on 2010-06-04
Was that kernel installed using a PPA?

I don't know about the kernel teams PPA's but Xorg Edgers fresh-crack has to be purged and reverted to Karmic official packages before upgrading to Lucid.

---

### Post by timonner on 2010-06-04
Sorry, but I don't know how to revert to Karmic official packages. Can you help me?

---

### Post by kansasnoob on 2010-06-04
> **timonner said:**
> Sorry, but I don't know how to revert to Karmic official packages. Can you help me?

How did you install the newer kernel?

---

### Post by timonner on 2010-06-06
I downloaded it from official site of Ubuntu in .deb package, after that did double click on file. Ubuntu automatically installed new kernel. Name of file, which was installed was something like "linux-image-2.6.32.22-generic" or "linux-kernel-2.6.32.22-generic".

---

### Post by timonner on 2010-06-09
Hey, people! Can you help me?

---

