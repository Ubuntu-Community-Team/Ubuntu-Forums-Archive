---
title: "UEFI EMMC Install Problem"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by Planorez on 2021-09-15
I am working with a Acer Aspire one 1-431 notebook with a EMMC drive and EUFI, secure boot enabled.  I put Ubuntu 20.04.3 on a 16 GB flash drive using Rufus set for GPT for a EUFI system.  The install on the notebook went well and seemed normal.  The problem is that when I now boot the notebook, I get "No Bootable Device".  The EMMC drive is the first item in the bootlist.  Has anyone seen this and what is the solution?  I appreciate your help.
planorez

---

### Post by oldfred on 2021-09-15
Acer typically requires "trust" setting in UEFI settings for any UEFI boot entry other than Windows.

Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

