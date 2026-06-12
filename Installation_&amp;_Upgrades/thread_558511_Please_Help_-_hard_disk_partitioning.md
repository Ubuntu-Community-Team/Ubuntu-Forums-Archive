---
title: "Please Help - hard disk partitioning"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by parallelogram on 2007-09-24
Here is picture of gparted - [URL="http://www.flickr.com/photos/quadcoreguy/1431105547/"]http://www.flickr.com/photos/quadcoreguy/1431105547/
[/URL]

I have a Maxtor 500GB. XP and Ubuntu/Kubuntu installed. Problem is that my hard disk has some extra space I want to use, but Gparted is not allowing me to create partition in unallocated space. It says "maximum 4 primary partitions only allowed". Is there any work around. Appreciate your help.

---

### Post by dabl on 2007-09-24
It is true that only 4 primary partitions are allowed, but that's not an impediment to doing what you want.

There's another problem, however.  The sizes of your "/" and "/home" partitions are exactly the opposite of what they should be, in my opinion. 9GB would be a reasonable, on the large size, for "/", and "/home" is for your data so it needs to be as large as possible.

So, can you click on the sda3 partition, and slide the right edge of it to the left, until it is down to maybe 7 or 8 GB in size, and then click on sda4 and expand it until it is filling up the rest of the disk? You should be able to just slide the edges of those partitions (in the top graphic) while viewing them (sequentially) in Gparted.  Gparted will generate the narrative of the changes, then when you click "apply" it will execute them.

Note that the execution of these changes may take multiple hours (like 4), so you might want to click "apply" right before you have something else to do.  :)

---

### Post by parallelogram on 2007-09-24
hey thanks. I'm gonna try the resizing tonight. 

But still my initial problem remains. I wasted 200gb disk space on a 500GB disk and the only way I can use it is if I cut down the number of existing primary partitions to less than 4. Again for this to happen, I believe I need to move the / and /home partitions I created for Linux inside the extended partition that is already existing. That way they cease to be primary partitions and I can create new partitions in the unallocated space. 

But is it possible. I mean how can I move two existing linux partitions (primary) under the existing extended partition

---

### Post by psusi on 2007-09-24
Why do you want more partitions?  Why not just make the ones you have larger?  And yes, you will need to create more extended partitions if you want more than 4, but it looks like your extended partition space is already used up, so you will have to delete partitions 3 and 4 and expand the extended partition to use up all of the remainder of the disk space.

---

### Post by dabl on 2007-09-24
> **parallelogram said:**
> 

But still my initial problem remains. I wasted 200gb disk space on a 500GB disk and the only way I can use it is if I cut down the number of existing primary partitions to less than 4.


Yikes -- I apparently wasn't writing clearly this morning. Let me try again.

You don't need MORE partitions, you need a BIGGER partition for "/home" and a SMALLER partition for "/".  That's what "resizing" means.

So, make sda3 SMALLER by (a) clicking on it in the GParted graphic (which will put a dashed border around it), and (b) sliding the right edge of it to the left until the size shown is 7GB.

Then make sda4 BIGGER by (a) clicking on it in the GParted graphic (which will put a dashed border around it), and (b) sliding the right edge of it all the way to the end of the hard drive at the right of the graphic.  This will use all the "unallocated" space that you are rightfully concerned about having wasted.

As a result of doing these steps, you will still have 4 partitions, but they will be using all of your hard drive, and your "/home" partition will be plenty big for all of those .wav or .jpeg files.

:)

---

### Post by parallelogram on 2007-09-24
Edit: Response to psusi

True. Infact.
 I am not particular about creating new partition. All I want to do is use the remaining space. 

Except for my work and the occasional gaming, I don't use Windows XP. 99% time I use Ubuntu. But in terms of reliability, I trust ntfs access from Ubuntu more than ext3 access from windows. Hence I store all my data - songs, movies,games etc on ntfs though I use linux all the time. 

So 400GB NTFS and 100GB ext3 is what I had in mind. Somebody told me that ntfs-3g has issues with large ntfs volumes. So I thought I'll split that 400GB into multiple NTFS partitions each under a 100GB. Thats why I mentioned creating new partition. desirable, but not necessary.

Whether I create new partition or not, I still want to use that unallocated space. Your recommendation seems the way to go. I can clone the / and /home partitions , then delete them, resize the extended partition and restore the cloned partitions under the extended partition. But I'm scared grub won't boot Ubuntu after that. gotta figure out...

---

### Post by parallelogram on 2007-09-24
Oh ok. I get your point. Yeah that is easy solution. Stupid of me to not think in that direction.

I try to keep all my data in NTFS though I use Linux primarily (as I mentioned in previous post). But considering the overhead involved (deleting / recreating partitions etc) to get there from this state, I think I will make an exception and follow your advice. Time saver and not risky. Thanks

---

### Post by psusi on 2007-09-24
Yes, you will have to reinstall grub, but that is fairly simple.

---

### Post by parallelogram on 2007-09-26
It took a very long time with the gparted live cd. But I am better now
Before resize I moved the partitions. So disk looks like [http://flickr.com/photos/quadcoreguy/1444009306/]("http://flickr.com/photos/quadcoreguy/1444009306/") now

@dabl - One of the reasons I kept home folder small is because all I store all my data in NTFS for easy access from ubuntu and windows. But now I have this doubt. Does it affect performance. ie when I do video encoding or download a big file, does it matter that I am reading/writing from ntfs as opposed to ext3. Does it impact performance in any way?
Also when I install new software doesn't it take up space on the root partition. Thats why I kept it 60 gb. Please correct me if I'm wrong

@psusi - I would really like to move sda3 and sda4 under the extended partition so that they are physically close to the swap partition. Can you please suggest how to make grub still boot Ubuntu after this change? 

Thanks...

---

### Post by psusi on 2007-09-26
You will need to reinstall grub any time you manipulate the partition which contains /boot.  As for changing a partition from primary to extended, I don't think that gparted can do that so you will just have to back up the files, delete it, and extend the extended partition to use up that space before creating a new extended partition and putting the files back.

---

### Post by parallelogram on 2007-09-27
was planning to use "copy partition to make copies inside the extended" and then delete the outside primary / and /home.

If that is not possible then I'll image the partition and restore using Acronis True Image.

---

### Post by dabl on 2007-09-27
I don't think the filesystem format is a huge factor in performance of your system.  I use reiserfs myself -- it takes longer to boot up, but seems to be more resilient under hard crash/power outage conditions -- I haven't lost any data no matter how bad I abuse it.

But, NTFS and ext3 are also reasonable choices, and lots of folks use them.  :)

---

