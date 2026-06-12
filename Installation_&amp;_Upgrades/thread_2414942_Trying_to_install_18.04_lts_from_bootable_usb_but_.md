---
title: "Trying to install 18.04 lts from bootable usb but screen keeps rotating"
date: 2019-03-17
forum: Installation &amp; Upgrades
---

### Post by AlyssaVS on 2019-03-17
I have been looking for this solution everywhere. The problem is that all of the solutions are for a system already installed. It is super frustrating trying to get this done. I've never had a version do this before. What can I do?

---

### Post by Autodave on 2019-03-17
What exactly are you trying to do?  Set up dual boot?  Single boot?  What is already installed?  Some specs on your machine would probably help, also.

---

### Post by AlyssaVS on 2019-03-17
This machine was in a dual partition before with Windows 7. I had just upgraded the Ubuntu side from 16.04 to 18.04 but the upgrade had several problems including the screen rotating arbitrarily. I decided to try a fresh install of ubuntu 18.04. So I backed up everything important, created a bootable usb from the startup disk creator, went to the windows side, created a repair disk and then went into windows disk manager and deleted the linux partitions. I didn't adjust the Windows partitions leaving the same amount of partition space for the fresh ubuntu install. The USB boots and the install starts like normal and then it suddenly rotates and it's hell to navigate. I tried to attach a pic of what the screen looks like but after uploading it here I can't find it.

I don't have all the specs memorized but it's an HP ProBook 450 G2, the hard drive is ATA Intel SSDSC2BB01.

---

### Post by Rick St. George on 2019-03-18
As a side note ... did you delete the linux partition or everything in the partition? Did the install take you through the steps to create the partition in unused space? Did you make it ext3? 

The screen acting funny .. is it temporary? As the install configs the video driver you will see video anamolies.  

Here some good notes for upgrading to v18.04 [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes) 

Moreover, there have multiple problems with people ugrading to v18.04. I suggest you Re-install v16.04, and wait till they fix all the problems!
For example, my prev. msgs. unanswered  [https://ubuntuforums.org/showthread.php?t=2414508](https://ubuntuforums.org/showthread.php?t=2414508) and [https://ubuntuforums.org/showthread.php?t=2411324](https://ubuntuforums.org/showthread.php?t=2411324) also scrolling in the category and look at Subject Headings for all the people suffering with the upgrade to v18.04.

Just saying !!! If you do get it up with v18.04, you'll probably have to deal with NetPlan. Canonical reconfigured the way internet interface.
See for explanations and instructions. [https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)  

Hope this helps!

---

