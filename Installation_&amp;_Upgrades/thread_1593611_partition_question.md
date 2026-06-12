---
title: "partition question"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by binarylife on 2010-10-11
Hi ,
Can I delete the ext and swap partitions from disk management on windows 7 ? Because I want to install a fresh new copy of ubuntu 10.10 . I know it would affect windows 7 boot up. I can handle it by system restore . Anyway can I do it or not ? 
Thanks a lot


[[IMG]http://img508.imageshack.us/img508/5571/50791591.jpg[/IMG]](http://img508.imageshack.us/i/50791591.jpg/)

---

### Post by gyussz on 2010-10-11
> **binarylife said:**
> Hi ,
Can I delete the ext and swap partitions from disk management on windows 7 ? Because I want to install a fresh new copy of ubuntu 10.10 . I know it would affect windows 7 boot up. I can handle it by system restore . Anyway can I do it or not ? 
Thanks a lot

You can... but If I were you, I wouldn't do that. I suggest you to do the formatting/partitioning job with your Ubuntu installation media manually. The result will be a fresh installation of Ubuntu on your ext4 partition, without messing up the Boot managers.

---

### Post by ronparent on 2010-10-11
The quick answer is no - you currently show more than four primary partition and an install would fail. Win 7 apparently lets you create more than four primary partitions. Also I don't believe it will let you create an extended partition. 

To install you would be best to use gparted from the live cd to create an extended partition out of your two last primary partitions. You would then be free to create the linux partitions you need (target for install and swap, or, as many as you want). Linux partition managers do not currently support creating more than four primary partitions. Post if you need more help.

---

### Post by binarylife on 2010-10-11
I've used gparted and deleted these partitions and installed it .: ) Thanks

---

### Post by binarylife on 2010-10-11
I can't install wireless drivers !! 
Broadcom B43 wireless driver
Broadcom STA wireless driver

error msg:
SystemError: installArchives() failed!! 
help please ?

---

### Post by srs5694 on 2010-10-11
> **ronparent said:**
> The quick answer is no - you currently show more than four primary partition and an install would fail. Win 7 apparently lets you create more than four primary partitions. Also I don't believe it will let you create an extended partition. 

Windows *cannot* allow you to create more than four primary partitions, at least not on an MBR disk, since the data structures to support more than four primary partitions on the disk simply do not exist. It would be like trying to fit more than 1 liter of water in a container with precisely 1 liter of volume. I have a vague recollection that recent versions of Windows label all partitions as being "primary," even when they're logical, but I can't check that myself because my Windows Vista install has stopped booting. :( It's also not clear to me that the 17.84GB and 840MB areas are actually partitions -- as I recall, the Windows disk management tool makes it hard to distinguish partitions from free space. Another possibility is that this is a GPT disk; however, that's only likely if the computer uses EFI or UEFI instead of a BIOS, since Windows won't boot from a GPT disk on a BIOS-based computer.

As I recall, there *is* an option to create an extended partition in the Windows disk manager; however, since my Vista installation won't boot, I can't give specific instructions on how to find it.

---

