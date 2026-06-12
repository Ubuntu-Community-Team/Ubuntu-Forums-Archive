---
title: "Ubuntu Installation - Problem with partitioning"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by sondratheloser on 2007-03-06
I'm trying to dual-install Ubuntu (first time) from a CD onto my PC which currently has XP installed.  

I've only been running the live CD for a few minutes, and I have the book "Ubuntu Linux for Non-Geeks" to supposedly help me through this,  

The problem I'm having is when I click "resize master partition", and it sets it to 50%, it says "unable to create enough disk space".

I recently upgraded to a better PC, and I just stuck my old 30GB harddrive in with my boyfriend's recently-nuked 120GB (the main drive).  I move about 12GB of music from the old 30GB to the new drive,  I installed Photoshop CS2, MS Office 2003, Illustrator CS2, and Doom 3.  That's about it.  I should still have plenty of space... so, I don't know what's going on.

Any help would be appreciated!

Edit -- Do you think it's because I didn't defrag windows first?

---

### Post by bulldog on 2007-03-06
You have to defrag windows several times to get all the file to the front of the disk.
Than take a look in windows to see how much free space is available on your hard disk for ubuntu.
You should have 5-10GB to begin with,but more is better.
Don't forget the swap file,it should be about 1GB,it's the same as the windows page file,only Linux uses a separate partition for it.

It could be preferable to download the GParted live cd .ISO,and burn it to a cd-r.
Boot from it,and you'll have a nice graphical easy to understand partitioner.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

EDIT:

Create a /  (root) partition 5-10GB [more is better] and format it as ext3.
Create  as swap 1GB and format it as swap.

If done pop in the ubuntu live cd and follow the steps as required till you come to the partitioner.
Now choose manually partitioning [already done that] and mount your created ext3 partition  as /  (root)
Mount the swap as swap and reformat both.
Be sure only those two partitions are setup for formatting.
Continue the install and reboot at the end.
All should go smoothly I hope.

If you have more questions,let us know.

Can't really say what your problem is,but it might be.
If the files are scattered around your whole disk,you can't resize it.
Just try and you'll see if it helps.

Just remind the GParted live cd,it's so much easier to use!!

---

### Post by sondratheloser on 2007-03-06
Thanks -- Sounds simple enough.  

Currently downloading gparted, and disk is in the process of defragging.  That'll take a while... download is almost through though. 

Once I get off work tonight I'll defrag again and see how things go :)

---

### Post by bulldog on 2007-03-06
Here's a helpful link,so you can read things up when you're confused.

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

Good luck.

---

### Post by fatal err0r on 2007-03-06
well doesn't 6.10 have the Gparted already in it? why would you need to have a seperate disc?

---

