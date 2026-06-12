---
title: "My computer has both SSD and HDD. How should I create partitions to install ubuntu 20"
date: 2021-01-16
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-01-16
I have 256GB SSD and 1TB HDD. Now I want to use SSD for every purpose by default(i.e. /home should be in SSD) but I also want to use HDD for storing some large files manually . I mean it will be good if I can just cut files from SSD and then move it to HDD directly. Please provide step-by-step guide because I have little knowledge on these topics.
Please note that I have no problem if I have more than one /home directories(if possible), I just want to use SSD as well as HDD for storing files and I don't want to limit the size of home directory in SSD.

---

### Post by ActionParsnip on 2021-01-16
You could make a /data folder then mount the file system to this folder. Users can then have a symlink to /data in $HOME for easy access. Just install Ubuntu to the SSD as normal. If you use the "something else" option (and the large storage isn't using NTFS) then you can add it to the system at install time. Just set it to not be formatted

---

### Post by mikewhatever on 2021-01-16
There is no need to do anything special. The HDD, if formatted, should be visible in the file browser, you should be able to click it to access, and copy/paste files. No step by step guide is needed for this not very unique setup.

---

### Post by EngineerStrange on 2021-01-16
What format is needed for the HDD and do I need to do it before installation or after installing?

---

### Post by oldfred on 2021-01-16
You can do either, if not installing into the HDD.
I prefer to use gparted. 
But cannot use gparted on mounted partitions, so normally used from live installer, or when installing, before or after install.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

But I do install gparted and use it on other drives, just cannot use it on my installed drive. It is not installed by default in your install.

I also like to have another install on my data drives, more for emergency use. I only install some typical repair tools, and not all the extra applications I install in my full install, so just need a smaller partition. And I often use it to test some change I may want to make to my configuration, but do not want issue of trying to undo in my main working install, if I do not like it. 

Details on using a data partition and linking folders in data partition back into /home, so it looks & acts like data in /home, but really is really in another partition.
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Everyone's partitioning requirements are different, so only you will know what you want or need.
Just for reference, this is my partitioning. I recently upgraded my M.2 SATA drive to NVMe and moved M.2 SATA into an external case. And with larger SSD, now moved data partition to SSD, so HDD is mostly test installs & backup. Still have unallocated space on both drives. Swap was there from one of my old installs. I have to say not to use it on new installs and may not be using it on anything still installed & will soon delete it.
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)

---

