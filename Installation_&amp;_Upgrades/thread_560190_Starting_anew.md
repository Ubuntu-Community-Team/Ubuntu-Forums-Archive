---
title: "Starting anew"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by Denizen08 on 2007-09-26
I want to reinstall ubuntu in a clean slate. Unfortunately I cant completely reformat ext3. How do I do this? Are there tools to be able to do this?

---

### Post by rsambuca on 2007-09-26
Just install overtop of your existing partition, and make sure you select the reformat option on the installation CD.  This will "wipe the slate clean" for you.

---

### Post by Denizen08 on 2007-09-26
I am doing that. The problem is the installer is able to find the previous ubuntu install during the installation of system files and considers it an unclean installation. It then aborts at that stage.

I need to wipe clean the partition, maybe even rewrite the 'obsolete' partition with a lot of zeroes. But I dont really know how to do this.

---

### Post by rsambuca on 2007-09-26
> **Denizen08 said:**
> I am doing that. The problem is the installer is able to find the previous ubuntu install during the installation of system files and considers it an unclean installation. It then aborts at that stage.

I need to wipe clean the partition, maybe even rewrite the 'obsolete' partition with a lot of zeroes. But I dont really know how to do this.

This shouldn't happen because the format should occur first.  I am afraid you are doing something wrong.

---

### Post by Denizen08 on 2007-09-26
Ok. I know it should but then I really dont know how to know if it works. All I know is it rejects installation on Ext3 file system even if 'reformat' is set. Despite this I am able to install it on ext2.

Anyway, I'll try going at it again later tonight as I am at school right now. BRB, I still have classes ><.

But if all else fails is there a tool I can use to wipe just a specific section of the hard disk and avoid a 'usable' partition such as where my Windows install is on. (btw I am dual booting)

---

### Post by dj Kalma on 2007-09-26
> **Denizen08 said:**
> But if all else fails is there a tool I can use to wipe just a specific section of the hard disk and avoid a 'usable' partition such as where my Windows install is on. (btw I am dual booting)

You can use gparted to fiddle around with the partitions. Just get gparted, burn it to a CD and boot from that.

---

### Post by Denizen08 on 2007-09-27
> **rsambuca said:**
> Just install overtop of your existing partition, and make sure you select the reformat option on the installation CD.  This will "wipe the slate clean" for you.


I think I found whats wrong/lacking with the operation and why the install is able to find the 'obsolete' install and considers it an unclean installation when installing:
Facts:
My initial installation was on ext3 file system and I want to reinstall on a 'clean' ext3 file system. Considering the fact that ext3 is a journaling file system (see [http://en.wikipedia.org/wiki/Ext3);](http://en.wikipedia.org/wiki/Ext3);) Ext3 is resilient to the quick reformatting method of just deleting the headers of data on a disk, which is what the installer does for a quick reformat.
Hypothesis:
Since I want to reinstall ubuntu on ext3 file system again, but this time on a clean one, it is able to identify the 'obsolete data' which was supposedly removed from the formatting stage of the install. It then tells me that it can't install because it is 'unclean'.

---

### Post by rsambuca on 2007-09-27
> **Denizen08 said:**
> Hypothesis:
Since I want to reinstall ubuntu on ext3 file system again, but this time on a clean one, it is able to identify the 'obsolete data' which was supposedly removed from the formatting stage of the install. It then tells me that it can't install because it is 'unclean'.

Sorry.  If you are doing the installation correctly it will not see the old files.  I routinely test different distros and have never had this happen.  

Questions:

What iso are you installing from?
Did you check the md5sum of the iso prior to burining?
Did you burn the iso as an image file (not data cd)?
Did you check the CD for defects prior to trying the installtion?
Are you using the alternate or liveCD?
Have you tried just using the gparted livecd to reformat first?

---

### Post by Denizen08 on 2007-09-27
> **rsambuca said:**
> 
What iso are you installing from? Are you using the alternate or liveCD?


I am using the Alternative ISO for ubuntu fiesty fawn (7.04).

> **rsambuca said:**
> 
Did you check the md5sum of the iso prior to burining?
Did you burn the iso as an image file (not data cd)?
Did you check the CD for defects prior to trying the installtion?


I burnt it as a data disk (as it is, using Nero 7), unfortunately I did not check the md5sum of the iso before burning it. But I did run an integrity check of the disk afterwards and everything went well enough. As for the disk itself, it has no physical defects what so ever.

> **rsambuca said:**
> 
Have you tried just using the gparted livecd to reformat first?


I haven't tried it yet, but will be soon, when I get the free time. About gparted, will it be able to format it properly? I dont mind the wait if it might take the entire day...

Btw, thanks for the correspondence.

---

