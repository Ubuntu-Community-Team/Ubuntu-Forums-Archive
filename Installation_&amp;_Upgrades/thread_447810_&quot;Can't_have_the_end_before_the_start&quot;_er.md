---
title: "&quot;Can't have the end before the start&quot; err message when partitioning."
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by sonnet on 2007-05-18
As per title I'm getting this weird error message when partitioning during the installation process.
I'm trying to create 2 primary partiton and a third logical partition using the residual space .
But when I go to create the logical partition selecting all the residual space I'm getting this weird error message :"Can't have the end before the start".
Even if I use little lesser space I get the same error message.
Even if I select as another primary.
So the problem is that doesn't allow me to use alle the hd space.
Does anyone have any suggestion or tips?

---

### Post by merlinus on 2007-05-18
I may be mistaken, but my understanding is that secondary partitions are actually part of a primary partition.  So perhaps your secondary partition needs to be created as part of your second primary???

-merlin

---

### Post by Wim Sturkenboom on 2007-05-18
Did you create an extended partition? Logical partitions are held in the extended partition.

---

### Post by sonnet on 2007-05-18
Not sorry I didn't explain enough the problem.
I have one hard disk.
So first I create 2 primary partition say one of 10 and the second of 15 gb.
Until now everything is fine.
The I have say 100gb of free space left.
I want create another partition,a logical partition so that I can create on that other extended partition.
The problem is that when I'm going to create this 3rd partition using the residual FREE space I get the error message i wrote above.

---

### Post by louieb on 2007-05-18
> **Wim Sturkenboom said:**
> Did you create an extended partition? Logical partitions are held in the extended partition.

> **sonnet said:**
> Not sorry I didn't explain enough the problem.
IThe I have say 100gb of free space left.
I want create another partition,a logical partition so that I can create on that other extended partition.

W.S. has it right. Create an extended partition : use the whole 100 gig.
once thats done. You create logical  partition(s) inside the extended one.
 [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")  
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

