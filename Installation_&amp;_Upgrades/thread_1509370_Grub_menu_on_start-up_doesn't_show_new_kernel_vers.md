---
title: "Grub menu on start-up doesn't show new kernel versions"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by bzzzwa on 2010-06-14
Hello,
I have newer kernel images installed on a server but they are not shown in grub menu on start-up. But these new kernel images are present at **menu.lst**.
I have proceeded **update-grub** many times, but no change.

So I can't boot to newer kernel nor remove 2.6.24-24 version.

My issue is similar to [http://ubuntuforums.org/showthread.php?t=1425998](http://ubuntuforums.org/showthread.php?t=1425998) , but it is not grub2 issue there I gues.

$ lsb_release -a
LSB Version:    core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:core-3.2-ia32:core-4.0-ia32:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

$ uname -a
Linux irserver 2.6.24-24-server #1 SMP Fri Sep 18 17:24:10 UTC 2009 i686 GNU/Linux

I have attached results from script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thank you
Petr

---

