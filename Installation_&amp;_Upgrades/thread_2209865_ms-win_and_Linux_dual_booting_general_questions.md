---
title: "ms-win and Linux dual booting general questions"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by nLpPyXR on 2014-03-07
I've been running Lubuntu 13.10 exclusively for months now, however I'm being forced to install windows again due to work-related stuff. The  timing's alright I guess since 14.04 is coming and I was planning on  formatting and building up from scratch anyway...

question is: what do I install first after wiping my HDD, Linux or windows? does it actually matter?

This is because I've read many people who have issues with Ubuntu's "OS selector" (the name of which I can't remember right now).

---

### Post by oldfred on 2014-03-07
Often better to install Windows first, Windows 7 or later uses 2 primary partitions with MBR(msdos) partitioning, not gpt with UEFI.

The real requirement is that Windows must boot from a primary NTFS formatted partition with the boot flag or active partition in Windows. Windows will not see Linux formatted partitions. If your primary NTFS is after an extended partition Windows may also not rewrite partition table correctly, again it does not see Linux partition and forgets to include it.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
You can always restore a different boot loader. But grub2 should let you boot both Ubuntu & Windows.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by nLpPyXR on 2014-03-07
thank you

---

