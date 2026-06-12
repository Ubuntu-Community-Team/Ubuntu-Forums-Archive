---
title: "Installing Ubuntu on a drive with 2 Win XP installations"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by nottyn on 2008-08-18
I am having some difficulty with my installation of Ubuntu so any help will be greatly appreciated.

Here is my setup…   I have an 80 GB drive that has two partitions that have Windows XP on each.  Windows XP crashed so bad that I did a new installation of Windows XP on the other partition.  

The second partition crashed.  So now, I want to install Ubuntu on one partition and have it the only operating system.  In other words, no dual boot need be configured.

The only thing I wish to do with the other partition is try to retrieve some files off it.  Then, I do not care what happens to my Windows XP.  
I have no desire to have Windows XP as a second Operating System to dual boot ever again.  Both these partitions are NTFS.

So if I format (erase) one of the partitions and do a complete Ubuntu install on that one partition, (which will be about 35 GB and I would also allocate a swap and /home thing on it) how should I mount the other partition so that Ubuntu will be able to see and retrieve a few files from it?

Also, what would be the best file format to run Ubuntu? If I erase the partition, is the “ext3 the best choice?

Sorry about the length of this post.  I am just trying to be more comprehensible. 

Thanks.

Nancy

---

### Post by tfosorcim on 2008-08-18
Ubuntu should detect the NTFS partition automatically and put in "Places". If not you will need to uses the Mount command. The best file system to use is a matter of opinion it seems. I use ext3.

---

### Post by nottyn on 2008-08-18
> **tfosorcim said:**
> Ubuntu should detect the NTFS partition automatically and put in "Places". If not you will need to uses the Mount command. The best file system to use is a matter of opinion it seems. I use ext3.
-------------------------------------

Thank you for your help.... 
Is it possible to do an installation of Ubuntu on the one partition and mount the other partition later?

Nancy

---

