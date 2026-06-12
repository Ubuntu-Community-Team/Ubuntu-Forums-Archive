---
title: "How to Uninstall Ubuntu 14.04 LTS"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by mike69 on 2015-09-03
I have Ubuntu 14.04 LTS as** the only operating system** on one of my laptops. I would like to remove it completely and install a fresh operating system (Previously had Windows XP Professional and want to reinstall it) but am having difficulty removing Ubuntu. **How can I format the hard drive when I only have the one drive? and no alternative system to boot from. **
I did boot from the Windows XP CD and it loads all the necessary files and then halts with the message that there is possibly not enough free disk space and/or the BIOS need updating. The HD size is 40Gb and 32Gb free. **Any help would be appreciated.**

---

### Post by TheFu on 2015-09-03
Boot any OS that will and run fdisk - delete all the partitions. It is common to use a CD, DVD or flash drive for this.

BTW - this is non-obvious for many people. Good question.

---

### Post by yancek on 2015-09-03
> The HD size is 40Gb and 32Gb free

You haven't posted any details but, the most likely scenario if you are getting that message is that you might have 32GB of free space but it is inside a partition or partitions.  You would need unallocated space outside a partition.  If you still have the Ubuntu installation medium you could also use GParted which is on that device to delete and/or format.

---

### Post by mike69 on 2015-09-03
Don't have any boot-able OS and the Ubuntu installation medium is nowhere to be found, I believe when I originally installed Ubuntu I downloaded it from the web. I do have the original Windows XP installation CD but cannot install it as mentioned in my original post. I believe I need someway to format it without an OS.
yancet, what additional details are you looking for that may help? as I'm open to any suggestions. Thanks

---

### Post by mike69 on 2015-09-04
After much research I was able to finally Uninstall and remove Ubuntu from the laptop and format the hard drive. When I find time I will now proceed with reinstalling Windows XP.

---

### Post by TheFu on 2015-09-04
> **mike69 said:**
> After much research I was able to finally Uninstall and remove Ubuntu from the laptop and format the hard drive. When I find time I will now proceed with reinstalling Windows XP.

You will be welcomed back when you decide that you miss Linux.

---

### Post by mike69 on 2015-09-04
> **TheFu said:**
> You will be welcomed back when you decide that you miss Linux.

Thank you for all your support.

---

