---
title: "use the largest continuous free space???"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by ubuncha on 2010-01-04
I have been trying to set up my laptop to dual-boot between Ubuntu 9.04 and Vista, I have partitioned my disk in Vista, as I was advised to do in the blog linked to below. I have 20GB unallocated.
 When I get to Step 4 (Prepare Disk Space) in the Ubuntu installer I see that I rightfully have 20GB free space.
 Although in the aforementioned blog, when I come to Step 4 of the installation, when asked "Where do you want to put Ubuntu 0.04?" there should be an option for me to select such as "Use the largest continuous free space".

"If you have followed my guide this far and created the "unallocated" space then all you need to do is select "Use the largest continuous free space"(this option is available on pretty much every distribution) and click Forward." 
[http://www.coverlesstech.com/dualboot](http://www.coverlesstech.com/dualboot)

Can anyone tell me if Ubuntu 9.04 supports this function? Or maybe there's something I'm doing wrong.

If I select "Specify partition manually" and then forward at Step 4, I come to a table with a device listed as 'unusable', with a size of 21474MB. If I select (right-click) the 'unusable' device, the only option is 'undo changes to partitions'.

I hit the forward button hoping for more options but I get the "No root file system - No root file system is defined - Please correct this from the partitioning menu" error message.

Any advice would be greatly appreciated - Thanks!

---

### Post by mkoehler on 2010-01-04
It's been a while since I reinstalled, but there should be a few options on the install menu if I'm not mistaken.  From looking at screenshots of the installation screens ([http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)) these are the options you should have presented to you:

- Install them side by side, choosing between each at startup.
- Erase and use the entire disk
- Specify partitions manually (advanced)

In your case you should use the first option ("Install them side by side, choosing between each at startup").

---

### Post by ubuncha on 2010-01-07
Yea, it does seem pretty straight forward going by the tutorial, although at Step 4 (Prepare Disk Space), I am not given the option top "use largest continuous free space".
Most of the video tuturials recommend this way of partitioning for dual booting purposes.

I'm thinking that maybe I did'nt free up space correctly in Vista, or did'nt defrag after I freed the space, although it did say that I had "free space" in disk management in Vista...
     Just curious now though, as I went ahead and installed over Vista. I still have my recovery discs so I might consider dual-booting still if I can find out the right way.

---

### Post by Bartender on 2010-01-08
ubuncha -
What kind of PC you got?  There are different strategies used by different manufacturers, but if you're thinking about trying to dual-boot again, I have a suggestion.  Especially since you don't have too much time invested into the existing Ubuntu install.

Download GParted LiveCD (I call it "GPLCD" - link under my sig).  Find the latest stable version .iso, download, and create a bootable CD just like you did the Ubuntu download.  This can be done on a Windows PC.

Boot from the GPLCD and delete all partitions until the HDD is one big unallocated partition.  There's a trick to GPLCD.  Each time you give it a task, it will stack those tasks in the list below the picture until you hit the Apply button.  My suggestion - Apply each change as you go.

Then create a primary NTFS partition big enough for Vista.  Half the drive, one-third, whatever.  Apply the change.  Leave the rest of the drive unallocated, or create a big primary partition formatted as ext4, or create an extended partition - there are several choices.  I would create an extended, then create the logical partitions for Ubuntu inside the extended.  I just like doing it that way.  It's not hard to do, unless you're doing it the first time!

Apply all your changes, get out of GPLCD, boot into your Vista recovery disc.  The recovery disc SHOULD install to just the NTFS partition, leaving the rest of the drive ready for Ubuntu.  Run Vista a few times to make sure it's working before diving into the Ubuntu installation.

---

