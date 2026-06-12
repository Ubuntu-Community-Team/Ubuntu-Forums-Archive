---
title: "Discovered that my disk is dynamic  Can I install ubuntu ?"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by A7med on 2010-10-17
Hello , 
I bought my laptop with Win 7 pre-installed and I shrinked a partition and created a free unallocated space , but when I was installing ubuntu It called this space "unusable" . So I started reading a bit and found that My disk is a dynamic disk and that's different from the basic disk so It doesn't have primary or logical disks ( Am I right ?) . I still want to install ubuntu what should I do ?

---

### Post by A7med on 2010-10-17
Btw , I read a solution where I must convert my disk to basic and that Sucks ! Any other solution ?

---

### Post by mordoc on 2010-10-17
> **A7med said:**
> Hello , 
I bought my laptop with Win 7 pre-installed and I shrinked a partition and created a free unallocated space , but when I was installing ubuntu It called this space "unusable" . So I started reading a bit and found that My disk is a dynamic disk and that's different from the basic disk so It doesn't have primary or logical disks ( Am I right ?) . I still want to install ubuntu what should I do ?

Here's an article from Technet on converting dynamic disks back to a basic disk:

[http://technet.microsoft.com/en-us/library/cc755238.aspx](http://technet.microsoft.com/en-us/library/cc755238.aspx)

---

### Post by srs5694 on 2010-10-18
I've never used it, but the main Web page for [Partition Wizard](http://www.partitionwizard.com) claims to be able to convert a dynamic disk to a basic disk without data loss.

Alternatively, you could wipe everything and re-install Windows; however, many computers come with crippled system restore tools that will only restore the disk to its original state, so you might end up back in the same boat. Maybe the manufacturer's tech support line would have a suggestion (but I wouldn't hold out high hopes for that).

Whatever you do, *be sure you've got recovery DVDs before you proceed!* Most (all?) manufacturers have gotten incredibly cheap and are shipping system restore software on the main hard disk, which of course is useless if the disk hardware or recovery partition is badly damaged. There's usually a utility to create your own DVDs, so you should run it. (Create two sets for safety.) While you're serving as a human disc-changer for the computer, try writing a letter to the manufacturer and Microsoft telling them how cheap you think they are. They'll keep pulling this sort of nonsense unless enough people complain.

---

