---
title: "Partitioning HD while Intalling Ubuntu"
date: 2019-09-04
forum: Installation &amp; Upgrades
---

### Post by genieinthebox on 2019-09-04
Hello, 

I am a beginner when it comes to technology. So I might need some help from the experts on here. I recently received a computer without a HD. I purchased a new one, and now am in the process of installing Ubuntu Linux onto my hard drive. In the installation process, a box came up entitled "Installation Type." The options are 1)"Erase disk and install Ubuntu" 2) Encrypt the new Ubuntu installation for security" 3) "Use LVM with the new Ubuntu installation" and 4) "Something Else." 

I would like to make it so that I can put another OS on if I want to. What are the steps taken, including choosing one of the above options, to make that happen? 

Thanks....

---

### Post by TheFu on 2019-09-04
If the other OS is Windows, you'll need to install that first.

---

### Post by oldfred on 2019-09-04
If planning on dual booting, best to partition in advance and then use Something Else. You can partition during install also, but only with Something Else.
Default install will just create one large / (root) partition which you may not want. If UEFI, it will also create an ESP - efi system partition. 

If planning on "other" system as Windows best to install it first.

Also important if system is UEFI or BIOS. And then you must install all systems in same UEFI or BIOS boot mode. Systems install in boot mode that you use to boot install media, USB flash drive, which can be different than default boot mode of system. So settings also important.

If newer UEFI system, lots more info in link below. Some also applies to older BIOS systems.

---

