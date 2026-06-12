---
title: "Install stalled on partition resize"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by JayBachatero on 2006-10-25
I tried to resize my HD to install 6.06 64bit.  I booted up and picked 50% for the partition and clicked foward.  It has been "running" for almost an hour and nothing is going on.  When I focus on the window it shows the loading image but I can select all the options and move the slider.  I looked at GParted and it shows a lock next to my HD.  I don't want to stop the partitioner in case it's actually running.  What should I do in regards to this?

---

### Post by Ennead on 2006-10-25
Hi, I just went through this same thing last weekend.  Since you are trying to repartition, I'm guessing that you want to set up a dual boot system.   I have a 120Gb HD with three partitions and Win98SE.  My goal was to make my third partition into my ubuntu partition, and thereby create a dual boot system.  And, to use the second partition for sharing files between Linux and windows.

I found this post to be helpful.  

"How do you easily install Ubuntu for dual-boot with Windows?"
[http://www.ubuntuforums.org/showthread.php?t=16287]("http://www.ubuntuforums.org/showthread.php?t=16287")
The posts from Machiner were particularly helpful!

I stalled on the 50% thing, too, and when I tried to do the manual partition, it wouldn't work either.  So I downloaded the GPartED Live CD ISO and used that to delete my third partition.  You can also use a rescue CD from [http://www.sysresccd.org/](http://www.sysresccd.org/) .

Then I restarted my install and found out you have to have at least two Linux partitions "/" and "/swap".  I ended up making 3 partitions, adding a "/home" just for the experience of doing it.  I do not yet have a good idea of what would make for a good partition setup, so don't take that part too seriously.

As I changed the partitions and moved to the next step, it wasn't recognizing my changes.  If I backed up, they were there.  If I moved forward, they were gone.  So, I cancelled the installation and restarted it, and then the new partitions showed up, and I was able to complete the install.  I actually had to cancel and restart several times to get my partitions right, so don't be surprised if you run into the same thing.  Cancelling appears to be a reasonably safe thing to do.

Good Luck! And be sure to check out that other thread.

---

