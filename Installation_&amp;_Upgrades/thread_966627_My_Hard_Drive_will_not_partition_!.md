---
title: "My Hard Drive will not partition !"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by exaviorn on 2008-11-01
I simply cannot resize my windows XP partition; I tried the installer and then tried Gparted (installed on ubuntu) However every time I would get an error message (availiable underneath). Earlier that day I deleted my install of Mandriva (so I could upgrade to ubuntu); I then resized my xp partition over the free space created ( I dont know If that helped with my problem)

My current PC Partition setup:
Xp and Win 2000

The Error file is attached :

Thanks 
Exaviorn :)

---

### Post by exaviorn on 2008-11-01
I think it is something to do with my hard drive, I have found the part of the log which went wrong:

real resize  00:01:16    ( ERROR )
    	
ntfsresize -P --force --force /dev/sda1 -s 29849508863
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 512 bytes
Current volume size: 58983450624 bytes (58984 MB)
Current device size: 58983450624 bytes (58984 MB)
New volume size : 29849508352 bytes (29850 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 16950 MB (28.7%)
Collecting resizing constraints ...
Needed relocations : 4365 (3 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR(5): Failed to read from the disk: Input/output error
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************

However how do I set up bad sectors on gparted??

---

### Post by esmailgad on 2008-11-01
> **exaviorn said:**
> I think it is something to do with my hard drive, I have found the part of the log which went wrong:

real resize  00:01:16    ( ERROR )
    	
ntfsresize -P --force --force /dev/sda1 -s 29849508863
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 512 bytes
Current volume size: 58983450624 bytes (58984 MB)
Current device size: 58983450624 bytes (58984 MB)
New volume size : 29849508352 bytes (29850 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 16950 MB (28.7%)
Collecting resizing constraints ...
Needed relocations : 4365 (3 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR(5): Failed to read from the disk: Input/output error
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************

However how do I set up bad sectors on gparted??
Hi
I belive you have to :
1-detect the integrity of your hard disk for bad sectors. under dos command type chkdsk/f to detect and fixe the errors.
2-under windows and under the system menu use the partition option in the storage devices
I hope it will work or return back to me for other trials

---

### Post by exaviorn on 2008-11-01
I have ran chkdsk a couple of times : it rebooted and ran  the boot check.

However I am confused about your second piece of advice :could you tell me where to access the settings you mentioned:confused:

Thanks
Exaviorn

---

### Post by exaviorn on 2008-11-02
What I do not understand is how my pc is still working after two days gparted warned me about the bad sectors, realy my computer should be having major problems.....

---

### Post by Pumalite on 2008-11-02
Try Gparted Live CD. Also if you want to shrink XP; defrag several times, turn PageFile to '0' and then use Gparted Live CD. If you want to test your drive you could use TestDisk in rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by exaviorn on 2008-11-03
Thank you for your advice, but If I change my pagefile (virtual memory) to 0 My PC will run slower :confused:

---

### Post by Pumalite on 2008-11-03
You can change it to it's origional value later.

---

### Post by haylun98 on 2008-11-03
Since you have XP, try Easeus Partition in Windows, its free for personal use:
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Make sure your backup your data first

---

### Post by exaviorn on 2008-11-03
When I first confrunted the problem I defragged my pc, now it says that I do not need to defrag- should I anyway?

---

### Post by Pumalite on 2008-11-03
The PageFile issue is more important than defragging.

---

### Post by exaviorn on 2008-11-04
The partitioning did not work! The job did go on for a couple of minutes before saying that it was checking the drive for errors after the real patitioning, however the application just dissapeared! I had to boot the app again, the it gave me a warning sign which I had recived numerous times during my partitioning attemps.

---

### Post by Coreigh on 2008-11-04
As others have said gparted is refusing to re-size because it is detecting a problem with your hard disk. This *may* be a serious problem, you might consider buying a new hard drive they are relatively cheap. However this may only be that Windows did not shut down cleanly.

Boot back in to Windows, don't rush it let it come up and get settled.
Open the Terminal Start >> Run, type CMD and click OK
In the Terminal type: ```
CHKDSK /F /X 
``` and press enter, you will get a message indicating you need to re-boot.
Re-boot back in to Windows, go through the whole shut down process, **don't hard power-off or pull the plug**. 
Again don't rush it. It will go through a thorough check-disk process and clean up the disk. Wait for Windows to come all the way back up.
Do a full shut down (don't rush or pull the plug)
Boot back in to Ubuntu (or the Gparted LiveCD) and try the re-size again.

If at this point the re-size does not work then it is definitely time to get a new hard drive.

---

