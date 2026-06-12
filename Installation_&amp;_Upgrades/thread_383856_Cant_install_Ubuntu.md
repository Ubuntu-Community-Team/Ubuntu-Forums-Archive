---
title: "Cant install Ubuntu"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Dizzyfish on 2007-03-13
I have tried the 86x version and that just hangs after I boot from the disk, so I tried the 64 version and I get up to a part where it says remove disk (if any) and press return, but that just hangs after that :confused: I have tried 2 types of CD and 1 DVD - its the same for all.

My system -

AMD 64 dual core @ 2.6G
Abit AT8
2 gig mem
Rad x1800 & x300 - 3 monitors

I was thinking about taking of of the cards out and trying again, do you think that's worth a try?

All my partitions are NTFS, do I need to make a separate partition for this? Never tried Linux before. Hoping to save some money on graphics and web dev apps.

Thanks for your help

---

### Post by wonk-o-matic on 2007-03-14
If you got to the part where the disk popped out, was it because you exited a Linux session on the LiveCD?  If so, did you actually choose the Install program?

---

### Post by Dizzyfish on 2007-03-14
> **wonk-o-matic said:**
> If you got to the part where the disk popped out, was it because you exited a Linux session on the LiveCD?  If so, did you actually choose the Install program?

Iam not sure what happened, its gets to some part where it says its scanning my drives and then it just says remove the disk and press return to continue, when I press return nothnig happens.

---

### Post by OzOle on 2007-03-14
Hey DizzyFish (good name in this situation  :)  )

I don't think you understood wonk-o-matic's question.

If everything is good, then you should be able to run
Ubuntu from the live CD without using your present
installation or harddisk.
[B]Question 1:
Could you do that?
[/B]
If you could actually poke around in Ubuntu from the
live CD then you should be able to install it on your PC.

Next step - install Ubuntu.
On the desktop you should see an icon which invites
you to install Ubuntu.
[B]Question 2:
Did you click on that and the install procedure started?
[/B]

If that happened then follows the next question which
is the most important one for anyone to try to understand
at what point things go wrong:
[B]Question 3:
At what point in the install procedure did you get the message
to take the CD out? In other words what was the message
immediately before that happened?
[/B]

If you can give us some specific answers then there is a
good chance that somebody can help you.
And, yes, the Ubuntu version to use is obviously 86x,
however, I don't know whether having a dual-core CPU
makes a difference. What we need here is some really
heavy systems programmer, I think.

Good luck, once you get it working you'll love it.

Ole from Australia

---

### Post by Dizzyfish on 2007-03-14
Right disregard my first question, I got it working:popcorn: 

So I clicked the install on the desktop, fill in the name password etc and then I come to the partition bit - I have 6 partitions on 2 HDD's windows, games, movies etc. Can I install it on one of these partitions without overwriting the data already on there? I wasn't sure if it was going to overwrite the data so I discontinued the install there. It was also asking something about mounting drives, if I continue the install and agree to the mounting business is my current data safe and can still be read by windows?

Thanks

---

### Post by zvacet on 2007-03-14
You say that you have 6 partitions.Is any of them free and what size is?Does your games...belong to windows partition?Post answer and we will see what to do next.

---

### Post by Dizzyfish on 2007-03-14
Sorry its 7, here's a screenshot -                          

[IMG]http://img177.imageshack.us/img177/3904/image1md3.jpg[/IMG]

---

### Post by bulldog on 2007-03-14
To install ubuntu you need to have some free space to do so {10GB}.
So you have to create a free partition for about this size as a minimum.
And it's recommended to create a swap file {1GB} as well.

If you install in an existing partition without creating a new partition ,your data will be lost!

---

### Post by Dizzyfish on 2007-03-14
So would it work if I repartitioned that Movie partition and created say another 15G partition for Ubuntu?

---

### Post by bulldog on 2007-03-14
> **Dizzyfish said:**
> So would it work if I repartitioned that Movie partition and created say another 15G partition for Ubuntu?

Yes it would :) 
Keep in mind ubuntu can be installed in an extended [logical] partition and your swap can be a logical too.
It doesn't require a primary like windows.

---

### Post by Dizzyfish on 2007-03-14
Thanks chaps, I'll give that a try now :)

Can Ubuntu read from those NTFS partitions also?

---

### Post by bulldog on 2007-03-14
Yes,Ubuntu can **read** the NTFS partitions,but **can't** write to them.

There is a method to make this happen.though.

---

### Post by Dizzyfish on 2007-03-14
Still cant install this bloody thing :( 

I tried to install it on one of my older Western digital 80G IDE drives, I chose the first option format entire drive to ext3 format, or something like that and then pressed install, it gets to %15 and says - the attempt to mount a drive with ext3 failed, I tried partitioning the drive with several ext3 partitions and it keeps saying that :/

---

