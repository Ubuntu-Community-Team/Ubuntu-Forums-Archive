---
title: "Windows XP drive unavailable in Ubuntu"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by vlceks on 2006-10-23
Hi ALL,

Several months ago, I installed Ubuntu Dapper Drake on my system as a dual OS along with windows XP.  My Windows partition was available to me IN Ubuntu; I could actually see evrything I had on Windows.  There was even an icon on my Ubuntu desktop for my Windows partition.  

Recently, I have had to reformat my HD and reinstall Windows AND Unbuntu, only this time the icon was missing and I was unable to access my Windows parition.  When I tried to mount this parition, I get the following error messsage:

Unable to mount selected volume

error: device /dev/hda1 is not removable
error: could not execute pmount


Thanks for all help.

---

### Post by meng on 2006-10-23
You'll need to edit the /etc/fstab
Look here for help:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

