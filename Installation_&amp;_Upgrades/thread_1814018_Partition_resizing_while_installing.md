---
title: "Partition resizing while installing"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by frogbrains on 2011-07-28
I'm installing 11.04 on a friend's laptop.  I'm fairly familiar with Ubuntu, and I'm sure when I've install it previously it didn't takr this long to resize the partition.  It's been going for around 15 minutes.  The loading cursor is still spinning, and the HDD activity light is on almost solidly, but it's been a long time with no updates.  The log says only "ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!".  Nothing appears to be happening.  Is this normal?

EDIT: Never mind, it failed.

---

### Post by jerrrys on 2011-07-28
its depends on the size of the resize as to how long it takes.  sometimes its just 15 minutes and on a big move it can be several hours.

some people say that you should only resize windows with a window partition manager, but i have not had a problem with gparted and ntfs.  the only exception to this is windows vista.  gparted will not play well with gparted and you will likely bork your vista install.

and if your thinking of putting ubuntu (or any linux distro) on ntfs, this will not work well. NTFS doesn't handle file permissions as required by Linux.  NTFS is a consideration, but it is proprietary and Window's peculiar  usage of these drives means that Linux doesn't quite work perfectly with  it. Further, Microsoft has the capability (and sometimes does) remotely  lock NTFS folders. Do you want to take that chance?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by ingeva on 2011-07-28
> **jerrrys said:**
> its depends on the size of the resize as to how long it takes.  sometimes its just 15 minutes and on a big move it can be several hours.
[]("http://www.dedoimedo.com/computers/gparted.html#mozTocId335513")I would leave the resizing procedure of NTFS partitions to Windows (Vista and later) because I don't trust the Linux partition manager to do it 100% correctly. If you do that, at least do a a Disk check under Windows afterwards.
Disk size changes DO take a long time. I usually copy the whole file system to another disk, delete the partition and create a new one, and then restore. Most times that's faster and safer.

---

### Post by Blasphemist on 2011-07-28
It is active. DO NOT STOP IT!

Since the hdd is staying active it is just still running. Do not stop it or you have a big risk in corruption.

---

### Post by Blasphemist on 2011-07-28
Windows does a very poor job of defragging and resizing its own partition(s). The Ubuntu installation will do a good job of it. When the installation finishes, you will need to boot windows twice. The first will run a chkdsk because of the resize operation. It will finish just fine. Then reboot and run windows again just to set your mind at ease. Resizing the partition takes longer for disks that are large and for those that are fragmented. Just sit back and have a drink. :D

---

### Post by Quackers on 2011-07-29
Resizing Windows XP partitions seems to go well with gparted.
Resizing Vista or Win 7 partitions with gparted can go horribly wrong!
In my experience it is much safer to defrag the partition and then use Windows Disk Management screen to resize Windows partitions. The actual resize operation is wuicker too :-)

"Windows for Windows partitions - Linux for Linux partitions" is a good maxim, methinks.

---

### Post by mastablasta on 2011-07-29
> **Quackers said:**
> In my experience it is much safer to defrag the partition and then use Windows Disk Management screen to resize Windows partitions. .
 
2 times defrag and then run chkdsk to be sure everythign is OK.
 
perhaps you didnt' defrag partition before attempting to resize it?

---

### Post by jerrrys on 2011-07-29
> **mastablasta said:**
> 2 times defrag and then run chkdsk to be sure everythign is OK.
 
perhaps you didnt' defrag partition before attempting to resize it?

good call, if you dont defrag first (do it twice) that can add a lot more time to the resize process.

---

