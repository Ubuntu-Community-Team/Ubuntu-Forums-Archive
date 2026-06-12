---
title: "Recover destroyed folder"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2014-09-01
Hello,

I am not a technical specialist and have done something really stupid.

I am running Ubuntu 12.04 LTS in double boot with Windows XP. I wanted to increase the size of my Ubuntu home (/dev/sda5) and root (/dev/sda6) folders which were running out of space.

I first used GParted with a live CD to increase the sise of the extended partiition (/dev/sda4) containing the Ubuntu home, root and swap folders. At that point there was about 2 GB in unallocated space at the beginning of sda4. Then I asked GParted to move sda5 to the beginning of the extended partition leaving 1 GB after it. It started working but I thought that had set a parameter incorrectly and stupidly cancelled the operation thinking that I could start again from scratch. After that to my horror there was no file system in the partition sda5 (question mark in the column for file system type). I asked GParted to reset it to ext3 - it called this reformatting but only took a second so I guess it did not physically erase the data. That of course did not bring back my files - the partition is still almost entirely unallocated. The situation is as follows:

[ATTACH=CONFIG]256029[/ATTACH]

I believe that the root folder and partition (sda6) and my NTFS partitions are undamaged. I cannot boot (no grub2). The sda5 partitition which contained the home folder shows empty except for 394 MB which I guess represents system files created when I reformatted to ext3. My original home folder was about 12 GB, but the sda5 partition has been expanded to 14.3 GB.

I have a recent back-up of most of my application data in the home folder, but my back-up of the whole home folder is about a year old (also I had copied it to an NTFS partition so perhaps there will be a problem with permissions in copying back?).

Could someone please help by informing whether i) it is possible to restore the files in my home directory or ii) if this is not possible whether I can copy my back-up home folder into the partition and get my system to reboot?

Thanks and best regards, John

---

### Post by Bashing-om on 2014-09-01
John_Rose; Despair not !

AND, Panic not. Just proceed in a calm and orderly fashion. IF you have not written to the hard disk, recovery is a good probability .
See:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
 And the more recommended tool:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112) <- Cheesemill post #7

[INDENT][INDENT][INDENT]ubuntu
[INDENT][INDENT][INDENT][INDENT]the impossible takes a while
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by John_Rose on 2014-09-01
Thanks Bashing-om,

I have not written to the disk BUT I did reformat the concerned partition to ext3. I will study all the links and try the analysis when I get back home next Saturday.

Will get back with the results asap. Best regards, John

---

### Post by Bashing-om on 2014-09-01
John_Rose; Good for all that;
So long as the disk it's self has not been written to, the prospects of restoring a usable partition table are good.
But study 3 times, develop a plan, as may only get the one shot at this (working on an 'image' of the hard drive might be a real good thing to do).

[INDENT][INDENT][INDENT]possible, possible
[/INDENT][/INDENT][/INDENT]

---

### Post by John_Rose on 2014-09-05
Dear Bashing-om and other friends,

I have studied the situation further and concluded that there was nothing straight-forward to do to recover my files. The ext3 Ubuntu home partition was not corrupted, but the file information inside was mashed up and mixed with information from the preceding shrunk partition. TestDisk is for partition repair and thus not relevant (the analysis showed nothing wrong) and the associated PhotoRec retrieved a mass of files without names, some coming from the preceding NTFS partition where I keep most of my data and which had been shrunk to give more space for Ubuntu.
On the web (see [http://ubuntuforums.org/showthread.php?t=2105712](http://ubuntuforums.org/showthread.php?t=2105712)) others have come to the same conclusion. One person did say that a similar situation was fixed with RStudio ([http://gparted-forum.surf4.info/viewtopic.php?id=3684](http://gparted-forum.surf4.info/viewtopic.php?id=3684)) but this was from 2008 and was for an NTFS partition.

Since the RStudio site ([http://www.rstudio.com/](http://www.rstudio.com/)) spoke about paying for a commercial product, and since I had not seen by then that RStudio can apparently be installed free ([http://ubuntuforums.org/showthread.php?t=2127394](http://ubuntuforums.org/showthread.php?t=2127394)), I decided to restore the data from my partially old and partially new back-ups. I have some problems with this which I will post on in a separate thread.

It would be nice if someone could continue by providing an evaluation of RStudio in this context - now too late for me. Of course I know now that one should never interrupt a GParted operation.

Best regards, John

---

### Post by Bashing-om on 2014-09-05
John_Rose; Yeah ;

Regrettable it came to that situation, and such a conclusion.
At the least is after a lot of sweat, effort and some tears, you are back up and running - that is a good thing - .

A big step in the learning process, I hope we all profit from you experience.

I have none with RStudio, so nothing else to say .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

