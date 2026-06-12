---
title: "installing ubuntu alongside windows on hp laptop"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by tdk93 on 2013-06-01
I know this question has been raised several times about HP laptop having four primary partition.
The trouble is that most of the solutions suggest deleting HP_TOOLS partition while at the HP official site it is termed the worst solution.
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/m-p/2179093#M53334](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/m-p/2179093#M53334)

Can someone suggest me what to do?

---

### Post by fantab on 2013-06-01
Is this a new Laptop with Windows8? If it is then it is very likely that you have UEFI mode set. And for this to be possible you will have GUID Partition Table [GPT]. With GPT you can have more than 100 Primary Partitions. You may not have to delete any partition. Just create some space by SHRINKING any large partition to create space for UBUNTU. Confirm this, its important.

You can ignore the warning @ HP official site. HP Tools are nothing but bloatware IMO. However it will be a good idea to make a complete backup of your Hard Disk and its partitions: 
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710) (Read the post by Mark Phelps and the tool he is talking about is [**HERE**]("http://www.macrium.com/reflectfree.aspx"))

---

### Post by Mark Phelps on 2013-06-01
My suggestion is to go into Windows Explorer and copy the entire contents of the HP_TOOLS partition to a directory on your drive.  That way, you have the tools if you need them later and, if you don't, you can always remove them and recovery the disk space.

---

