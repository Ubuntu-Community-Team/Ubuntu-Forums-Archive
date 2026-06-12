---
title: "Another partitioning problem"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by Horizon9 on 2011-05-28
OK, I'm a noob.. :D

Now that we got that out of the way, here's the problem and I hope someone can help me. Before posting, I read everything I could find here about partitioning in gparted (at least what I think applied to my situation). I'm pretty sure that this has an easy answer (or I hope it does).

I originally installed Ubuntu 10.10 on a USB stick  to try and retrieve files from a failed NAS drive. That worked pretty well (thanks to a very smart guy who posted instructions on how to do the hex editing necessary to realign and enter a reiserfs disk) so I decided I'd jump in and play with Ubuntu.

I decided to port my USB install to an 80GB USB drive I had kicking around, but the install didn't actually take the whole disk the way I thought it would, it only took the 7.xGB from the USB drive.

I didn't notice (I know, dumb) and then I did the 11.04 upgrade to it. I'm trying to recapture the other 65GB of unused space via gparted, but I can't for the life of me figure out how to extend the original boot partition (I have no /home partition). i tried to format the unused space to ext4, but no matter what i do I can't expand that original partition (I can shrink it if that matters). Just to be clear, I booted from a live cd 10.10, and I'm running gparted on the unmounted USB drive. The boot partition should not be active.

My screen shots capability is not working correctly right now, but I'll post one if I can. I can only get a full screen shot, and this is on a 30" monitor.. I just want the active window 

the /dev/sdj1 partition is on the left (7.11GiB) witha boot flag, then the Ext/Swap at 377MiB each /dev/sdj2 and 5) and then another 68,85 GiB partition, currently formatted to Ext4 on the right labeled /dev/sdj3. No other partitions. I can extend the Ext/swap, but not the boot partition.

Any help would be most appreciated. 

thanks

---

### Post by Hedgehog1 on 2011-05-28
You have the right idea.

First - you need to boot off the an Ubuntu LiveUSB or LiveCD (or a separate Ubuntu install on a USB stick :D )  and run gparted from that.  This is because you cannot make change to the partitions that are mounted.

So, from the Booted USB run gparted.

In gparted, right click on the swap partition on the hard drive, and select 'swapoff' if that option shows. This makes sure the swap partition is not in use.

Now - If you have an extended partition that your Ubuntu partition(s) are in, expand that to the end of the disk.

Then, move your swap partition to the very end of the available space.

You can now expand the EXT4 partition to fill the available space.

***The Hedge***

:KS

p.s. This would be a good time to consider making a separate home partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by Horizon9 on 2011-05-28
Wow, that was fast! :D

I am running from a live CD (10.10) and running gparted there. (in my first post).

When I click on the swap partition, I see "swapon", so should I assume that means it's already off?

My extended partition is 377 MiB and I can't enlarge it.. I'm shrinking the 65GB partition to give myself some room...


I wish I could get the screen capture to work correctly. When I try to shrink the capture from a 30" monitor, you can't see anything.

I hope I'm not going off the deep end here, but I'm changing the largest/unused partition to a smaller one, with space on both sides. that should give me space to enlarge the Extended/swap partition to the right. Should I also move the left side to the right, giving me more space to enlarge the boot partition?

IOW, is it just a matter of "moving thing's down the line" to make room?

---

### Post by Hedgehog1 on 2011-05-28
You can do this - and it will tells us about your disks and partitions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by Horizon9 on 2011-05-28
First, I want to say Thank You! I was so surprised that someone responded so quicly I forgot to say thanks!

Anyway, I may have been mistaken, but the partitioning is taking some time since I now will have a partition with empty space on both sides. It says it's has 17 minutes remaining. I'm assuming I can run that when I'm done, and then post the results..

I'm not sure why this is taking so long though. When I did some other experiments, they all completed in 1-2 min....

I may have screwed up... but I hope not...[-o<

Update... this is screwed up..now it's copying "data" as it move the partition, but it was empty to begin with... Uggg.. It say it has 55 more min to go.. and there's nothing there...

I should just do a reinstall I think, but I'm afraid to stop this process...

---

### Post by Horizon9 on 2011-05-28
Forgot... I'll create a new /home partition when I get this part straightened out. :D

---

### Post by Hedgehog1 on 2011-05-28
Take your time - it is more important that you are careful then fast.

:P

---

### Post by Horizon9 on 2011-05-28
Still can't get the screen shot to work for the active window only.. Very strange

Anyway, my gparted window looks like before for the first two (reading left to right) partitions (boot, then extended and swap within it) then I have a 12GB hole, then a 36GB partition, then another 21GB hole...

I was hoping that I could start moving the ext/swap partition to the right and expand the boot partition by dragging it to the right too...No luck...

I downloaded the boot info script, but I don't know how to run it...:confused:

---

### Post by Horizon9 on 2011-05-29
hedge,    

Thanks for the help, but it just was never going to work...  I could never get the screen shot capability to work, so it was making it a little more difficult to explain (I was using th 10.10 live CD).    

I decided to say screw it and wipe out the hard drive.  I reinstalled 11.04 and set up the new partitions similar to this


[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)  


Not exactly the same, but close enough.

I know I'm a linux noob, but I'm not convinced that gparted is as powerful as some say. I'm not a noob when it comes to computers, or programming, though, and have used several partitioning tools. I could never get either the / or swap partitions to move. Oh well...Faster to set up a new install since I have almost no data to lose (already saved to another hard drive) and few configurations that couldn't be recreated.   thanks again..

---

### Post by Hedgehog1 on 2011-05-30
Well - sometimes a 'nuke-and-rebuild' has it place.

I have always been able to get gparted to work **IF** the partition map was not damaged.

With the troubles you were having, you partiton map may have been damaged and the 'nuke-and-rebuild' solves that, too.

In any case - you are running Ubuntu again.  That's great!

***The Hedge***

:KS

---

