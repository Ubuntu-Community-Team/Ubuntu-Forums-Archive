---
title: "Installing Ubuntu on USB key"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by klaudio123 on 2013-06-10
For my ubuntu usb distribution I bought an 8GB key 
and set up 4GB as reserved extra space but during update 
process ubuntu warned:
not enough space, please use 'clean' command to
free up memory.
*(issue 1)*
I followed the advice and used the command:
'sudo apt-get clean' to free up memory but I wonder 
where temporary and old files are(I mean which folders 
contain them)and which commands to use to delete them, 
in order to free up more memory.
*(issue 2)*
I also followed the advice issuing to use 'Disk Usage 
Analyzer' but I don't know how data is organized.
Where can I find a table or and explanation about
the content of all folders of ubuntu file system?
*(issue 3)*
Then I also decided to investigate how space is used.
I opened my ubuntu usb key on ubuntu CD session, so I 
found my original system in casper folder(700 MB) + 
'casper-rw' file(2.9 GB) in main usb folder containing 
probably all updates.
I ask for confirmation about this.
*(issue 4)*
When I built my usb distribution I chose the option to
set up a reserved extra space for settings and documents,
but when I run my usb ubuntu I cannot access them as
a partition, however I can access my 'home' folder
from launcher, but as I cannot access my reserved extra
space as a partition I don't know which settings are
saved. 
As my 'casper-rw' file is about 2.9 GB I suspect 
that it represents my reserved extra space file(maybe
this extra space is fully contained in a unique file), 
so containing all settings, updates and home folder.
Or maybe updates are not counted as reserved extra 
space but still contained in file casper-rw.
Which is the truth? Which folders I find in 
'Disk Usage Analyzer' are contained in my reserved 
extra space?
Can anyone please address this issue?

---

### Post by oldfred on 2013-06-10
RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

I have never liked Disk Usage Analyzer. In my 25GB / (root) partition it shows 240GB. Which is somewhat correct as I also link in two other 100GB partitions, but I usually want to know details of each partition not the sum. 
This shows by partition.
df -H

If you just have a installer with persistence it may be different.
      
 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With persistence you cannot update system as it will still install as originally downloaded. But you can save added drivers or your files.

      
 Linux Standard Base details
[http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html](http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html)

 Explanation of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

---

