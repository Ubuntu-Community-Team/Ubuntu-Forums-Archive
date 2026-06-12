---
title: "dual boot 2 linux distros?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2010-06-08
So I was looking a the back track distro and it was saying that you are better off running the full distro not adding the programs to a regular ubuntu.

So that got me thinking could you have a second disto that only has it boot partition and then still use the same swap space and home folder.

heres a screen shot of my partitions

---

### Post by mikewhatever on 2010-06-08
Theoretically, yes. There shouldn't be any problems with a single swap partition, no matter how many distros you install. The home folder is a different story. From what I understand, Backtrack guys think themselves to be security geniuses, and so everything is run as root (please correct me if that's wrong). Now, if you use the same home directory for Ubuntu and Backtrack, some config files may become owned by root, and then you'll have problems with Ubuntu. The least you can do is make a backup of your home before installing Backtrack.

---

