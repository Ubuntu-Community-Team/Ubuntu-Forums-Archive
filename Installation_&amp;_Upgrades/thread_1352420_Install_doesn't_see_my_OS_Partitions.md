---
title: "Install doesn't see my OS Partitions"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by PoopyTheJ on 2009-12-11
I'm trying to install Ubuntu 9.10 as a clean install overwriting my old Ubuntu install. I have three physical drives in the computer, with 4 partitions. On my primary drive sda I have two partitions a 230GB windows partition in the first position and a  GB Ext4 partition running Ubuntu 9.04. I have two other drives a 640GB drive and a 1TB drive for media files. When trying to install through the installer I get this mesage when the partitioner starts up, "This computer has no operating systems on it." The partitioner sees sdb and sdc but doesn't see sda. I can't overwrite my previous install if the partitioner can't find it! I've tried running e2fsck on the missing partition but no go. Any advise or help? Would be greatly appreciated!

---

### Post by darkod on 2009-12-11
If you are NOT running raid, boot with the 9.10 cd, select Try Ubuntu and in terminal execute:
sudo apt-get remove dmraid

That should sort it out.

---

### Post by PoopyTheJ on 2009-12-11
hmm installer still doesn't see my partition, I'll reboot and try again. btw I can open and brose the files on the missing partitions, in the installer missing I mean, just fine. If I open up gparted it see's those partitions just fine as well.

---

### Post by darkod on 2009-12-11
Yes, I think you need to reboot. For this description, that's usually the cure.

---

### Post by PoopyTheJ on 2009-12-11
That does seem to have sorted it out. Thanks!

---

### Post by PoopyTheJ on 2009-12-11
Can you give me a rough idea of why that happened? And why dmraid is installed or operating, what is it doing and why is it causing the issue?

---

### Post by darkod on 2009-12-11
> **PoopyTheJ said:**
> Can you give me a rough idea of why that happened? And why dmraid is installed or operating, what is it doing and why is it causing the issue?

I haven't investigated too much, but my personal explanation is: at some point the drive might have been used for raid setup, and traces of the settings remain. Maybe even before you bought it. Up to 9.04 it seems that doesn't matter but 9.10 seem to detect them and it confuses the hell out of it. :)
With that command you are removing those traces. Maybe I'm wrong about all of this. :)

---

