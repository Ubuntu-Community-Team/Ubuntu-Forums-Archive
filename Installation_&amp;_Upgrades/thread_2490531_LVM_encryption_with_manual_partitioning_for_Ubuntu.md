---
title: "LVM encryption with manual partitioning for Ubuntu 23.04"
date: 2023-09-06
forum: Installation &amp; Upgrades
---

### Post by homurawasframed on 2023-09-06
Is there a way to LVM encrypt a volume when choosing manual  partitioning in Ubuntu 23.04? 

I only see an encrypted volume if I let  Ubuntu decide my partition tables for me:

[IMG]https://imgur.com/C2NKCUb.jpg[/IMG]


 

 If I select manual partitioning, there does not appear to be a way to achieve encryption. Screenshots in the installer:

 [URL="https://i.stack.imgur.com/0Ynr7.jpg"][IMG]https://imgur.com/jkl7NUl.png[/IMG]
[/URL]

 In the old installer there would be an option to add to encrypted volume, this doesn't exist in 23.04:

 
[IMG]https://imgur.com/VIgZFLm.jpg[/IMG]



 Editing a proposed partition shows new options, but not encryption:
[IMG]https://imgur.com/9AC9jwq.jpg[/IMG]

 

 Summary of proposed partitions again shows no option for encryption. I can only go back or Install.

 
[IMG]https://imgur.com/HMlCQ8B.jpg[/IMG]


 

**I'd strongly prefer doing this with GUI rather than encrypting via command line after the fact.**



 **Apples and oranges**, but in RHEL I'm able to check a box with the  manual partition method and it encrypts the partitions with one step:


 [IMG]https://imgur.com/tyG2YVV.jpg[/IMG]

---

### Post by MAFoElffen on 2023-09-06
No. The partitioner in that Installer is not File system, nor file manager aware.

With previous installers, we would jump out to the system to get to a terminal session or a command prompt in a vtty, set up LUKS, LVM, mdadm, etc... Then toggle back to the installer... Start the partitoner, to connect the mounts to what is there, then continue the install. The new installer's partition not being file system / file manager aware prevents that possibility.  

Join this bug: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

---

