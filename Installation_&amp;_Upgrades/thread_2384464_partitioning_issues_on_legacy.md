---
title: "partitioning issues on legacy"
date: 2018-02-07
forum: Installation &amp; Upgrades
---

### Post by supernooblet on 2018-02-07
Hello! 

I'm trying to install ubuntu 16.04 LTS on an old Toshiba laptop that's on legacy. I understand that I have reached the maximum partitioning of 4 and so I can't create an additional partition for ubuntu for now, but I am really, really confused as to which other partitions I should delete/extend. I don't actually need what's left on my Toshiba but I suppose dual-booting is a safer option for a beginner:oops: Here is my boot-info: [https://paste.ubuntu.com/26536722/](https://paste.ubuntu.com/26536722/)

I look forward to your replies and thank you in advance!!

---

### Post by oldfred on 2018-02-07
First you must have backups.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm) 

You seem to have several recovery partitions. Often you can backup vendor tools partition as it usually is one of the smaller partitions.
Some even work from a logical partition.

You can use fixparts to convert sda3 to logical.
Then use Windows tools to shrink sda2.
Then use gparted to expand extended partition to in effect move unallocated space into extended partition.
Then you can create as many logical partitions as you want in the extended partition.

      
 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[URL="http://www.rodsbooks.com/fixparts/"]http://www.rodsbooks.com/fixparts/

      [/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
    [URL="http://www.rodsbooks.com/fixparts/"]
[/URL]

---

### Post by TheFu on 2018-02-07
Welcome to the forums.

There are lots of different ways to attack this issue.  Here's my opinion. 

If you don't need Windows, wiping it will make things much easier.  MBR or GPT doesn't matter to Linux.  I'd switch to GPT partitioning to get hundreds of partitions. There is a small risk that the BIOS won't work with GPT.  But I've not seen that with my 2010-period systems. They worked with GPT and Linux.

I don't understand how dual-booting is safer for a beginner, if you don't plan to run Windows again.  If you have a properly created Linux boot flash drive, and it boots with a "Try Ubuntu" click, there really isn't much danger.  You have nothing to loose. If you like, a $50 replacement HDD can be used to completely remove the dangers. Plus, many people need a backup storage solution anyways.

Wiping everything is always safer.

16.04.3 is the version you want today. Good choice staying with LTS.

Of course, there will be different opinions.

---

### Post by oldfred on 2018-02-07
+1 on TheFu's suggestion.

My 2006 Toshiba laptop was dual boot with XP & Ubuntu  12.04 and only had 1.5GB of RAM. I got it two weeks before Vista, not wanting Vista. Soon after started learning Linux and dual booted with Ubuntu.
When 12.04 expired, I retired laptop.

But just to see how well it worked I installed 16.04 64 bit Ubuntu but with gnome-panel  as lighter weight gui on entire drive using gpt partitioning.
And it worked well enough to be usable, just not as fast as my newer UEFI systems with lots of RAM.

---

### Post by supernooblet on 2018-02-09
Thank you for all of your replies! I appreciate everyone's kind help and detailed explanations. Unfortunately I still couldn't wrap my head around partitioning so I followed TheFu and oldfred's advice and wiped clean Windows instead. Thank you once again. :)

---

