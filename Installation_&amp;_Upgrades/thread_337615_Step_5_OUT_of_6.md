---
title: "Step 5 OUT of 6"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Drive By on 2007-01-13
Well first off, Hello :).. how you all doing?..

Ok, I am new with _Ubuntu_, I burned it onto CD & having trouble installing it, When _Ubuntu_ loads up an im at the *Desktop*, I press the Install icon on the *Desktop*, I go threw the steps untill step 5, Which is the "**Partition**" step, i leave it at 50% an press the **Forward** button, I left my computer on so it can install untill the morning, But nothing has happend nearly 10 hours have past.. So can anybody help.. 

Thanks alot..

---

### Post by matthew on 2007-01-13
I moved this thread to a more appropriate forum. Someone should give you some pointers here. There is obviously something gone wrong for you as this is not normal. I can usually do a complete installation in 35-40 minutes start to finish.

To help out, please describe your computer hardware more completely. There could be a problem there. It could also just be a freak error and trying again from scratch might just work.

---

### Post by taurus on 2007-01-13
Maybe this helps.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Drive By on 2007-01-13
> **matthew said:**
> I moved this thread to a more appropriate forum. Someone should give you some pointers here. There is obviously something gone wrong for you as this is not normal. I can usually do a complete installation in 35-40 minutes start to finish.

To help out, please describe your computer hardware more completely. There could be a problem there. It could also just be a freak error and trying again from scratch might just work.

Ah sorry, Wont do it again next time ;)..

Well this is my system, [http://img169.imageshack.us/img169/9308/mysystemgq6.jpg](http://img169.imageshack.us/img169/9308/mysystemgq6.jpg)

Hope it helps.

---

### Post by Drive By on 2007-01-13
> **taurus said:**
> Maybe this helps.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

This site just tells me what partitioning is, An its to long to read i am abit lazy :twisted: :twisted: .. Well i took a photo yesterday when i was installing: [http://img79.imageshack.us/img79/6364/photo0037qw8.jpg](http://img79.imageshack.us/img79/6364/photo0037qw8.jpg)            It just stays like this all the time nothing eles happens

---

### Post by icefaerie on 2007-01-13
You could try partitioning before you do the actual install.  From the System menu, go to the Administration menu and click on the Gnome Partition Editor.  From here you can partition as you would have during the actual install and make sure everything goes okay with the partitioning before actually installing.  The guide taurus linked to should help you plan your partitions.

Once you finish partitioning, you can just go through the install.  When you get to the partitioning step, once again select "Manually edit the partitions" as opposed to erasing the whole drive, as yo already have your partitions set up.  Then you can assign the partitions to the right locations.

---

### Post by Drive By on 2007-01-13
> **icefaerie said:**
> You could try partitioning before you do the actual install.  From the System menu, go to the Administration menu and click on the Gnome Partition Editor.  From here you can partition as you would have during the actual install and make sure everything goes okay with the partitioning before actually installing.  The guide taurus linked to should help you plan your partitions.

Once you finish partitioning, you can just go through the install.  When you get to the partitioning step, once again select "Manually edit the partitions" as opposed to erasing the whole drive, as yo already have your partitions set up.  Then you can assign the partitions to the right locations.

Well I tryed i don't know what i am doing wrong.. I took 2 Photos so maybe you know what I am doing wrong.. 

[http://img74.imageshack.us/img74/2773/photo0038rp1.jpg](http://img74.imageshack.us/img74/2773/photo0038rp1.jpg)

[http://img74.imageshack.us/img74/2469/photo0039uy1.jpg](http://img74.imageshack.us/img74/2469/photo0039uy1.jpg)

Hope you can help. Thanks

---

### Post by ENN0 on 2007-01-13
i had the exact same problem..i used edgy and i just gave up and burnt dapper drake and it installed fine...i then installed edgy trough dapper drake and it works fine!

---

### Post by Drive By on 2007-01-14
> **ENN0 said:**
> i had the exact same problem..i used edgy and i just gave up and burnt dapper drake and it installed fine...i then installed edgy trough dapper drake and it works fine!

Hey, Is dapper drake the same? as Ubuntu... because i am new at this Ubuntu linux thing.. So  there is no other way to fix my problem... and i need to download dapper?.. an what is edgy.. 

Thanks

---

### Post by icefaerie on 2007-01-14
Drive By, Edgy and Dapper are nicknames for the different versions of Ubuntu.  The most recent version is 6.10, also known as "Edgy Eft" or "Edgy" for short.  The previous version is 6.06 or "Dapper Drake"/"Dapper."

I would recommend trying a Dapper (6.06) install CD.  Those seem to work a lot better than the Edgy CDs for many people (myself included!).  If you can successfully install with the Dapper CD, then you can upgrade to Edgy later.

---

### Post by tredegar on 2007-01-14
Drive By,
Your screenshots shou the install is failing at "Resize Partition", the very first step.
How much free space does your windows drive have? Currently it is about 120GB, and you are trying to resize it to 60GB. You cannot do this is the disk is more than half full! 
If you do have >60GB free, then you might try defragging your windows disk before attempting to resize it.

---

### Post by Drive By on 2007-01-14
> **icefaerie said:**
> Drive By, Edgy and Dapper are nicknames for the different versions of Ubuntu.  The most recent version is 6.10, also known as "Edgy Eft" or "Edgy" for short.  The previous version is 6.06 or "Dapper Drake"/"Dapper."

I would recommend trying a Dapper (6.06) install CD.  Those seem to work a lot better than the Edgy CDs for many people (myself included!).  If you can successfully install with the Dapper CD, then you can upgrade to Edgy later.

Oh i see, I will try installing Dapper. 

Thanks

---

### Post by Drive By on 2007-01-14
> **tredegar said:**
> Drive By,
Your screenshots shou the install is failing at "Resize Partition", the very first step.
How much free space does your windows drive have? Currently it is about 120GB, and you are trying to resize it to 60GB. You cannot do this is the disk is more than half full! 
If you do have >60GB free, then you might try defragging your windows disk before attempting to resize it.

Well i have alot of free space because 1 week ago i have installed windows xp.. 98.3GB of free space

---

### Post by Bartender on 2007-01-14
It sounds like you have broadband.  If so, download [GPLCD]("http://gparted.sourceforge.net/livecd.php") and burn to a CD just like the Ubuntu CD's.  It's kinda the same as the partitioner you've already been using within the install CD, but it just works better.  Make your ext3 and swap partitions with GPLCD, then toss in the Ubuntu CD.  Mount / to the ext3 partition and swap to the "linuxswap" partition.  Linuxswap doesn't have to be any bigger than 1GiB.

And I'd sure recommend going back thru aysiu's website and reading it.  Telling us that you're lazy doesn't exactly impress anyone.  aysiu put a lot of work into his guides and you would do well to spend some time there absorbing knowledge.  Proceeding down the path you're on with a threadbare grasp of the fundamentals is asking for trouble. 

Defrag Windows 3 or 4X and take a look at the final results.  Make sure you're not bumping up against Windows data when you're trying to resize the NTFS partition!

If you use GPLCD first you may have to go the "manually partition" route, which means you'll have to understand mount points.

EDIT:  I see you stacked up jobs within the partitioner.  Don't do that.  Complete one task at a time, as per the recommendations by GParted developers.

---

### Post by Drive By on 2007-01-14
Ah, I am realy stuck on what to do.. :(.. So can't i just like half the partition thing so i can have windows an ubuntu on it, Its so much trouble i fort it was a easy installation

Its such a long process an i am not realy good with pc stuff an i dont understand

---

### Post by icefaerie on 2007-01-14
> **Drive By said:**
> Ah, I am realy stuck on what to do.. :(.. So can't i just like half the partition thing so i can have windows an ubuntu on it, Its so much trouble i fort it was a easy installation

Its such a long process an i am not realy good with pc stuff an i dont understand

You can dual boot!  It's just a little trickier to set up the partitions.  First, in Windows, [defragment]("http://www.geekgirls.com/windows_defrag.htm") your hard drive a good 3 or 4 times.  This will move any files away from the end of the hard drive and towards the beginning.  This will make it more likely that your partitioning will succeed.

Then you can partition your hard drive.  There are several options.  You can use GParted/Gnome Partition Editor on the Ubuntu Live CD (or QTParted on Kubuntu).  There is also a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") that you can boot into just to partition your hard drive.

What does this accomplish?  Well, it creates separate sections of your hard drive for different operating systems, so you can choose to boot into either Windows or Linux from the same physical hard drive.  But by partitioning, you essentially break up your hard drive, so the computer sees a few different "hard drives."

Now, for the partitioning.  Most likely your hard drive is formatted as NTFS, a Windows file system.  First, you will need to resize your Windows partition to a smaller size to leave room for other things.  Then, you can add a FAT32 partition.  The good thing about the FAT32 partition is that both Linux and Windows can natively read and write to it!  You'll be able to access files on it from both Windows and Linux.  Then you can have a partition for Ubuntu using a file system like ext3 or resierfs.  There is a guide to partitioning somewhere, but I don't have the link to it.  Maybe someone else knows what I mean.

Hopefully, you were able to partition everything.  If it worked, then you know you're ready and able to proceed with the install!

I know this was long.  I hope it helped a bit.

---

### Post by Drive By on 2007-01-15
> **icefaerie said:**
> You can dual boot!  It's just a little trickier to set up the partitions.  First, in Windows, [defragment]("http://www.geekgirls.com/windows_defrag.htm") your hard drive a good 3 or 4 times.  This will move any files away from the end of the hard drive and towards the beginning.  This will make it more likely that your partitioning will succeed.

Then you can partition your hard drive.  There are several options.  You can use GParted/Gnome Partition Editor on the Ubuntu Live CD (or QTParted on Kubuntu).  There is also a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") that you can boot into just to partition your hard drive.

What does this accomplish?  Well, it creates separate sections of your hard drive for different operating systems, so you can choose to boot into either Windows or Linux from the same physical hard drive.  But by partitioning, you essentially break up your hard drive, so the computer sees a few different "hard drives."

Now, for the partitioning.  Most likely your hard drive is formatted as NTFS, a Windows file system.  First, you will need to resize your Windows partition to a smaller size to leave room for other things.  Then, you can add a FAT32 partition.  The good thing about the FAT32 partition is that both Linux and Windows can natively read and write to it!  You'll be able to access files on it from both Windows and Linux.  Then you can have a partition for Ubuntu using a file system like ext3 or resierfs.  There is a guide to partitioning somewhere, but I don't have the link to it.  Maybe someone else knows what I mean.

Hopefully, you were able to partition everything.  If it worked, then you know you're ready and able to proceed with the install!

I know this was long.  I hope it helped a bit.

Hey bro thanks, but on Gnome Partition Editor what do i make the normal windows hard drive gb to ? its like 111GB now so what should i make it to? thats what im stuck on to.. so its 111 now can't i make it like 60gb then the rest can be for Ubuntu.. i tryed it before but i got a error so what would u recomend?.. Thanks

---

### Post by Drive By on 2007-01-16
I have download a program called partition magic, So i need to partition my drive into 2 more peices?.. a FAT and a ext3?

---

