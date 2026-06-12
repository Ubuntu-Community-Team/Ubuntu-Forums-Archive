---
title: "ubuntu 10.04 manual partition: free space is unusable"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by Usagi_ on 2011-09-21
Hi,
I'm totally new to this stuff and I'm trying to install Ubuntu 10.04 on my pc and dual boot with windows 7.
I used the disk management tool to shrink volumes and create some space, but when I try to install ubuntu I don't have the option to install it side by side with windows, so I have to choose the manual one, but there it says that my free space is unusable. 
I think that it's because I already have 4 partitions on my pc, but I'm totally new to this kind of stuff and I don't know what I should do now.
I attached a screenshot of my disc managment and one of the partitions while installing ubuntu.
thank you very much for your help

---

### Post by Elfy on 2011-09-21
That is beacuse you have 4 primary partitions already. 

You'll need to lose on eof the primaries and create an extended.

Perhpas backup one of the smaller partitions - delete it after you've got a backup.

Then create an extended in the new free space - then you can create logicals - one for the data previously backed up ans then you'll be able to install ubuntu in logicals.

You need backups anyway - partition editing is safe - but things happen just when you're not expecting it.

---

### Post by Usagi_ on 2011-09-21
which one can I delete?

---

### Post by Elfy on 2011-09-21
I have no idea what you have on your partitions? 

You need to make that decision.

---

### Post by srs5694 on 2011-09-21
Although deleting one of the partitions, as forestpiskie suggests, is the traditional way to do this, it's unclear to me that it's safe to delete any of those partitions. Fortunately, there is another option: You can convert /dev/sda4 into a logical partition, which will then enable you to create additional Linux partitions as logical partitions in the free space. (You may need to explicitly resize the new extended partition to make this work, though.)

One way to do this is to use my FixParts tool, which is available on several platforms. (You can download the Windows version [using this link.](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/fixparts-windows-0.8.0.zip/download)) See the [FixParts documentation](http://www.rodsbooks.com/fixparts/) for details on how to use it. There's a good chance that some Windows-only tools can do the job, too, but if so I don't know which ones. You should *not* use the standard disk partitioner in Windows itself to further manipulate your partition table, though; it might convert your system to use a "dynamic disks" configuration, which will just be digging a deeper hole for yourself.

As always when dealing with partitioning, you should be sure you've got good backups before proceeding further. Although most partitioning tools are fairly reliable, sometimes bad things can happen and can result in damage to your partition table, which can translate into loss of all your data, particularly if you err in your recovery attempts.

---

### Post by Usagi_ on 2011-09-21
I did like forestpiskie said and now I finally have ubuntu installed :) thank you

---

