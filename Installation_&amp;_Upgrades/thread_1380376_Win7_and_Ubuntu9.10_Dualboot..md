---
title: "Win7 and Ubuntu9.10 Dualboot."
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by jakeeee on 2010-01-13
Apologys if I've posted this in the wrong section.
So i currently have windows 7 installed.
I wanna dual boot Ubuntu 9.10 with it.

Where should i save my music at?
I'll want to acsess it on both operating systems.

Should i create a seperate patition for things like that?

Please reply :D

---

### Post by darkod on 2010-01-13
Ubuntu can read ntfs partitions, so even if you leave your music on C: (assuming it's there right now), it will be able to read it. However, just as precaution, I wouldn't be accessing the windows system partition too often from ubuntu.
If you have the opportunity to create another ntfs partition and place your music there, I would do that. That way you can access it both from windows and ubuntu, and at the same time ubuntu is not accessing the windows system partition too often.

---

### Post by latenightrob on 2010-01-13
I set my system up follow the article in Lifehacker.com "dual boot win7 and ubuntu in perfect harmony" it explains how to create a storage drive that both ubuntu and windows can share.

---

### Post by jakeeee on 2010-01-13
That guide is pretty good :)
Thanks.
But how big should i set my storage partition if i have a total of 150gb HDD?

---

### Post by darkod on 2010-01-13
> **jakeeee said:**
> That guide is pretty good :)
Thanks.
But how big should i set my storage partition if i have a total of 150gb HDD?

That depends entirely on you and how much data you plan to put there. Have in mind that you also need enough space on the system partition for windows and programs.

---

### Post by wkulecz on 2010-01-13
If you have anything you want on your Win 7 system back it up before you install 9.10.

Installing Kubuntu 9.04 on my Win7RC1 test system broke Win7 such that I had to reinstall Win7 and then manually reinstall grub from the live CD to get back Kubuntu and Win7 boot options :(  I'd hoped 9.10 would fix it but seems not and Gub2 seems to be making repairs harder for folks because its so new and different.

Read up on the Grub2 windows 7 dual boot issues here before you start!


> But how big should i set my storage partition if i have a total of 150gb HDD?  I strongly suggest a second drive for your storage partition, and perhaps Ubuntu as well.  I found a 250GB partition to be pretty small for Win7RC1 although I do mostly video editing on Windows.

Fry's has 1TB SATA drives on sale this week for $70, how much is your time and data worth?

--wally.

---

### Post by jakeeee on 2010-01-13
Ha, I wish I could afford a new drive..
Unfortunately, I'm broke.

I have 9.8 gb of music currently.
But i have a whole list of more music i plan on getting.
So like 30gb?

---

### Post by darkod on 2010-01-13
> **jakeeee said:**
> Ha, I wish I could afford a new drive..
Unfortunately, I'm broke.

I have 9.8 gb of music currently.
But i have a whole list of more music i plan on getting.
So like 30gb?

Sounds good. Lets look at it from another perspective. Standard ubuntu desktop install is around 2.7GB before adding any software. Added software doesn't need as much space as windows. Because you will keep your music on the shared ntfs partition, no need for great storage in ubuntu. Under these conditions, 25GB space for ubuntu is probably enough. Not single 25GB partition, don't create it yourself (unless you know how to do it). Don't forget, ubuntu uses 2 partitions as default. Just leave 25GB unallocated unpartitioned space on the hdd and use the Use Largest Available Free space option when installing. That will take care of everything.

---

### Post by jakeeee on 2010-01-13
> **darkod said:**
> Sounds good. Lets look at it from another perspective. Standard ubuntu desktop install is around 2.7GB before adding any software. Added software doesn't need as much space as windows. Because you will keep your music on the shared ntfs partition, no need for great storage in ubuntu. Under these conditions, 25GB space for ubuntu is probably enough. Not single 25GB partition, don't create it yourself (unless you know how to do it). Don't forget, ubuntu uses 2 partitions as default. Just leave 25GB unallocated unpartitioned space on the hdd and use the Use Largest Available Free space option when installing. That will take care of everything.
Alright, so what your saying is to just leave unpartitioned space and let the ubuntu installer do the rest?

So in the end, I'll have these partitions:

30GB storage
25GB ubuntu
The rest windows?

---

### Post by darkod on 2010-01-13
> **jakeeee said:**
> Alright, so what your saying is to just leave unpartitioned space and let the ubuntu installer do the rest?

So in the end, I'll have these partitions:

30GB storage
25GB ubuntu
The rest windows?

Yes, but usually windows would already be there so it would be:

windows ?
30GB ntfs storage
25GB ubuntu

Also, you can dedicate more than 30GB for the storage. Check how much your windows partition is using right now, and if you have all the software you plan to use, you can calculate how much space is enough for the system partition. Of course, you should leave some spare space. Once you calculate how much you need for the system partition with reserve, and the 25GB for ubuntu, the rest can go to storage partition. If you have spare space, you can also raise ubuntu partition from 25GB to 30GB for example. It's up to you to do the math about your usage.

---

### Post by jakeeee on 2010-01-13
Thanks for all your help :)
Mostly appreciated (:

Im gonna try it out now.

---

### Post by jakeeee on 2010-01-13
You said : Use Largest Available Free space option when installing.

Shouldnt I put the option install them side by side chosing between them at start up?

---

### Post by darkod on 2010-01-13
> **jakeeee said:**
> You said : Use Largest Available Free space option when installing.

Shouldnt I put the option install them side by side chosing between them at start up?

I've only installed few times, but if I remember it correctly that option is if you haven't created unallocated empty space for ubuntu in advance. The side-by-side option allows to resize windows part of disk to make space for ubuntu.

If you have the unallocated space as discussed, just use Largest Available Free space. Don't worry, they'll still be side-by-side because the partitions are next to each other. They have nowhere to go. :)

---

### Post by jakeeee on 2010-01-13
Alright thanks :)
This is my first dualboot, so im kinda nervous.
Thanks for all your help again :)

---

### Post by darkod on 2010-01-13
See, the top line is showing the current state, the bottom line what it will look like. Notice the light gray slider that you can move left-right resizing the two "halves"?

But this is not mine preferred way.

---

### Post by jakeeee on 2010-01-13
YAY :D
I wanna thank everyone who replyed for helping me.

I have sucsessfully dualbooted Windows7 and Ubuntu9.10 (:

---

