---
title: "Problem installing Ubuntu alongside Windows 7"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by Gornarok on 2015-09-26
Hello,
so I tried installing Ubuntu first by using Wubi (which I learned is not supported any longer so should not be used), while doing so I encountered error: Failed to partition selected disk. I learned that its a bug in Wubi 14.10 (I hope the number is right)

So I made installation usb and tried to install like that. The installation boots normaly, the problem is that once I click "Install alongside windows 7" the pc restarts itself and either its goes into Ubuntu preinstall menu or it boots to Windows.

Any idea what I should do?

Should I try different distribution of Linux? 

Thank you

---

### Post by grahammechanical on 2015-09-26
When you say "wubi 14.10" do you mean Ubuntu 14.10? If so, you should not be using Ubuntu 14.10 as it has reached end of life. You are better off installing Ubuntu 14.04.3 or Ubuntu 15.04 but keep in mind that 15.04 is only supported for 9 months starting from the end of April 2015. And 15.10 which will be released at the end of October 2015 will also only be supported for 9 months.

Try again with 14.04.3 or 15.04. If Windows 7 came pre-installed then it is possible that the motherboard is using what may be called BIOS boot system with a disk partition table that only allows 4 primary partitions. If the manufacturer and Windows have used up the 4 primary partitions then it is not possible to use the Install alongside option as the installer cannot create the 2 partitions that it needs to install Ubuntu with. This could be the reason why the installer is setting off a restart.

Load into Windows and use a Windows utility to examine the hard disk partition layout. Take a screenshot and post the image in this thread. In that way we can see the partition layout for ourselves.

You may need to reorganise the partitions. Use Windows utilities to defrag the hard disk more than once and restart Windows each time. Use Windows utilities to delete and resize Windows partitions to create unallocated space that the installer can use for Linux partitions.

You will get more advice once we see that screenshot.

Regards.

---

### Post by Gornarok on 2015-09-26
Hi,
oh so only 14.10 is bad and I can use Wubi for the rest? Good to know. I tried to Wubi Ubuntu 14.04 but when I restarted the PC it just booted Windows without any chance to select boot of Ubuntu.

And here is my partition image: C(system disk)/D/E and reserved space [http://imgur.com/cxjK6Zl](http://imgur.com/cxjK6Zl)
[IMG]http://imgur.com/cxjK6Zl[/IMG]

---

### Post by oldfred on 2015-09-26
You also have dynamic partitions, that is proprietary to Windows and will not work with Linux.
And dynamic partitions do not work with some Windows standard repair tools either. :)

       Forums Staff recommendations on WUBI
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]http://ubuntuforums.org/showthread.php?t=2229766

      [/URL]
 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html

[/URL]
 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]
[/URL]

    [URL="http://ubuntuforums.org/showthread.php?t=2229766"]
[/URL]

---

### Post by yancek on 2015-09-26
> oh so only 14.10 is bad and I can use Wubi for the rest? Good to know.

No.  Wubi is not being developed and is not supported at all.  According to their site, it won't work at all with windows or later.  You might get it to work with older versions of windows but it isn't supported.  In addition to the Dynamic disks problem, your drive is used with the four partitions currently on it so you would have to shrink one to make room for Ubuntu and if you are using MBR and not GPT, you would need to delete a partition.

---

### Post by Gornarok on 2015-09-26
OK, thank you all. Im not looking forward to this, but I guess there is no help. If my work wouldnt be much easier in Linux I think Id pass on this till my next system reinstall... Ill see if what I can do...

---

### Post by Mark Phelps on 2015-09-26
> **Gornarok said:**
> OK, thank you all. Im not looking forward to this, but I guess there is no help. If my work wouldnt be much easier in Linux I think Id pass on this till my next system reinstall... Ill see if what I can do...

Don't know what you mean by "no help"!!

Oldfred's post has LOTS of help in it -- you need to read through the details because, somewhere along the line, a windows partitioning tool was used to try and create a new partition -- and THAT automatically forced the conversion of ALL your partitions in Windows from basic volumes to dynamic disks.  This is not a situation you want to keep.

So, instead, you need to read Oldfred's links about EaseUS conversion products to convert your dynamic disks back to basic volumes.

Once that is done, you will than have 4 primary partitions on your drive -- which is all you are allowed to have.  But, if you come back after that, folks can give you advice then about installing Ubuntu, because with basic volumes, that can be done.

---

### Post by Gornarok on 2015-09-28
Sry I meant that there is no way around it, that I have to do stuff with my HDD I hoped I wont have to. I thanked everyone in the first place :)

---

