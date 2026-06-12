---
title: "New user intro, and 6.10 hangs at install"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by Skidpad on 2006-12-30
Greetings all, great forum/community! N00b user here, well almost a new user that is...let me explain...

3 yr old Compaq laptop, currently running XP, 40GB single partition hd , with 26 GB of free space.   System will run a LiveCD just fine, so I thought I'd install 6.10 from the LiveCD (not alternate) and join the crowd.  :)

Here's the problem: when presented with the partitioning options, checking the "automatic resize" option does nothing but "spin the wheel", as gparted never appears (even after an hour).  The optical drive never spins and I have to cancel the installation.

If I choose the "manually resize" partition option, I can set everything up (ext3, swap, etc), gparted begins, optical drive spins, but when it comes time to actually resize my XP partition, I get an error mesage stating that hda1 cannot be resized.  

If I choose the use "largest available free space" option, it appears as though the installation may work, but I am unwilling to use this option without some control over the installation and partition sizes.



Here's the interesting part: during my defragmenting efforts prior to attempting my install, there are files at the end of my hd that are unmovable, either with XP's defragmenting utility, or with PerfectDisk 8.  The files can be seen in the treemap and won't move with either defrag program.  Could this be causing my partitioning errors and preventing Ubuntu installation?  

As a side note, I've burned 3 different LiveCD's, all at diferent speeds, and with two different software pakages, checksum matched as well; I get the same errors/hangs with all of them.

Any input would be greatly appreciated, I'm seeking feedback before trying the alternate CD.  Also looking forward to a full installation and contributing here whatever I can.  :)
Thanks to all.

---

### Post by riven0 on 2006-12-30
Looks like you've got the same problem I did when first trying to install Ubuntu. Those files that are unmovable on your harddrive is a hidden partition XP set aside to prevent the hd from being re-partitioned.

The way I fixed this was to run chkdsk. Start >> Run >> chkdsk

You may have to restart the comp to complete it. That should unlock the hidden partition. 

good luck! :KS

---

### Post by Skidpad on 2006-12-30
I ran chksdsk from the command prompt, and again at reboot - still no help.  I am beginning to wonder if partitioning the hd first, and then trying to install Ubuntu may be a better way to go (?)

---

### Post by riven0 on 2006-12-30
> **Skidpad said:**
> I ran chksdsk from the command prompt, and again at reboot - still no help.  I am beginning to wonder if partitioning the hd first, and then trying to install Ubuntu may be a better way to go (?)

You can try that. Either do it through Partition Magic 8 or [one of these free partitioners.]("http://www.thefreecountry.com/utilities/partitioneditors.shtml")

---

### Post by logos34 on 2006-12-30
You may have to delete the unmovable windows files and then reinstall them after you shrink the partition.
 
Take a look at this:
[Creating a Dual-Boot Windows XP and Ubuntu Laptop]("http://www.linuxdevcenter.com/lpt/a/6554")

---

### Post by taco_truck on 2006-12-31
Wow...I had the same exact problem you had where it hangs on the second to last step and the wheel just keeps spinning.  I need a answer to this problem, fast.

---

### Post by Sef on 2006-12-31
> Either do it through Partition Magic 8 or one of these free partitioners.

Do not use Partition Magic.  It and Linux tend not to work well together.  I would use [GParted]("http://gparted.sourceforge.net").

---

### Post by taco_truck on 2006-12-31
Use gparted for what?

---

### Post by riven0 on 2006-12-31
> **taco_truck said:**
> Use gparted for what?

To delete that hidden partition we were talking about. 

I did use partition magic 8 to resize a partition when gparted wouldn't go. That was fine. It was resizing that partition that went bad, (wiped out Ubuntu, it did :evil: ).

But in the end, it was all good; it gave me the incentive I needed to finally wipe out XP. :mrgreen:

---

### Post by Skidpad on 2006-12-31
> **logos34 said:**
> You may have to delete the unmovable windows files and then reinstall them after you shrink the partition.
 
Take a look at this:
[Creating a Dual-Boot Windows XP and Ubuntu Laptop]("http://www.linuxdevcenter.com/lpt/a/6554")
That's exactly what I needed to do, it was my pagefile and hibernation files getting in the way.  I used this link ([http://howtoprimers.com/techtalk/category/windows/](http://howtoprimers.com/techtalk/category/windows/)) to turn off hibernation and reduce my paging file.  I then rebooted and defragged.  Once defrag was complete, those two unmovable files were gone, and my Ubuntu installation took place normally!

I am now typing this in Ubuntu on my dual-boot laptop.  I'm a happy camper.  :D 

Thanks!

---

### Post by logos34 on 2006-12-31
Hey great!

---

### Post by handy on 2006-12-31
It's interesting how sometimes gparted will/won't do what you need to do on a drive, or only the Knoppix live CD will, or on occassion only booting a windoze drive with Partition Magic will succeed? :confused:

---

