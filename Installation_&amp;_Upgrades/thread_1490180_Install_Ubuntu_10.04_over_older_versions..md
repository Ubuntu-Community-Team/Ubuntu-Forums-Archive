---
title: "Install Ubuntu 10.04 over older versions."
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by Akpsp on 2010-05-21
How can i install Ubuntu 10.04 over my older version of Xbuntu 9.10? I already have the 32 bit ISO downloaded. I am on step 5 of 8, Select Partition. But it aint letting me select the older ubuntu partition. Any ideas?

---

### Post by 2hot6ft2 on 2010-05-21
Select Manual and click Forward then select the partition you want to install it to and click on change then set the file system and mount point then continue.
:popcorn:

---

### Post by Akpsp on 2010-05-21
> **2hot6ft2 said:**
> Select Manual and click Forward then select the partition you want to install it to and click on change then set the file system and mount point then continue.
:popcorn:

What File system should i use? and what about the mount point, it shouldnt matter right? and what about grub? i heard it installs over the windows boot.

When i try that its saying No root file system.

---

### Post by oldfred on 2010-05-21
You can use ext3 or ext4. Ext4 is the standard. When it first came out a year or two ago it was a lot faster but then they found issues. In fixing issues it now is a little faster and supposedly better.

You have to specify / (root) and the format. It will find your current swap. If you have a separate existing /home you specify that but check off do not format.

You want grub2 to manage booting and should install to the MBR of the same drive you install to. If you have more that one drive use the advanced button on screen #8 where it says ready to install to choose drive to install to. Do not install to partitions.

---

### Post by Akpsp on 2010-05-21
> **oldfred said:**
> You can use ext3 or ext4. Ext4 is the standard. When it first came out a year or two ago it was a lot faster but then they found issues. In fixing issues it now is a little faster and supposedly better.

You have to specify / (root) and the format. It will find your current swap. If you have a separate existing /home you specify that but check off do not format.

You want grub2 to manage booting and should install to the MBR of the same drive you install to. If you have more that one drive use the advanced button on screen #8 where it says ready to install to choose drive to install to. Do not install to partitions.

So what should i set mount point to?

---

### Post by dik909 on 2010-05-22
new Q, sorta:

i was running Ubuntu 8.04 on this old frankenstein box i received out of all recycled parts.  it's great !!  

anyways, i did a full Lucid Lynx install over it, and now i'm having strange, serious-seeming issues, such as:

-randomly shutting down
-not fully shutting down when prompted to do so



i never had these problems with Ubuntu 8.04, so i'm wondering where the disconnect is coming from... 

thoughts, suggestions ??

---

### Post by Akpsp on 2010-05-22
> **dik909 said:**
> new Q, sorta:

i was running Ubuntu 8.04 on this old frankenstein box i received out of all recycled parts.  it's great !!  

anyways, i did a full Lucid Lynx install over it, and now i'm having strange, serious-seeming issues, such as:

-randomly shutting down
-not fully shutting down when prompted to do so



i never had these problems with Ubuntu 8.04, so i'm wondering where the disconnect is coming from... 

thoughts, suggestions ??

So your saying...? O.o

---

### Post by hansdown on 2010-05-22
Sorry to continue the  interrupt, Akpsp, but dik909, If you are using older hardware, there could likely be issues, not due to the OS, but to the fact, that the hardware makers don't supply drivers, etc.

---

### Post by Akpsp on 2010-05-22
Thats okay handsdown. Im still Xubuntu tho. lol

---

### Post by hansdown on 2010-05-22
Thanks Akpsp.

2hot6ft2 has the answer you are looking for.

---

### Post by Akpsp on 2010-05-22
> **hansdown said:**
> Thanks Akpsp.

2hot6ft2 has the answer you are looking for.

Why does it keep saying "No root filesystem defined" "Please correct this from the partition menu." 

I changed the partition menu to this: 

New Partition size in megabytes:                          62166

Use as:                                                                  Ext4 journaling file system

Format the partition:                                              The box is unchecked

Mount point:                                                           /home

Then i click forward and thats when it says no root filesystem. :confused:

---

### Post by darkod on 2010-05-22
> **Akpsp said:**
> 

[COLOR=Red]Mount point:                                                           /home
[/COLOR] 
Then i click forward and thats when it says no root filesystem. :confused:
You also need to have a partition with mount point /. That is your root (system) partition.

If you want separate /home partition, what you described above is correct, but you need another partition as /.

Or just select mount point / for the above mentioned partition but in that case you won't have separate /home partition if that is your goal.

---

### Post by Akpsp on 2010-05-22
> **darkod said:**
> You also need to have a partition with mount point /. That is your root (system) partition.

If you want separate /home partition, what you described above is correct, but you need another partition as /.

Or just select mount point / for the above mentioned partition but in that case you won't have separate /home partition if that is your goal.

Okay, thx. Now im at step 8. Where should i install the grub? The default is at /dev/sda 

Also, on the "Ready to install page," it says "The following partitions are going to be formatted" partition #6 as swap. Should i just install?

---

### Post by darkod on 2010-05-22
> **Akpsp said:**
> Okay, thx. Now im at step 8. Where should i install the grub? The default is at /dev/sda 

Also, on the "Ready to install page," it says "The following partitions are going to be formatted" partition #6 as swap. Should i just install?

Yes, grub2 would usually go to the MBR of the disk, in other words /dev/sda without a number in it.

You won't format the root partition too, just swap?

---

### Post by Akpsp on 2010-05-22
> **darkod said:**
> Yes, grub2 would usually go to the MBR of the disk, in other words /dev/sda without a number in it.

You won't format the root partition too, just swap?

Should i go back to Step 5 and check the box "Format Partition?"

---

### Post by darkod on 2010-05-22
> **Akpsp said:**
> Should i go back to Step 5 and check the box "Format Partition?"

OK, lets go a step back. When reinstalling over previous version, there are usually two situations:

1. Your previous version had only / and swap partitions. In that case your Home folder is inside / as a folder, and you need to backup all your data or it will be lost when you format /.

2. Your previous version had /, /home and swap partitions (3, not only 2). In that case, with the manual partitioning you set the correct mount points for / and /home, and you would usually format / but not format /home. Your personal files are in the separate /home partition and are safe if you don't format.

It seems you had only / and swap. If you don't format the new / you are setting up, it might leave traces from the previous version, which was not only older version but it was also Xubuntu, not Ubuntu.

It might still work OK, but in your place I would format /. Of course, that will delete ALL DATA ON IT, including anything in your Home folder in Xubuntu. Do you have a backup of everything you need? If you do, go back, tick the format box and proceed.

If you don't have backup, cancel this install process, boot Xubuntu, copy everything you need on external hdd or similar, and then proceed.

---

### Post by Akpsp on 2010-05-22
Its installing right now. I have backed up everything already. So if all go as planned, i'll hopefully be running my w7 and ubuntu 10.04.

---

### Post by Akpsp on 2010-05-22
Alright, I have Ubuntu 10.04 installed, it updated just fine. Windows 7 is booting ok. I'd like to thank all of you guys that helped me. I also like to apologize to some of you, I feel like I've annoyed some of you. lol

Once again, thx guys!!!!  :)

---

### Post by darkod on 2010-05-22
Excellent. And now you know how to do manual installs and not to depend on the automated methods. :)

---

