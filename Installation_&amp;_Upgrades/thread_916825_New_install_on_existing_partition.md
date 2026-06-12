---
title: "New install on existing partition"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by rrumaner on 2008-09-11
I am about to jump headfirst into the world of Ubuntu but before I step off the edge and install it I have a question.

I have a C drive (duh) and do not understand the part about installing Ubuntu to it in a partition. I do not currently have any partitions on the drive and want to do dual boot. Still have to allow Windows to boot as usual.

Does the installer reformat the entire drive when it partitions it or does it just 'slice' off a piece and format that? 

I  guess my concern is that I will end up formatting my entire C drive and lose everything in the process. Am I missing something or does is this a real concern?

I also have an empty USB External drive with 160 gig free. I tried to install to that originally but received an error. 

Failed to create a file system. The ext3 file system creation in partition #1 of SCSI8 (0,0,0) (sfd) failed

Does this mean I cannot install Ubuntu to the external drive?

---

### Post by oldos2er on 2008-09-11
> **rrumaner said:**
> 
Does the installer reformat the entire drive when it partitions it or does it just 'slice' off a piece and format that? 
  

 It can do either of those things, depending on what you tell it to do. I suggest you backup any data you wish to keep before installing Ubuntu, just to be safe.

 How much free space do you have in your Windows partition? it's suggested to run Windows' defrag program more than once before installing Ubuntu; and if you're running Vista, you'll want to use its disk partitioner program to carve out a partition prior to install Ubuntu.

Read [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

