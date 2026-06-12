---
title: "Partitioning for Windows and Linux"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by anonymous131 on 2009-12-24
Hi guys, I'm trying to get both Windows and Linux to run on my computer.

I just did a fresh install of Windows and used the dualbooting tool that came with the Ubuntu cd.

My question is:
Why can't Ubuntu see the Windows Files and vice versa?
I want to set up my computer in a way so that Ubuntu is my main OS and Windows XP is my secondary OS, and they can write to eachother. How should I partition my harddrive?

Thanks.

---

### Post by mikewhatever on 2009-12-24
There are many partitioning schemes, some of the popular ones being

Windows
/
swap

Windows
/
/home
swap

and variations.
If that doesn't tell you much, it doesn't matter. Ubuntu should have full support of NTFS (read/write) out of the box, while Windows will need [-->drivers<--]("http://www.fs-driver.org/") to support Linux file systems.
The notion of main and secondary OS is irrelevant when dual booting because both OSs are independent.

---

### Post by oldfred on 2009-12-24
I have read that even with windows it is better not to have your data in the windows partition but in a separate partition so if windows gets corrupted you can still get to your data.

The windows driver into ext3 is still in development, some say it works ok. It does not work with Karmic and ext4 partitions.

I created a separate shared partition formated as NTFS and put any data that I think I might share with windows in that partition. I have photos, and my firefox & thunderbird profiles there. Now I am in Ubuntu so much that almost all the rest of my data is in a separate ext3 data partition as I will never be in windows and want that data. So I have /-root,  swap, shared NTFS, data - ext3 and several more partitions with other systems that also can share the data partitions.

---

### Post by Mark Phelps on 2009-12-24
> **oldfred said:**
> I have read that even with windows it is better not to have your data in the windows partition but in a separate partition so if windows gets corrupted you can still get to your data.

+1!!

I have several different OSs running on my main desktop PC -- and have been using this "separate data partition" approach for some time without any problems.  This allows you to recover your data from any of the OSs, so if an MS Windows OS gets corrupted, I can still use one of the Linux OSs.

Best of both worlds -- in my view.

---

