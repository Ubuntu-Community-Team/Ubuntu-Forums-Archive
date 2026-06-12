---
title: "install or boot disk issues!!"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by curtsw5 on 2008-04-29
my friend downloaded ubuntu 8.04 onto his microsoft windows IBM thinkpad and burned the bootable version to a disk. I am trying to install this on my suse linux based dell without success. whats wrong?

---

### Post by iaculallad on 2008-04-29
Could you give us at least details on your installation. What problem are you encountering: Did the CD/DVD boot up after restart? Did you reach the installation menu?

---

### Post by curtsw5 on 2008-04-29
good questions. the cdr failed to boot entirely. when i turned on my machine, went to f12 to choose boot options, chose cd/dvd/cdrw option, hit enter, with cdr already inserted and a grub loader message appears very briefly at which time the suse system overrides ( i guess ) the boot option

---

### Post by iaculallad on 2008-04-29
> **curtsw5 said:**
> good questions. the cdr failed to boot entirely. when i turned on my machine, went to f12 to choose boot options, chose cd/dvd/cdrw option, hit enter, with cdr already inserted and a grub loader message appears very briefly at which time the suse system overrides ( i guess ) the boot option


Check the downloaded ISO's integrity and compare it with its valid MD5 hash.

md5 xxxxxx-8.04-kubuntu.iso

You might have burned a corrupted ISO.

---

