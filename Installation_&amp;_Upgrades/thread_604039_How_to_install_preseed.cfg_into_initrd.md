---
title: "How to install preseed.cfg into initrd"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by avalder on 2007-11-05
My goal is to create an automatic install CD.  I plan to install a preseed.cfg file on the iso image that I will burn.  So far I have found no documentation that explains how to install the preseed.cfg into the initrd.  My assumption is that I need to create a temporary directory, cd to this directory, then do
a gunzip -c /boot/initrd.img | cpio -i -d -H newc --no-absolute-filenames.
Next copy my preseed.cfg file into this directory and then do:
find . -depth | cpio -H newc -o | gzip -c > new_initrd.img 
And then cp new_initrd.img to the root of my iso directory and then
mkisofs on that directory.
Am I headed down the correct path or do I have to do anything else?

---

