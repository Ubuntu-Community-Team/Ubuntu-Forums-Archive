---
title: "Newbeee. Need help"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by raj17 on 2011-06-19
Hi,
This is Raj.I'm learning how to use linux. And i'm having many doubts. And i'm not able to find clear answers through search. Please someone answer all my questions clearly. I'm listing questions below. (I'm planning to install Ubuntu linux)

1. I know that windows file system is NTFS. What is Linux File system. (ext3 ?) or are there any linux file systems? can windows read linux file system and can linux read windows file system?
2. I'm planning to install ubuntu alongside my windows. As far as i know for linux file system should be ext3. But in Ubuntu site I went through installation instructions. he has given nothing about changing the file system of drive where linux would be installed to ext3. So can i directly install ubuntu on NTFS? or does it automatically change format from ntfs to ext3? or is it only for ubuntu that it can get installed on ntfs. and all other flavours of linux require ext3 file system. even if ubuntu can get installed on ntfs is it good to install it on ext3 file system or will it create any problems. pleae explaiin clearly. even if i have not asked something let me know.
3.Can linux read flash drives or external hard drives directly or is it compulsory to install ntfs drivers for it. how do i do it.

These are some questions i could think of before installation. pleae reply

---

### Post by sanderd17 on 2011-06-20
> **raj17 said:**
> Hi,
This is Raj.I'm learning how to use linux. And i'm having many doubts. And i'm not able to find clear answers through search. Please someone answer all my questions clearly. I'm listing questions below. (I'm planning to install Ubuntu linux)

1. I know that windows file system is NTFS. What is Linux File system. (ext3 ?) or are there any linux file systems? can windows read linux file system and can linux read windows file system?

Linux has many file systems, but the most used is currently ext4. I have read that you can install an ext4 reader module in Windows, but it seems to be unstable. Linux has no problem with reading from NTFS, but the NTFS doesn't support features Linux needs to operate. So all internal Linux files and all configuration files can't be on NTFS.
> 
2. I'm planning to install ubuntu alongside my windows. As far as i know for linux file system should be ext3. But in Ubuntu site I went through installation instructions. he has given nothing about changing the file system of drive where linux would be installed to ext3. So can i directly install ubuntu on NTFS? or does it automatically change format from ntfs to ext3? or is it only for ubuntu that it can get installed on ntfs. and all other flavours of linux require ext3 file system. even if ubuntu can get installed on ntfs is it good to install it on ext3 file system or will it create any problems. pleae explaiin clearly. even if i have not asked something let me know.

When you install Ubuntu, you will be given some options:
[LIST]
[*]Use entire disk: erase windows and partition everything as ext4
[*]next to your current OS: shrink windows NTFS and make a new ext4 partition
[*]Manually: do it your self: shrink or delete partitions, create new ones ... (only advised if you have done partitioning before)
[/LIST]
> 
3.Can linux read flash drives or external hard drives directly or is it compulsory to install ntfs drivers for it. how do i do it.

These are some questions i could think of before installation. pleae reply

Linux can read a lot of file systems. It only has problems with some filesystems that are used by Apple. The drivers for NTFS and FAT32 are included in the kernel.

As a final note: most desktop Linux systems offer about the same functionality for different filesystems. But there are Linux variants (like Android, Meego, WebOS ...) that aren't build for computers and don't offer that support. As a result, you can't say "all Linux".

---

### Post by raj17 on 2011-06-20
Thank U very much for replying. I'll install and ask further questions if i'm having any problems. thank u once again.

---

