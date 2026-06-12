---
title: "Need assistance with fixing Windows boot using boot-repair"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by jeked on 2016-06-28
Hi,

Firstly:
[http://paste.ubuntu.com/18069760](http://paste.ubuntu.com/18069760)

Windows laptop that is unable to find a bootable device.

We have gone through our limited knowledge of recovering the partition table using gpart and testdisk which only found a single partition.

It is a Dell laptop (OEM) with Windows 7 Pro.

When we boot now after the testdisk we get an error:
Error when booting.
Ctrl + Alt + Delete to restart

Any help greatly appreciated.

John Crombie

---

### Post by oldfred on 2016-06-28
You do not have standard Windows 7 partition table.
Default with most Windows in BIOS mode is a 100MB boot partition at beginning of drive and then main install.
You have a gap before first partition. Did you not recover all the partitions with testdisk?

What got you into this? Is perhaps hard drive failing?

Do you have good backups? If not you may need a tool like photorec that scans drive for anything that looks like a file. But some have posted Windows tools may work better.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

        [URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step
      [/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 
    [URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]
[/URL]

---

### Post by yancek on 2016-06-29
How about using the 'repair' option on your windows installation DVD.  Posting more information on what led to this situation might give someone an idea to suggest.  Since you don't have any Linux/Ubuntu and this is solely a problem with your microsoft windows system, you might be better off doing a search at the microsoft support site or a windows forum.

---

### Post by jeked on 2016-06-29
Hi and thanks for both reply's :)

The user of the laptop said that "laptop was powered off on Friday and wouldnt boot on Monday"...so no help there unfortunatley.

In regards to testdisk:
"Did you not recover all the partitions with testdisk?"
There was only a single partition show even after doing a 'Deep Scan'

Running the windows repair option from Windows 7 Install disk is unable to find any windows 7 installations on the disk.

The SMART checks on the drive from Ubuntu running extensive tests come back with no errors so at the moment we are assuming the drive is OK.

At this point we are trying to recover the data from the disc. All data is backed up to External HDD and email 'in the could' however the user had been Archiving to his local laptop and not his office 365 Archive and now has lost 40+GB of emails...winning.

The non-standard partition table is likely to be due to Dell. Typically we have seen: Boot, Recovery, C:\, SomethingElseDell.

Ill give Recuva a shot as from here I am thinking the quickest way forward is data recovery and then reinstall.

---

