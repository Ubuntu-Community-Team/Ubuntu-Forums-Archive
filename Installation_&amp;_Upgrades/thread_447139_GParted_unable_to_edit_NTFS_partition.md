---
title: "GParted unable to edit NTFS partition"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by tbonepower07 on 2007-05-17
Ubuntu 7.04
7 yo Gateway w/ Windows XP
Attempting to dual boot
Can't resize partition
chkdsk /f
...


I am trying to install Feisty on a friend's 7 year old and _extremely_ slow/unusable Gateway, and he is letting me create an Ubuntu/XP dual boot mainly because I'm putting in a very good word for Ubuntu.  Unfortunately, I can't resize the existing XP partition.  GParted returns an error saying that I should resize the partition to a different size - one smaller than the existing used space (I can't delete his files - one, he  wouldn't let me, two, GParted wouldn't let me).  The details said that I should run "chkdsk /f" on windows and reboot twice; I did so.  However, I am still unable to edit the partitions.  The in-installation partition editor (which is an instance of GParted, no?) lags for many minutes, with radio button choice not appearing - I suspect this is because it is trying to automatically repartition the drive but cannot.  Finally, I know that the CD is not corrputed because I successfully used it to install 7.04 in a virtual machine.  Looking through other posts, I saw that the solution might involve reducing Windows swap space / defragmenting the drive, but I couldn't find a definitive step-by-step approach (I am quite a newbie, and I need this - I don't want to screw up my friend's computer).  Help would be appreciated.

Jack

---

### Post by tbonepower07 on 2007-05-17
Also, it is possible that the GParted LiveCD will help?  I have been using the GParted on the Ubuntu LiveCD.

---

### Post by ugm6hr on 2007-05-17
The version of GParted in Ubuntu Synaptics is older than that available on the GParted LiveCD.  I can confirm that the GParted LiveCD has the capacity to resize (and I think also move) NTFS partitions.

I would recommend you use the GParted LiveCD to resize the existing NTFS partition, and leave an "unpartitioned" or empty space for the linux swap / Ubuntu installation.  The Ubuntu Live CD will then automatically sort that out for you (just select the "use largest continuous empty space" option).

---

### Post by punong_bisyonaryo on 2007-05-17
I originally had a dual boot PC. however, I would now like to get rid of the windows partition. I am worried, though, because hda1 (the ntfs partition) has a "boot" flag on it. I want to redistribute this partition into the other existing partitions without risking my Ubuntu files. How do I do this? I'm using Dapper by the way.

---

### Post by jerrylamos on 2007-05-17
For dual boot, first thing to do is in Windows to defrag.  That gathers together the files somewhat and with any kind of luck leaves some space at the top.  After I did that, I then went into control panel, system, virtual memory, and made the paging size zero.  That turns paging off and gets rid of the page file which is usually at the high end of memory.  Defrag again, look at details, and estimate very closely how much empty space there is at the top of memory.  That's as much as you can safely resize Windows down.

Bring up Gparted on CD Live and see if it can resize the Windows partition down what you saw as clear space after defrag.  Then try resizing down that much, no more.  In the empty space you allocate a swap 256 MB at least, and the rest as partition / to be formatted ext3.  It has to be at least 2 GB.  You can do a good bit with 4 GB, and 8 GB is fine unless you do a lot of photos or music.

On rebooting Windows next time, best go into control panel, system, virtual memory, page size, "let windows manage".

Let us know how it goes.  Cheers, Jerry

---

### Post by tbonepower07 on 2007-05-18
Thank you very much, ugm6hr and Jerry.  I'll try out your instructions and get this thing installed.

Jack

---

### Post by BrianKDav on 2008-05-11
I'm not sure if this will solve your caution sign in gparted, but it did mine.  On the file menu of gparted, select "features".  When I did this for the gparted that came with Hardy, nothing of ntfs was shown as supported.  I went to the gparted website, and found a reference to "ntfsprogs" in the features documentation.  The bottom line hare is that I fixed this problem with "**sudo apt-get install ntfsprogs**".

I know I need to send the following two comments somewhere else to get them heard, and I will when I get time:
[LIST]
[*]To the Ubuntu team: I think that ntfsprogs should be part of base Ubuntu - there's just too many people who will need it moments after they install Ubuntu.
[*]To the gparted development team.  The text displayed behind the caution sign should advise the user to check the active features via the menu bar.  That would have saved **thousands of hours**, worldwide, in little one-hour pieces spread across many geeks.
[/LIST]
But aside from all that, thank you all for your own hours of hard work on both products.

--Brian

---

