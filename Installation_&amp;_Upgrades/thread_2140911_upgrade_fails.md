---
title: "upgrade fails"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Huikermaster on 2013-05-01
I recently installed 12.10 (desktop edition) on a machine that I will probably use as a small home server (I know, I could have gone for the server edition, but I may want to use it as a desktop at some point).

When I log in to it via ssh, I get the message 

> 
New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.


When I type this command I get the message (sorry for the first sentence in Dutch, but it just states that it checks whether there is a new version available).
> 
Er wordt gecontroleerd of er een nieuwe Ubuntu-uitgave is
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 145, in <module>
    fetcher.run_options += ["--mode=%s" % options.mode,
AttributeError: type object 'DistUpgradeFetcherCore' has no attribute 'run_options'


Is there a way to solve this issue?

---

### Post by plucky on 2013-05-01
> I recently installed 12.10 (desktop edition) on a machine that I will probably use as a small home server (I know, I could have gone for the server edition, but I may want to use it as a desktop at some point).


Have you run ```
sudo apt-get update && sudo apt-get dist-upgrade
``` as yet?

You have to install updates since 12.10 was released before you can do a distribution upgrade to 13.04.

Good Luck

---

### Post by Huikermaster on 2013-05-01
Thank you very much!!!
 (:oops:, should have realised that myself)

---

### Post by Huikermaster on 2013-05-02
So now I get the folllowing message when I log in:

```

Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.

```

That seems to suggest that the upgraded succeeded but that the version number string is not present in all config files. Any easy way to sort this one out?

---

