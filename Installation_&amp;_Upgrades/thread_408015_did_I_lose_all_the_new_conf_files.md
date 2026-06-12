---
title: "did I lose all the new conf files?"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by manifoldronin on 2007-04-12
I did an online upgrade from Edgy to Feisty beta last night. Mostly went smooth - except one issue:

During the upgrade, I would be asked whether to keep or replace certain configuration files, and I had always chosen "keep", in hoping that update manager would keep the current file as is, _and_ save the new version under a different file name, because I wanted to do the merge afterwards. But after it's done and I booted back up, I can't find any of the dpkg_new files?  Did I misunderstand what "keep" means and the update manager didn't actually save any of the new files?  Or am I missing something obvious?

Thanks in advance for any hint.
-- 
manifoldronin

---

### Post by zvacet on 2007-04-13
You told that you want to keep your conf. files and that is the reason that you don´t see new one.

---

### Post by manifoldronin on 2007-04-13
> **zvacet said:**
> You told that you want to keep your conf. files and that is the reason that you don´t see new one.

Thanks.  But that doesn't make much sense, does it?  If "keep" keeps the existing version *only*, and "replace" replaces it, when do you get a chance to merge them?

I come from Fedora/yum. Whenever I run a yum update, it saves the conflicting conf files with names ending in .rpm.new. I thought that was what "keep" would do.

---

