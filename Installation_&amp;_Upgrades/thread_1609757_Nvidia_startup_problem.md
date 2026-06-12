---
title: "Nvidia startup problem"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by Experimental on 2010-10-30
I have gt9600 and I installed 10.10 brand new. I installed it with nomodeset option but I can't start ubuntu after installation. I tried adding nomodeset in edit mode but It didin't work for me. What can I do

---

### Post by Experimental on 2010-10-31
I have seen that nomodeset option is not an option anymore. Is that true ? Then what should I do now

---

### Post by P4man on 2010-10-31
You have to edit grub startup lines now. See here:
[http://ubuntuforums.org/showthread.php?p=10005672](http://ubuntuforums.org/showthread.php?p=10005672)

If you plan to install the nvidia restricted driver, you probably only need to change grub line once, then install nvidia driver and you should be okay (so you dont need to follow the instructions linked above to make it permanent).

BTW, you may want to bump this bug report by confirming it and saying it affects you too:
[https://bugs.launchpad.net/hundredpapercuts/+bug/664526](https://bugs.launchpad.net/hundredpapercuts/+bug/664526)

It describes your situation exactly.

---

