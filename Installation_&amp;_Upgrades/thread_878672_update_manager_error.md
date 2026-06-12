---
title: "update manager error"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by burb16 on 2008-08-03
hi
Been trying to update hardy heron and it cannot download all files and is not able to install the files which it can download I get the following errors

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

can anyone help with this please
bob

---

### Post by coffeecat on 2008-08-03
> **burb16 said:**
> E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.

I've never seen this error before, but it looks as though your root partition is full, or with so little space that the downloaded files cannot be cached. Go to System > Administration > System Monitor. Now click on the File Systems tab. Look for the device where the directory is '/' - probably the first on the list. What do the total, free, available, used and % columns say?

If you're more than about 90% full, you've got a problem. One way to make some room would be to run 'sudo apt-get clean' from a terminal. This would clear out all the previously downloaded packages from the cache. If you've installed many applications and kept your system up to date, that could be a sizeable chunk of re-usable space.

---

### Post by burb16 on 2008-08-05
thanks for that checked it out and the partition is full. I am running linux on the same drive as vista is there a way of taking disk space of vista without upsetting the applecart ?

cheers...bob




> **coffeecat said:**
> I've never seen this error before, but it looks as though your root partition is full, or with so little space that the downloaded files cannot be cached. Go to System > Administration > System Monitor. Now click on the File Systems tab. Look for the device where the directory is '/' - probably the first on the list. What do the total, free, available, used and % columns say?

If you're more than about 90% full, you've got a problem. One way to make some room would be to run 'sudo apt-get clean' from a terminal. This would clear out all the previously downloaded packages from the cache. If you've installed many applications and kept your system up to date, that could be a sizeable chunk of re-usable space.

---

### Post by coffeecat on 2008-08-05
First thing - did you try clearing out the package cache?

Second - you need to post details of your partitions and their sizes before anyone can give good advice. You could open a terminal and post the output of:

```
sudo fdisk -l
``` (That's lower-case L, not one.) But that's user-unfriendly when you want the sizes in gigabytes. So give the partition sizes listed in System Monitor as well when you next post. Post both.

> **burb16 said:**
>  is there a way of taking disk space of vista without upsetting the applecart ?

Theoretically yes, but with caveats. I've no experience of Vista myself, but I've read that it has a drive C: resizing tool which is safer than shrinking the NTFS partition with Gparted in Ubuntu. But having done that, the free space may not be contiguous with your Ubuntu root partition - the swap partition may be in between. And even if it was, I've never been able to resize ext3 partitions (your Ubuntu root). In fact it may be that it's not recommended. So what you might have to do is make another partition with the freed space, move some stuff there (perhaps /home) and link it across. But I can't say anything definite until seeing the output of fdisk and the partition sizes.

---

