---
title: "Which option do I choose for installing?"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Catalyst91 on 2007-06-26
So I am trying to install currently, and am looking at this screen
[http://i39.photobucket.com/albums/e191/druski15/Screenshot.png](http://i39.photobucket.com/albums/e191/druski15/Screenshot.png)

Which option should I choose to proceed to dual boot XP and Ubuntu?

---

### Post by merlinus on 2007-06-26
Guided -- use the largest contiguous free space.  Do not choose Guided -- use entire disk or you will kiss Redmond goodbye!

And I highly recommend defragging your windows partition several times first.

-merlin

---

### Post by Catalyst91 on 2007-06-26
It said it was too small to be automatically partitioned D:

---

### Post by merlinus on 2007-06-26
It looks like you have a usb flashdrive plugged in.  If so, unplug it before doing any of this.

Did you defrag your windows drive several times?

You can select Manual to at least look at the free space.

-merlin

---

### Post by Catalyst91 on 2007-06-26
Ok, I unplugged the flash drive and I got this screen
[http://i39.photobucket.com/albums/e191/druski15/Screenshot-1.png](http://i39.photobucket.com/albums/e191/druski15/Screenshot-1.png)

There doesnt seem to be a guided option. I did defrag several times to get all of my data to the beginning of the drive.

And I know for a fact I have like 60gb of space left on this drive

---

### Post by merlinus on 2007-06-26
Looks like you will have to use Manual partitioning.

This may help:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

or this (scroll down the page to get to the manual partitioning:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

-merlin

---

### Post by Catalyst91 on 2007-06-26
So will it work if I edit my NTFS partition and make it smaller so that it will create another empty partition for Ubuntu?

---

### Post by merlinus on 2007-06-26
That is exactly what you need to do -- shrink your ntfs partition and make free space for installing ubuntu.

When partitioning, you may wish to create an extended partition first, and then at least two logical partitions within that, / and /swap.

If you have room, I would also create /home, which will make it easy to keep many of your settings and configurations when upgrading to a newer version.

You might leave 25G for windows, unless you have lots of apps and data, and then have 15G for /, 1.5G for /swap, and the rest for /home.

-merlin

---

### Post by Catalyst91 on 2007-06-26
Ok. I'll try that. If I run into any problems, I'll post them  back on here

---

### Post by Catalyst91 on 2007-06-27
I do have one more question, do I place these partitions at the beginning of the drive, or do I select the end option?

---

### Post by merlinus on 2007-06-27
Windows needs to be at the beginning.  You will shrink your windows partition from right to left, making it smaller.  Then use the freed-up space more-or-less as outlined.

Again, make an extended partition from all of the freed-up space, and then create the other partitions (logical ones) within that.

/swap can be last.  / and /home do not matter, in terms of order.

After creating each partition, set the format to ext3.  You will then have to specify a mount point by clicking on the partition, choosing edit and selecting from the dropdown list.

Take your time.  Nothing will be set in stone until you say so.  You can go back at any time to make sure everything is correct.

-merlin

---

### Post by Catalyst91 on 2007-06-27
Alright, this is what I have
[http://i39.photobucket.com/albums/e191/druski15/Screenshot-2.png](http://i39.photobucket.com/albums/e191/druski15/Screenshot-2.png)

Look correct?

---

### Post by merlinus on 2007-06-27
It looks very good indeed -- well done!

Only question is about the 8MB of free space, but you can probably add that to /swap after the installation is complete.

-merlin

---

### Post by Catalyst91 on 2007-06-27
Great :)
Thank you for all your help

Now to boot into Ubuntu on startup, I want to install GRUB when prompted, correct?

---

### Post by merlinus on 2007-06-27
Yes.  It should install by default in your / partition, sda5.  It will be listed as (hd0,4) -- first hard drive (in your case, the only one), partition no. 5.  

Partition counting for these purposes begins at 0.

-merlin

---

