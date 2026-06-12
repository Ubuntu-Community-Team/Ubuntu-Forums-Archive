---
title: "Installing Ubuntu. Want to make sure it goes on the correct partition."
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by deleyd on 2008-02-04
I want to make sure I get Ubuntu to install on the correct partition I have created for it.

HP Laptop dv9410us Windows Vista 160GB hard drive. (Saw post about not installing 7.10, so I'm installing 8.04alpha. Live CD seems to work fine, so ready to install for real now.) 

I previously made a 10GB partition on the disk by shrinking my C drive in Windows Vista. I'm at the "Prepare Partitions" part of the install, Step 5 of 8, and it says:

/dev/sda1  ntfs  /media/sda1   140526 MB [COLOR="Red"]my C drive Vista[/COLOR]
free space                                  10736 MB [COLOR="Red"]want Ubuntu here[/COLOR]
/dev/sda2  ntfs  /media/sda2       8777 MB [COLOR="red"]D drive HP system backup[/COLOR]

If I select the "free space" and click 'Forward' it says:

"No root file system is defined. Please correct this from the partition menu."

If I click "New Partition" button, it gives me "Create a new partition" dialog, with options I'm not sure about.

Type for new partition: {Primary or Logical?}
New partition size in megabytes (1000000 bytes): 107326
Location for new partition: {Beginning or End?}
Use as: {ext3, but maybe I should select Fat32 so I can  access partition from Windows Vista?}
Mount point: {no options}

I'm not sure what to select here, Primary or Logical, Beginning or End, ext3 or Fat32?

I also tried using the "Guided: Use largest continuous freespace" option instead of "Manual" at the 'Prepare disk space' dialog, but it ended up saying it would put part on partition3 and the other part on partition 5, which confused me, as I made only one free partition. I've since read in this book, "Ubuntu requires at least two partitions (one for the system and one for virtual memory swap space)".

Is it OK to go ahead with the "Guided - use largest continuous free space" option, and let it install on what it calls partitions 3 and 5? I just want to make sure it's not going to erase Windows Vista before I go ahead and do this.

Complete novice to Linux, though savvy with Windows & programming.

---

### Post by shutslar on 2008-02-04
It appears that you have freed up disk space for your install but you have not actually partitioned it.  You should probably use gparted (install it from the livecd) and move your HP system backup next to your vista partition making your free space at the end of your disk drive.  Let the automatic install do the partitioning for you and it will create the 2 partitions you need.  

Hope this helps.

---

### Post by zvacet on 2008-02-05
Im sure,reading [this](http://www.psychocats.net/ubuntu/installing) will help you.

---

