---
title: "Raid1, BootITNG and Ubuntu - Wrong Combination?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by GG_HTPC on 2007-06-21
Hi Everyone,
I am trying to build a dream PVR using Intel Core2 Duo, 2 GB RAM, Asus P5wDH motherboard, LiteOn optical drive and Seagate 7200.10 500GB SATA HDD. I have given the brief background of what I have already tried below. The problem is described in last paragraph of this post. 

 In first round, I had partitioned my HDD using BootitNG partitioning utility and installed Windows XP MCE roll-up 2. After getting frustrated with the limitations of Windows XP MCE, I decided to try MythTV and Ubuntu. So, I shrinked my Windows partition and installed Ubuntu in its own partition. No problem in Ubuntu installtion except my TVTuner card (MyHD MDP130) and Soundcard (Azuntech Meridian 7.1) were not supported on Linux. But I am determined so I changed my TVTuner card to FusionTV 5 Gold RT (supposed to be supported by MythTV) and enable onboard sound card supported by ALSA. :popcorn: This week, I also bought another Seagate 7200.10 500GB SATA HDD to implement a Raid 1 configuration. I have more than 400 audio CDs and 60 GB worth of photographs on my network drives. I thought a Raid 1 configuration will reduce some risk. 

After I installed the second HDD and enabled the BIOS utility (Intel Matrix) storage manager, I had to create a new RAID volume and was force to wipe the entire HDD. :mad: But I took this opportunity to repartition the HDD as I wanted. One big partition for my data (~400 GB), one partition for Windows (sorry, I need to run MS Project and other Windows projects) and one partition for Ubuntu/MythTV. BootItNG creates its own partition for itself as well. 

After creating the partitions with BootITNG, I poped in the Ubuntu LiveCD in the optical drive to install Ubuntu. But the installtion halts with a message "/bin/sh: can't access tty; job control turned off". Since I was able to install successfully from the same CD, the installation image should be fine. After reading the posts in Ubuntu forums, I tried switching off the second HDD. No Luck! Then I deleted the partitions created by BootIt and tried the Ubuntu install again. This time, the installation started just fine. So I plugged back the second HDD and rebuild the RAID volume and started the installation, again. I created a partition for Ubuntu manually from the Partition dialog in the installation. Again, I tried to partition the unsed space using BootIT, but BootIT could not use the free space for anything:confused: On top of it when I installed BootIT, again, Ubuntu will not Boot :frown: Ubuntu installation starts fine if I delete BootIT partition/EMBR](*,)

Right now I am very frustrated and not sure if BootIT/Ubuntu and Raid does not work together? Any help offered is appreciated. Thank you in Advance.

---

### Post by GG_HTPC on 2007-06-22
Update - I deleted all the partitions (kept Raid configuration) and popped the LiveCD again. Installation went fine but now I dont have any space for Windows installation and Extended partition for Data.:(

---

