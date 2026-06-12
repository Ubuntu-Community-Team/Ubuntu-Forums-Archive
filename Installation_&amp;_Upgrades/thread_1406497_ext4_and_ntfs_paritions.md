---
title: "ext4 and ntfs paritions"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by lilyamma on 2010-02-14
I just installed ubuntu to a partition on my external hd (using ext4 file system) and am trying to format the other partition on that same drive using ntfs so that I can still access it from windows. (I have a windows installation on my internal hd)

I've tried to format it using a few different programs in ubuntu but keep getting this error message:  

> error creating file system: helper exited with exit code 1: cannot spawn 'mkntfs -f -L "Storage" /dev/sdb3': Failed to execute child process "mkntfs" (No such file or directory)I've also tried to format the partition from windows (vista), but when I start up vista and plug in the drive neither of the partitions (the one with the linux install and the other which is currently just unallocated disc space) show up..

Is it possible to have ext4 and ntfs on different partitions within the same drive?  I remember reading that in order to have windows and linux installed on one drive windows has to be installed first...perhaps this is also the case with ntfs and ext4 file systems? In which case I would have to wipe my linux, format the ntfs, and then reinstall it all :(

Thanks for any and all help!

---

### Post by TitanusEramius on 2010-02-14
One possible solution is that your Ubuntu is missing the tools it's need to write NTFS on a disk. You can install mkntfs through Synaptic in System>Administration, when it opens you have to give your password, and then do a search for "mkntfs". 

There will only be one result, install it by marking it and press "apply" and then try to format the disk again :)

---

### Post by presence1960 on 2010-02-14
install ntfsprogs. Either from System > Administration > Synaptic Package Manager or from a terminal run ```
sudo apt-get install ntfsprogs
```
That is a complete set of tools for NTFS and includes mkntfs.

You do not need to install windows first, that is a fallacy perpetuated by uninformed but well meaning people.

---

### Post by lilyamma on 2010-02-14
Ah awesome that did it, thanks guys

---

### Post by lilyamma on 2010-02-14
hmm nevermind. I was able to format it as ntfs and everything was fine, but then once i unmounted the drive it went back to being unknown/unrecognized in my disk manager and wouldn't let me mount it again.  Doesn't show up in windows either.  Unfortunately this was after i copied all of my data back onto it :(  nothing too crucial was lost at least...I'm guessing the data is still there but somehow it seems to have lost its file system (I don't really know how this all works so that might not make sense).  I could try formatting it again but I'm guessing it will just be to the same effect, and the HD itself should be fine because it also contains the partition i'm running linux from, which is working fine.

I'm not sure if this really counts as an ubuntu issue anymore, but if you guys have any ideas they would be much appreciated.

---

