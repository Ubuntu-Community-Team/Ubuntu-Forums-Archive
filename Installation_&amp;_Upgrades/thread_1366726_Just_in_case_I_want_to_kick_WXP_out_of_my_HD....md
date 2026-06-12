---
title: "Just in case I want to kick WXP out of my HD..."
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2009-12-28
I have plenty of info ("My Documents") in WXP (however it fits in my Ubuntu file system). I have backed it up in a DVD (just copied the folders and files with Nero).

My HD is a 80GB, 50 for WXP, 20GB for Ubuntu and the rest es available free disk space.

In case I want Ubuntu to be the only OS, which are the steps to follow? Is it there any chance of re-partitioning Ubuntu?

Do I have to install Ubuntu from zero without partitioning the HD, and restoring the data from the CD, copying the files to my /home/robert/documents/ folder ?

---

### Post by ugm6hr on 2009-12-28
Lots of options:

My suggestion is to just reformat the WXP partition as ext3 and use as data; you can then create a shortcut from Ubuntu's home folder to the new partition.

If / when you upgrade to the next Ubuntu (i.e. 10.04), you can then do a fresh install with that partition as a separate /home.

---

### Post by rva1945 on 2009-12-28
> **ugm6hr said:**
> Lots of options:

My suggestion is to just reformat the WXP partition as ext3 and use as data; you can then create a shortcut from Ubuntu's home folder to the new partition.

If / when you upgrade to the next Ubuntu (i.e. 10.04), you can then do a fresh install with that partition as a separate /home.

"...reformat the WXP partition as ext3..."

HOW TO? From Windows?

---

### Post by VastOne on 2009-12-28
> **rva1945 said:**
> "...reformat the WXP partition as ext3..."

HOW TO? From Windows?

Using gParted

If you have not already loaded it you can get it via Synaptic

---

### Post by rva1945 on 2009-12-28
> **ugm6hr said:**
> Lots of options:

My suggestion is to just reformat the WXP partition as ext3 and use as data; you can then create a shortcut from Ubuntu's home folder to the new partition.

If / when you upgrade to the next Ubuntu (i.e. 10.04), you can then do a fresh install with that partition as a separate /home.


How do I create a shortcut to my current WXP My Documents folder? By right-clicking I can just create Folders or Documents.

---

### Post by ugm6hr on 2009-12-29
> **rva1945 said:**
> How do I create a shortcut to my current WXP My Documents folder? By right-clicking I can just create Folders or Documents.

I realise you are just exploring options, but you need to decide what you want to do and ask for advice to do that.

Creating shortcuts to NTFS / vfat (i.e. WXP partitions) directories does not work very well; you can create a shortcut to the C: drive, but not to My Documennts as far as I remember (sorry - haven't used WXP for a while).

If you reformat (with GParted or using cfdisk / fdisk commands) to ext3, then you can create a shortcut to any directory within the partition.

---

