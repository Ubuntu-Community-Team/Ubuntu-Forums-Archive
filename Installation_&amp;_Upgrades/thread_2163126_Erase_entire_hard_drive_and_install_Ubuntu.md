---
title: "Erase entire hard drive and install Ubuntu"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2013-07-17
I have a Dell laptop with Windows 8 installed.
There are a total of five different partitions.
I want to delete everything on the hard disk and install Ubuntu 13.04. 
I do not want a dual load capability.
I see that there is an option to do this when installing Ubuntu.
Here's my concern: When I install Ubuntu, using the entire disk option, will all of these five now existing partitions be deleted or will I end up with part of my hard disk holding on to some of those not wanted partitions.
I really don't want that to happen, so can somebody let me know if I'm good to go or not.
Thank you

---

### Post by dino99 on 2013-07-17
im not a fan to let ubiquity doing its own stuff, as it cant know my real needs. So i always do it manually, following that thread:
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

in your case, you should set a primary partition and an extended one where you then can create other partitions

---

### Post by sudodus on 2013-07-17
It is enough to install with the ***entire disk option***, which is the simplest one to run. But the data remain on the hard disk, so many of the files can be recovered with special tools like PhotoRec unless overwritten by new data. If this is OK, just go ahead. 

Which this option there will be two partitions, the Ubuntu root partition and a small swap partition. All Windows partitions will be deleted from the partition table.

*Edit*: But as *dino99* wrote, if you want more control, do the partitioning manually, before you install Ubuntu.

---

### Post by thelugnut on 2013-07-17
much obliged for the replies...
I shall follow the  sage advice from both of you, and mark this thread as solved.:)

---

### Post by cybrsaylr on 2013-07-17
Agree if you don't care about Windows just install Ubuntu with the entire disk option, which is the easiest install to do.

---

