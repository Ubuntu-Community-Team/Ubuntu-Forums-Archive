---
title: "/dev/sda disappears when select &quot;New Partition Table&quot;"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by bg8ssxs on 2010-06-27
I want to install Ubuntu 10.04 on a brand new hard disk.  It shows in the "Use Entire Disk" drop down as /dev/sda.
 
I don't want to use the entire disk, so I select advanced partitioning.  I select the disk, and click "New Partition Table".  I get an error dialogue with a title of "??? ???" and the message of "??? ???".
 
After this happens, I can click on "New Partition Table" to my hearts content, and nothing happens.
 
Going back to the previous screen after this has happened, and my new, blank disk is no longer in the drop down.
 
Any ideas?

---

### Post by darkod on 2010-06-27
In advanced partitioning you should start creating partitions, not write a new partition table. That means completely removing the current one. You don't need to do that, you already have partition table and no partitions created on the disk. Just start creating them.

I hope the selection to write a new table didn't mess anything up. Try again, start the installer again, don't do forward/back because it doesn't remember changes.

---

### Post by darkod on 2010-06-27
PS. If you plan to install windows on the computer later, make sure you install it into primary partition, it has to be in primary. So you have to be able to create one more primary partition later.

---

### Post by bg8ssxs on 2010-06-27
The "Add" isn't high lighted unless you are sitting on "Free Space" if it is like 9.  
 
In this particular case, the "Add" wasn't ever highlighted no matter where I clicked. 
 
I did load up 9 CD, and verified my understanding of the older partitioning tool.  That worked fine.  I wonder if the tool changed drastically between 9 and 10?
 
Thanks for the reply.

---

### Post by darkod on 2010-06-27
I haven't noticed huge difference between 9.10 and 10.04. If by 9 you mean 9.04, there might be a possibility for the disk to have raid meta data on it if it was used in raid (but unlikely). Since 9.10 the installer can detect this meta data and acts differently.

So you are saying the Lucid installer is not allowing you to create any partitions into the unallocated space? But it shows it as unallocated?

---

### Post by bg8ssxs on 2010-06-27
I see a line for 
/dev/sda (highlighted)
then lines for 
/dev/sdb
  /dev/sdb1
  /dev/sdb2
  /dev/sdb3
 
I click on the "New Partition Table" with /dev/sda highlighted, and get the above mentioned dialogue, and the line for empty space never shows up.
 
9.10 is the unbuntu I have used to verify and am currently installing.
 
I have had slackware and SuSE installed on this very hardware (less brand new disk).  Never had problems like this.  Very aggravating and humiliating :)
 
Thanks for your continued attention.

---

### Post by ajgreeny on 2010-06-27
Even though it should do the same thing as the installer partitioner, you could try using gparted from the live CD you are using to install.

I know it is not truly necessary, but I tend to make my partitions with gparted and then use manual partitioning at install and simply use those ready made partitions.  It shouldn't make a scrap of difference to the outcome, but I always seem to find it easier to get the sizes I want, and also with gparted you can make the partition sizes conform with cylinder boundaries, and avoid error messages later in "sudo fdisk -l" commands.  I don't think the install partitioner allows you to do that.

---

### Post by darkod on 2010-06-27
> **ajgreeny said:**
>   I don't think the install partitioner allows you to do that.

It does, there is a tick box Round to Cylinder and it's ticked by default. What ever size you select, it will round it unless you deselect the option.

But I agree, in this case try Gparted, make the partitions, and then just select them one by one in the installer and use the Change button to specify how to use each partition. It might move you forward.

---

### Post by bg8ssxs on 2010-06-27
Thank you for all your replys.  I "essentially" (long way around the barn with 9.10 installation) did what you indicated, partitioning outside of 10, and then just using the partitions with the 10 installer.
 
I tried fdisk from the 10.04 live CD, but that was after one of the failed attempts.  fdisk -l only showed the /dev/sdb device.  I have never used the gparted.  That might have helped.

---

### Post by bg8ssxs on 2010-06-27
How do I mark resolved?

---

### Post by bg8ssxs on 2010-06-27
I spoke too early, it started the install, complained about second swap partitiion from older disk.  When I tried to go back to set that partitiion not to be used /dev/sda was no longer visible.

---

### Post by darkod on 2010-06-27
OK, boot the 10.04 cd in live mode first. Open Gparted in System-Administration. Get rid of the old swap partition (why is it still there???).

Again if necessary, create the partitions on sda as you like them. Then start the installer and try again. Any progress?

---

