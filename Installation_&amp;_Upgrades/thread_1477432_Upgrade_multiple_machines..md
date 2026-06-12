---
title: "Upgrade multiple machines."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by EliotB on 2010-05-08
I have several machines here running 8.04 and wanted to avoid more than one 2GB download to update to 10.04.  

I used a very simple one-off solution: manual copy of /var/cache/apt/

[LIST]
[*]On the upgraded machine, copy the entire /var/cache/apt/ to a portable drive
[*]On the machine to be upgraded, first make sure current distro is up to date
[*]Replace /var/cache/apt/ with the one from the portable drive
[*]Start upgrade as usual
[*]Profit! (2 minutes of download instead of 2 hours)
[/LIST]
(This locked thread is high on google search for the 'Ubuntu upgrade  multiple machines": [http://ubuntuforums.org/showthread.php?t=581597](http://ubuntuforums.org/showthread.php?t=581597))

There are a number of post/articles about setting up apt-cacher, apt-proxy, or sharing /var/cache/apt via NFS, however these are harder to setup up, and I suspect more prone to breakage.

---

