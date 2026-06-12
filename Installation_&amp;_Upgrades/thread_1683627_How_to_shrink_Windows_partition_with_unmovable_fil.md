---
title: "How to shrink Windows partition with unmovable files in dual boot installation"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2011-02-07
To install Ubuntu alongside Windows 7, I have to shrink Windows 7 partition C:. But due to some unmovable files, I cannot shrink as much as I plan  by using Windows own shrinking tool. I guess many of you who have both OSes on the same hard drive must have similar experience. How to solve this problem?

Any reference that can help is also appreciated!

Thanks and regards!

---

### Post by Quackers on 2011-02-07
In my experience Windows 7 will voluntarily shrink by about half (unless more than half is used, obviously :-) ). Any more than that and you may struggle. I believe sometimes that turning off the paging file can help.
Have you defragmented Windows first?
How much are you trying to shrink it by?

---

### Post by flylehe on 2011-02-07
Thanks!

I have defragemented first.
My C: partition is 220 GB, I want to shrink it to 70 GB, create 110 GB for D: and the rest for Ubuntu partitions. How can I do that?

I checked "Event Viewer" and found that the unmovable file that prevent further shrinking is:
> 
The last unmovable file appears to be: \ProgramData\Microsoft\Search\Data\Applications\Windows\Projects\SystemIndex\Indexer\CiFiles\00010015.wid::$DATA

Do you know how I can move this file away? I guess I have to move the whole \ProgramData away, not just that file.

Thanks!

---

### Post by Quackers on 2011-02-07
I'm afraid I don't know what the importance of that file is. I do know that Windows stores certain data at the end of the drive that can cause problems if removed, but I don't know if that is the file you quote.
If you go to disk management and right-click on the C: partition and select "shrink", how much shrinkage is being offered?

---

### Post by flylehe on 2011-02-07
The allowable maximum shrinkage is around 100 GB. But I hope to shrink 150 GB

---

### Post by Quackers on 2011-02-07
Well, I suspect gparted will do it, but beware, resizing NTFS file systems with gparted can (occasionally) go wrong! Make sure you have good backups, recovery dvd's or an installation disc, and a Windows repair cd.
Then it's up to you :-)
If you do go down this route you should reboot Windows at least twice, to make sure it is happy about the resize, before you do any further partitioning.

You could also wait for other opinions/suggestions first :-)

---

### Post by JLangford on 2011-02-08
Try defragmenting your windows partition, this often moves 'unmovable' files to different sectors of the hard disk.

---

### Post by flylehe on 2011-02-08
@JLangford: I have tried Windows own defrag tool, but it does not move unmovable files.

I don't want to move these unmovable files using copy and delete, because it might damage the Windows system. So I prefer to find setup to eliminate the unmovable system files and after I can shrink as much as I plan, I will re-setup the unmovable system files.

As posted earlier, the unmovable file that prevent shrinking is now:

> \ProgramData\Microsoft\Search\Data\Applications\Windows\Projects\SystemIndex\Indexer\CiFiles\00010015.wid::$DATA  

I guess the file belong to Windows Search. Can I set up somewhere in Windows system settings to temperately eliminate the file and similar ones (because there are many similar files under the same directory which I guess will also stand in the way of shrinking and unmovable by defrag)?

---

### Post by oldfred on 2011-02-08
Some discussion of the issues and workarounds. Is Vista but 7 is the same.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

With windows you do need to have 30-30% free space in the NTFS partition for it to work well.

---

