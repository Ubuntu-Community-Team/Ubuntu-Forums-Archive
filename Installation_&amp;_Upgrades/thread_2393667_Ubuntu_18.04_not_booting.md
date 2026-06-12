---
title: "Ubuntu 18.04 not booting"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by oo0hnoo0 on 2018-06-06
Hello all,

I attempted to erase my hard disk, and install Ubuntu 18.04 from 16.04
However once the installation is complete, it does not boot. And my BIOS does not exist.

I attempted to do a boot-repair.
Here's the log.

paste.ubuntu.com/p/kssTRQMpJf/

Sorry if this message sounds incoherent I haven't got much sleep last night.

---

### Post by Autodave on 2018-06-06
BIOS will exist with no HD present, so it sounds like a hardware problem.  Is this laptop or desktop?  Make and model?

---

### Post by ajgreeny on 2018-06-06
You appear to have only a single disk showing, sda, which has a single partition on its 29.8GB? available space which is probably a 32GB USB drive used to install the system.
Maybe you have a live system but no full installation on a hard disk of the OS as you expected.

What hardware do you have and what exactly did you do when you tried to install the OS?
Do you have another hard disk than that 32GB one that is showing?
Does you machine use UEFI or legacy BIOS?

---

