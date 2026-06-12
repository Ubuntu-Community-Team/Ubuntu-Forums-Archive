---
title: "Installing Ubuntu on Sony Vaio"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by puneit on 2008-07-05
Hello...

I have a very specific question regarding partitioning of hard-disk on a newly purchased Sony Vaio VGN-CR 363. The machine has a 250GB hard-disk with Windows Vista Home Premimum loaded on it. The machine also has a recovery partition which can be used to bring the C: drive into factory state.

You all know how Windows work. I have already experienced BSOD twice. Well, that's not the reason to dual boot to Ubuntu. I am an Ubuntu user and have been using it since Dapper. I need to have Windows for my portable hardware which is not supported in Ubuntu as of now.

Now, coming to my problem - I am not able to partition the disk using Vista built in partition editor (found in diskmgmt.msc). Have read that Partition magic will corrupt the OS since it is not compatible on Vista. So both are more or less uselss.

So, if I run partition the hard-disk using Gpartd say into 3 partitions and install Ubuntu in the second partiton. Now, I expect that at this point, Vista will not boot or function properly, due to loss of fragmented files. If, now, I run the recovery partition which will recover the C: drive to factory state, will it retain the partioning or remove it. Unfortunately the recovery doesn't have any option to partition the C: drive.

I know I can try this and see for myself, but recovering Vista and then Sony's software takes 1hr 45 min and loss of all customisation that I have done in last 2 weeks. I just want to know that will it work, the way I intend to do, so that my time is not wasted for nothing.
If not then I will have to live with Vista, which will be too sad...

---

### Post by avtolle on 2008-07-05
Have you defragged the drive and then used the Vista resize utility (sorry, not really familiar with Vista, but have been reading threads) to shrink the Vista partition? Then, as I recall, you may use the live CD to create new partitions for your proposed Ubuntu install.

---

### Post by theravenproject on 2008-07-05
What does the current partition table look like?

---

### Post by puneit on 2008-07-05
Yeah done that too. But Shrink partition in Vista (diskmgmt.msc) returns with an error that there is not sufficient space to create the partition.
Unlike XP, the Vista defragmenter doesn't show the progress graph. I am also new to Vista

---

### Post by puneit on 2008-07-05
Current partition table has two partition. One of approximately 10 GB for the recovery, and the rest as C: drive for Vista

---

### Post by avtolle on 2008-07-05
Did you (by error, easy enough to do IMO) try to shrink the recovery partition and not the Vista C: partition?

---

### Post by puneit on 2008-07-05
No. I am only trying to shrink the Vista C: drive. I am careful not to touch the recovery.

---

### Post by puneit on 2008-07-06
Solved:

Here is what I did.

I downloaded Power Defragmenter 2.0 from the following link [http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

Its a freeware tool, doesn't need installation and is good. Using this tool, Vista allowed me to shrink out a 70 GB partition. Good enough for me to install Ubuntu. 

I hope this information helps someone who is stuck like me.

---

### Post by akarmenia on 2008-07-06
If you would like to install XP and Ubuntu on the same computer, you can try my tutorial wiki at:

[http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot]("http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot")

---

