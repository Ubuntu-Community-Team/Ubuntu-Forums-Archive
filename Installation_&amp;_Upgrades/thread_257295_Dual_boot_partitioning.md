---
title: "Dual boot partitioning"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by jetsetlemming on 2006-09-14
I want to install Ubuntu on my Hard Drive, without erasing or damaging my windows OS or current files on my hard drive (I've already made 8 backup CD-R's of various things just in case). So, I have to make resize my current partition, and make a new one for Ubuntu, and, apparently, a third one of 500 MB... for some reason. How do I set up these two new partitions with the Ubuntu installation manual partition manager? What file system should they be? I read in the guides ubuntu doesn't like NTSF. How big should they be? Should I set them as "Primary partition"s or "Extended Partition"s? How do I make Ubuntu install in the new partition instead of overtop windows? Any help would be greatly appreciated, as well as any other advice with installation for dual booting ubuntu and windows. 
Thanks in advance.

---

### Post by moore.bryan on 2006-09-14
*a good way is to subtract the 500mb (for swap... swap is kind-of a virtual ram for spill-over) from the overall size of your drive and divide by two.  that'll give you equal size windows and ubuntu spaces... the partitioning guide will walk you through the whole process.  ext3 is what i chose and ubuntu will know not to put itself on top of windows.*

---

### Post by jetsetlemming on 2006-09-14
Thanks. What about the primary partition and extended partition setting? It defaults to "primary partition", and no one's mentioned it in any of the threads I've looked in or installation guides, so I think it should be left that, but I'd rather not take chances with something as major as changing the makeup of my hard drive.

---

### Post by moore.bryan on 2006-09-14
*swap will be put in extended, by itself, and ubuntu will go primary.*

---

