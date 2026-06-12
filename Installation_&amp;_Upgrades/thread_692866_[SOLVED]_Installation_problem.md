---
title: "[SOLVED] Installation problem"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by XXLFazer on 2008-02-10
I have a bit of a strange problem and hope you guys can help out here.

After I run the install from the live cd it does the check for the partitions and formats the swap file space no problem, then it says it will format the root space as ntfs.

After it does that it then says it's installing the system, but nothing happens, it just switches straight back to the Live CD desktop.

I have checked and double checked that the space I have is enough (10Mb for file system and 1Mb for swap file) but I can't figure out what is wrong and why it wont install.

Any help is appreciated, but please bear in mind I am COMPLETELY new at this Linux and don't fully understand it yet, I just want to get away from crappy windows......LOL

Thanks in anticipation

XXLFazer

---

### Post by fish2ways on 2008-02-10
If you format the root partition to ntfs then Ubuntu won't install. ntfs is a MS Windows file system. You need to set it to partition root to the ext3 file system

---

### Post by XXLFazer on 2008-02-10
OK, will try and see if I can get it to format it differently, when I first did it, I think I didn't get the choice as to which format, but I will go and check again.

Thanks

---

### Post by fish2ways on 2008-02-11
I'm a little rusty on the install process, it's a while since I did one, but you should be offered the options:
Guided 
Manual
Which option are you choosing? Are installing to dual boot with windows? Or are you installing to replace Windows?
Also, I've just noticed in your original post you say you've allotted 10Mb for root and 1Mb for Swap. Do you mean megabytes or gigabytes?
If it's megabytes then that's no where near enough space for either. You need to provide **at least** 4 gigabytes of space.

---

### Post by Chubuntip on 2008-02-12
If you are replacing your windows system on a single hard drive, it might be easiest to run "sudo gparted" from a terminal command and reformat the entire drive to a different format (just not ntfs). 

Then run the install link from the Ubuntu desktop (on live cd).

But DON'T do this if you are hoping to keep your windows up and running.

---

### Post by housam on 2008-02-12
use the Gparted tool on the live CD to format your partitions to ext3 for the (/) root and linux swap solaris for the swap. then use the manual way in asigning the partitions during the install process.

---

### Post by XXLFazer on 2008-02-19
Thanks guys, what I did wrong was to let PartitionMagic create the Partition, so it made it ntfs.

I deleted the Partition and re-created it from the Live CD and made it ext3 file system.
Managed to install no problem now.

Thanks

---

