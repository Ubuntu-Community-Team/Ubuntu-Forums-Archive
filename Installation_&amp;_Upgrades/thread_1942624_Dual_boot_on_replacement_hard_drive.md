---
title: "Dual boot on replacement hard drive"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by mikeo56 on 2012-03-17
Hello:
I seek enlightenment. Need to replace a failing hard drive and wish to do a fresh install of Win XP and also Ubuntu on the new replacement drive - WD PATA 320gb. 
I have never installed an OS. I am aware that, basically XP should be installed first, Ubuntu second and grub will manage the booting of both OS's and that there are ways to partition the disc that will facilitate the PC's operation.
I need a basic outline of how to do this and I have a couple of questions now and may become more than a little confused as this progresses. 
What would be the best way to partition and after partitioning how does the OS installations relate to their particular partitions? XP and related programs/primary partition, Ubuntu and related programs/primary partition, shared files in extended partition and a a last swap partition. What can go in the shared partition? What is in a swap partition. Maybe it is better to make it simpler?
Can Ubuntu 11.10 work with the shared partition being NTFS? 
Can I leave my still functioning old hard drive in as master or slave, install the new drive, then install XP and Ubuntu, and remove the drives and reinstall the new drive alone with good results? If I switch out drives from two to one and the new goes from slave to master will this mess up the letter labeling of the drives - C:, D:, E: etc?

---

### Post by raja.genupula on 2012-03-18
* make the new HDD as master
* Install the XP .dont worry about partitions . keep some space as empty for Ubuntu and for remaining partition make them as general usage partitions .
* after installing XP , install Ubuntu . while installing choose the empty as installation partition and leave somespace(double of your RAM )for swap . and after that as usual . 

for more information look at this 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

