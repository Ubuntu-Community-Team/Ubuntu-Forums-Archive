---
title: "&quot;no init found&quot; after installation on SSD"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by deshd on 2016-08-30
I've installed Xubuntu  from USB onto a clean (outdated) system, which I just intend to use for emailing and web browsing. 

Installation worked well, but deletion of not required packages took some time. If I boot from internal SSD I get the following messages (see also screenshot): "No init found. Try passing init = bootarg."A little bit earlier it says "/dev/sda1: clean ..." but some lines later "mount: mounting /dev/sda1 on root failed Invalid argument" etc. 

First thing I did, was to check the SSD, the filesystem, partition etc.. Everything as expected, but no chance to boot. Booted again from USB (no issues) and installed anew. Same behaviour as before. I'm suspecting some timeouts in accessing the SSD or some hw driver issues.

I'm gratefull for every hint

P.S.: BIOS sees and recognises the SDD (see second screenshot)

.[ATTACH=CONFIG]270936[/ATTACH][ATTACH=CONFIG]270937[/ATTACH]

---

