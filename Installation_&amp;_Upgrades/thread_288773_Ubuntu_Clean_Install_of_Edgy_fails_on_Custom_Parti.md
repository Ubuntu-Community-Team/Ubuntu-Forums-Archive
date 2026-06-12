---
title: "Ubuntu Clean Install of Edgy fails on Custom Partitioning"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by VinnyM69 on 2006-10-30
I've tried doing a clean install (X86 - AMD Duron) with the Live CD and can't get past the custom partitioning screen.  I have a root partition set up as the first partition on the disk where I do the install and then a swap partition and finally a home partition.  The root and swap partitions are to be formatted and the home partition is not re-formatted.  When I get to the custom partitioning screen to set this up it is not recognizing that I have set up a root partition.  Gives me an error about no root partition being set up.  I'm an experienced Linux user and have done many installs of prior releases of Ubuntu with the custom partitioning with no problems.  Anybody have any ideas or suggestions?  I'm back on Dapper now, but would really love to get Edgy to install.  

TIA!  :confused:

---

### Post by xcity on 2006-10-30
You are not the only person who are seeing this problem. I installed ubuntu in my home notebook, which is fine. But when I installed edgy in my office notebook, I saw exactly what you experienced. My temp solution is by deleting  your home partition, then create it again. 

After that, this edgy can find it.You can continue your installation.

---

### Post by cius on 2006-10-30
I did not get that far into the install process.  I had bizarre behaviors on booting the live cd and ran into a small problem with the partitioner that effectively turned me off to the idea of upgrading to Edgy.  My problem was that I could not figure out how to tell the partitioner to mount my existing partitions.  In Dapper's isntaller, it was simple, I just told the installer to format my root partition and not to format my home partition, just mount it at /home.  When I booted into the Edgy live cd though, it would allow me to delete partitions and recreate them, but there was no obvious way to tell it where to mount my existing partitions or which ones to format.  I decided that its best to simply wait until 7.04 or atleast until I get reports of a more stable system.  Until then, I'm fine using Dapper.  :)

---

### Post by VinnyM69 on 2006-10-30
That is the same problem I'm having.  I guess I could delete the root & swap partitions that I already have set up under Dapper and then redefine them.  I am not deleting the /home partition, because it houses all my user files and I don't have a back up solution.  I suppose I could just do the install with the root and swap partitions and then mount the home partition after the install.  But I think I'll just wait until they get the installer fixed.  It seems strange that the custom partitioning install was working fine in Dapper and now it's broke.  The screen looks the same, but obviously something has changed "under the covers".

---

### Post by VinnyM69 on 2006-10-30
Installed ok after doing the manual partitioning and deleting and re-adding the previous root partition I had under Dapper.  This is a known issue.  I hadn't bothered to read the known issues before installing, duh!

---

