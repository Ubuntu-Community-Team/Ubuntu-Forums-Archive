---
title: "Ubuntu Installer - Odd Partition Error"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by schmickers on 2007-06-28
Hi al,

Currently trying to install ubuntu side-by-side with a Windows XP install. Currently, the XP partition occupies the entire 80GB HDD.

I am having trouble resizing the NTFS partition. The ubuntu installer script will not do it at all, coimplaining about not having enough free space. Using GParted, I get the following output:



```
GParted 0.2.5

*Resize /dev/hda1 from 74.51 GiB to 44.42 GiB*    ( ERROR )
     	
check filesystem on /dev/hda1 for errors and (if possible) fix them    ( ERROR )
     	
*/ntfsresize -P -i -f -v /dev/hda1/*
     	
/ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80007262720 bytes (80008 MB)
Current device size: 80007266304 bytes (80008 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 9796993 (0x957d81): extra cluster in $Bitmap
Cluster accounting failed at 9796994 (0x957d82): extra cluster in $Bitmap
Cluster accounting failed at 9796995 (0x957d83): extra cluster in $Bitmap

```
... and so on ad nauseam, and then ...
```
Cluster accounting failed at 15337929 (0xea09c9): missing cluster in $Bitmap
Cluster accounting failed at 15337930 (0xea09ca): missing cluster in $Bitmap
Cluster accounting failed at 15337931 (0xea09cb): missing cluster in $Bitmap
```
... also repeated hundreds of times. It finally exits with:
```
Filesystem check failed! Totally 4160 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
/
```

I have chkdsk /f twice (and it shows no errors), rebooted multiple times, and defragged more times than I can count. My defrag analysis in Windows XP shows a block of unfragmented files (in blue) near the end of the HDD which remain there and do not get moved to the front of the drive despite repeated attempts at defragging. There are no unmovable files shown. Hibernate, System Restore, and the Paging File are all switched off.

Any suggestions as to how to continue?

Regards,

Michael

---

### Post by sampan74 on 2007-08-10
I am experiencing the exact same problem on my spanking new laptop. I have tried the same remedies as you without success - so far. Now I will try to start windows in safe mode and run chkdisk from there. Hopefully this can help...

---

### Post by sampan74 on 2007-08-10
Grrrr, no success when running chkdsk in safe mode. Actually the windows behaviour was exactly the same. A the chkdsk was scheduled on the next reboot...:confused:

---

### Post by sampan74 on 2007-08-10
Aha!!! Problem seems to be solved. The installation process is ongoing as i write this. Here's what I did:

Numerous chkdsk /f in Windows without success. Then I got tired of that and fired up Ubuntu 7.04 once again. Once Ubuntu came up I dismounted the Windows-partition that were reporting errors and fired up GParted (System->Administration->GNOME Partition Editor). Now GParted did not have any problems resizing my Windows-partition. 

Once having resized the Windows-partition, and thereby making space for my Ubuntu partitions) I had no problem creating the necessary partitions from within the Install application.... 

Hopefully the same works for you, my friend.

---

### Post by go_beep_yourself on 2007-12-31
> **sampan74 said:**
> Aha!!! Problem seems to be solved. The installation process is ongoing as i write this. Here's what I did:

Numerous chkdsk /f in Windows without success.

How did you get chkdsk /f to work? Each time I boot into Windows, open command prompt, and type that, I get the message that it cannot be done because the volume is in use. I've run chkdsk before logging in several times, and that hasn't solved the problem. My problem is a little different than yours but similar. Are you able to help any?

[http://ubuntuforums.org/showthread.php?t=654983](http://ubuntuforums.org/showthread.php?t=654983)

---

