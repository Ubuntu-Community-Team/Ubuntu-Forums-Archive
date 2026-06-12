---
title: "Ubuntu Install Getting More Difficult NOT Easier"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Qboy61 on 2010-10-23
I am trying to install 10.10 on a 60GB area of my hard drive that is unpartitioned. WinXP is in the other partition. I've downloaded 10.10 32-bit desktop and burned a Live CD. The Live CD has been tested for errors. I'm installing 10.10 and the partition manager gives me the choice of 1) Install Ubuntu to Entire Disk (this would destroy WinXP) and 2) Manual Partition. 
 
???? Where is the selection for install to largest unused area of the disk??? 
 
I've been installing Ubuntu since 7.10 to the largest unused area and it never touched the Windows partition. Now we have to manually set the partitions??? UBUNTU 10.10 IS GETTING HARDER, IF NOT IMPOSSIBLE TO INSTALL. The garbage with boot graphics on 10.04 and 10.10 is also a failure. The other day I watched my daughter's Dell620 boot Ubuntu 9.10 with a beatiful smooth boot screen which elegantly fades to the desktop after login (really looked polished). MR. SHUTTLEWORTH WHAT HAS HAPPENED IN THE LAST YEAR? :(:(:( :mad::mad::mad:

---

### Post by perspectoff on 2010-10-23
> **Qboy61 said:**
> 
 
???? Where is the selection for install to largest unused area of the disk??? 
 


Do you actually have any unused area on your disk? Because if you don't, you know, there won't be an option to use it...

---

### Post by jfinner1 on 2010-10-23
I had the same issue when I had a pre-existing WinXP partition. For some reason, when Windows partitioned the drive, it left the unused space as partitioned space, not free space. My advice, go with the manual partition editor install. It's not hard, and there should be plenty of guides for how much space to use.

---

### Post by Mark Phelps on 2010-10-24
Sigh ... it's NOT a Windows XP problem -- despite the eagerness of folks on this forum to blame every installation problem on XP, Vista, or Seven.

Canonical DID make it much harder to install to free space than it was on previous versions, so hard in fact, that we're seeing thread after thread from folks who THOUGHT they were making the right selection, but ended up wiping out their MS Windows installation in the process.

After you have selected the Install alongside ..., you will then get an option to choose to use the entire disk.  Do NOT select that.  Instead, go into manual partitioning, select the free space, and partition that.

If you're concerned about losing your MS Windows install, and you have an external drive or somewhere else you can save it, Google for Macrium Reflect, go to their website, download their free version, install it in MS Windows, and launch it to make an image backup of your MS Windows install.  Also, use the option to create a boot disk.  You will need both the backup and boot disk if your MS Windows install get trashed.

---

### Post by coffeecat on 2010-10-24
> **Mark Phelps said:**
> If you're concerned about losing your MS Windows install, and you have an external drive or somewhere else you can save it, Google for Macrium Reflect, go to their website, download their free version, install it in MS Windows, and launch it to make an image backup of your MS Windows install.  Also, use the option to create a boot disk.  You will need both the backup and boot disk if your MS Windows install get trashed.

+1

@Qboy61, this is excellent advice.

---

### Post by A_T on 2010-10-24
The installer has regressed since Lucid. Now unless you know what you're doing with the advanced partitioner you have to use the simple option which does not tell you what you are doing to your hard disc.

---

### Post by Qboy61 on 2010-11-11
I'm glad to see that some of you agree.  I didn't mean to rant but I'm dissapointed that Ubuntu (that was making great strides in competing with Windows) has now made it so difficult to install 10.10 and these switches in the graphics/sound structure (that might be better someday) have made the system seem amateur at boot up and shutdown.  I know these are silly details but fit and finish makes a system look professional.  Everyone loves Macs because of attention to detail.  :-k
 
I hope they add the partitioning steps back in for Ubuntu 11.04.  I also hope that we can stop resorting to terminal entry sessions for all the tweaks required when trying to install odd things in Ubuntu.  Ubuntu needs to try to do everything (as much as possible) graphically.  It's friendlier for computer persons who are switching from Windows and not especially versed in command line entry.
 
I've helped many friends (some are challenged in their computer experience) get involved with Ubuntu over the last several years.  I certainly would not have gotten them interested with the installation nightmares of Maverick Meercat.

---

