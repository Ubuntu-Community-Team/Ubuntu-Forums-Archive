---
title: "Attention!  Intrepid Ibex - Installation note for all acronis users!!!"
date: 2008-08-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by applecookie on 2008-08-24
Hello.

Maybe here are some other users of the tool "acronis trueimage", which I use to make images of my current installation.

When you install "intrepid ibex", you will have to take care of the following case:

You need to make the partitioning before you install intrepid - for example with a gparted live cd - and also format them with another program. Then, you can install intrepid, but take care not to check the "format" checkbox for the partitions, you want intrepid to be installed on! Intrepid can be installed on clean partitions without formatting it another time - the maybe shown messagebox isn't important.
The reason for this is, that when you make a normal installation using the intrepid partition program to format it, acronis is not able to make an image of them anymore! It causes an error and acronis says, you have an invalid file system on it!

The reason for this error is, that till intrepid, ubuntu formats the ext3 - Partition with 128 I-Nodes. Intrepid (as also Mandriva 2008.1 and Mandriva 2009.0 where this problem also occurs) formats with 256 I-Nodes.
Acronis Trueimage (which in the safeboot version is a linux tool!) can only handle the old formatting-version of ext3-partition!

When you take care of this, you can use trueimage 11 to make image backups of your intrepid installation as I did.

Regards

applecookie

---

### Post by stinger30au on 2008-08-24
then tell acronis to fix their software so it reads the partitions correctly.

not an ubuntu fault by the sounds of it

---

### Post by applecookie on 2008-08-24
nice comment :-(

I never said, it's an ubuntu fault!!! I just wanted to warn the other users of this software. It's a fact, that acronis software has some bugs.

---

### Post by Jabes on 2008-09-24
> **stinger30au said:**
> 

not an ubuntu fault by the sounds of it

Regardless of whose fault it is, it is still a problem that I would like to know about.

Thanks for the heads up, applecookie.  I appreciate people posting their issues because it possibly saves me time and effort later.

---

### Post by night-wing on 2008-10-21
I must say: This seems also to be true with Trueimage 2009!

---

### Post by shane19174 on 2008-10-30
Thanks for the info, applecookie.

So does anyone know what to do, short of reformatting and reinstalling, if you have already installed Intrepid on partitions with the new formatting? Will the sector-for-sector method work?

Thanks for any ideas.

---

### Post by crjackson on 2008-10-30
Wow, thanks for the heads up. I would have ran into this problem later this week.

---

### Post by rbmorse on 2008-10-30
> **shane19174 said:**
> Thanks for the info, applecookie.

So does anyone know what to do, short of reformatting and reinstalling, if you have already installed Intrepid on partitions with the new formatting? Will the sector-for-sector method work?

Thanks for any ideas.

Sector backup from Acronis will still work, but it's bog slow. I've bitten the bullet and gone to partimage....actually "Clonezilla" which is a sort of GUI for Partimage and comes with SystemRescueCD -- which is always nice to have on hand.

---

### Post by shane19174 on 2008-10-30
> **rbmorse said:**
> Sector backup from Acronis will still work, but it's bog slow. I've bitten the bullet and gone to partimage....actually "Clonezilla" which is a sort of GUI for Partimage and comes with SystemRescueCD -- which is always nice to have on hand.

I'm doing a sector-by-sector backup now, and I see what you mean about it being slow...

About Clonezilla: I thought that was a separate project from SystemRescueCD. Don't both of them used Partimage? Or has Clonezilla been integrated into SystemRescueCD now? I haven't tested yet, but it looks like I'll have to. So how does it compare to Acronis in terms of speed, reliability, and the like?

Thanks

---

