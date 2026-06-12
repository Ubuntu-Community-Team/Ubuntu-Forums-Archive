---
title: "[SOLVED] new installation, mount /home to existing ntfs partition"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by qwertymodo on 2008-10-23
I'm installing a fresh copy of Ubuntu Hardy onto a dual-boot configuration and I have an ext3 partition set up ready to install, but I would like to mount my /home directory to an existing ntfs partition (I had windows installed first, it's my largest partition).  However, when I select that partition in the installer, I can't select a folder to mount unless I first select a file system (presumably in order to format the partition), which ntfs is not on the list.  I have had Ubuntu installed previously and tried several tutorials on moving the directory after installing, but it resulted in breaking my installation where I couldn't even log in so now here I am reinstalling from scratch.  Don't worry I only had it installed for like a week, so not like I lost anything...

---

### Post by Elfy on 2008-10-23
Pretty sure that you won't be able to use ntfs for /home - there's nothing to stop you using seperate partitions for your data

You can once you've finished the install mount the ntfs partition in ubuntu at boot and use the drive for data.

---

### Post by qwertymodo on 2008-10-23
Not the answer I was hoping for, but thanks.

---

