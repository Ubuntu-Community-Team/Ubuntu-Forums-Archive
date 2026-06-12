---
title: "Ubuntu Install detecting wrong windows installation drive for automatic install"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by Royi on 2014-06-04
On my PC I have 4 drives, one of which is the one I'm currently booting off of and is a 120gb SSD with windows 8 on it. Unfortunately, when I try to do the Ubuntu Side by side install, it is detecting one of my other drives, which was a windows 7 boot drive in its former life in a former PC. I can go the "something else" route and pick the 120g SSD, but then I don't really know what I'm doing. I do see 4 partitions on it (sdba I think), one of which is the 119gb current boot partition, with 40gb used (windows 8 startup disk). Should I select that partition, resize it to 75gb (or something) and then... what. It looks like as soon as I resize the partition it does it and there is no going back so I want to make sure I know what I'm doing if I do press OK. 

Or is there any way to get the ubuntu install to recognize the 120gb SSD and not the old windows 7 drive from the other PC?

Thanks in advance!

---

### Post by Mark Phelps on 2014-06-05
First of all, do NOT resize any Windows OS partitions using the Ubuntu installer or GParted.  This risks corrupting the Windows filesystem and if that happens, Windows will then be unbootable to run repairs.  Use only the Windows Disk Management utility to shrink Windows OS partitions.

Second, the best approach, when you have multiple drives, in my experience, has been to have ONLY the target drive connected when you want to install a new OS. That prevents accidental damage to other drives from the install process.

---

### Post by Royi on 2014-06-05
Thanks! I wasn't really worried about losing the windows partition. It's windows 8 and it sucks and if it dies I won't be upset, been meaning to downgrade to win7 anyways. Either way, I'll disconnect the extra drives and just leave the SSD in there and install in the free space on it leftover by using the windows disk management to make the existing windows partition smaller.

---

### Post by erind on 2014-06-05
Just FYI - when you install ubuntu (depending how you will partition your SSD drive) use "Something Else" option during the install. There are reports that the ubuntu installer wipes out the other partitions when using other options, see this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So as suggested, it's very critical that all the extra drives are disconnected during the install.

---

