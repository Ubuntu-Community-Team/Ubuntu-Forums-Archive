---
title: "cannot upgrade, not enough free space"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by pjizz on 2010-09-27
hello,

i've been using 10.04 on my laptop for a while now, and I am ready to make the jump on main machine (with 10.10 coming out soon, I don't want to be too behind the times)

however, my / partition is apparently too full, as I get the message: "not enough free disk space."

Since I'm not really sure what in the / partition is fair game and what needs to be left alone, I am sort of at a loss for how to free up space.  i have plenty of free space in other partitions, but I don't know of a way to stretch them out, so to speak.

i've attached a screenshot of gparted showing how my disk is partitioned

any suggestions on how to go about making the necessary changes to get the upgrade?

thanks in advance!

---

### Post by pjizz on 2010-09-27
here is the full message
```

The upgrade is now aborted. The upgrade needs a total of 3240M free 
space on disk '/'. Please free at least an additional 226M of disk 
space on '/'. Empty your trash and remove temporary packages of 
former installations using 'sudo apt-get clean'
```

---

### Post by snowpine on 2010-09-27
A good start would be to follow the suggestions:

> Empty your trash and remove temporary packages of 
former installations using 'sudo apt-get clean'

Failing that, you appear to have plenty of room in your Data partition, so I would recommend booting with a Live CD and using GParted to move the partitions around and create some extra space in your / partition.

Of course, you will want to make a full backup of all paritions before doing this. :) 

Alternately, you can do a fresh reinstall of 10.10... many users consider this to be the "cleaner" option.

I would wait until 10.10 is stable, personally.

---

### Post by pjizz on 2010-09-30
> **snowpine said:**
> I would recommend booting with a Live CD and using GParted to move the partitions around and create some extra space in your / partition.

Of course, you will want to make a full backup of all paritions before doing this. :) 

would i need to use the live cd, or could i simply use GParted after having booted from the hard disk?

---

### Post by snowpine on 2010-09-30
> **pjizz said:**
> would i need to use the live cd, or could i simply use GParted after having booted from the hard disk?

You cannot change the tires on your car while you're driving... you need to use a Live CD. :)

---

### Post by pjizz on 2010-09-30
haha, that's what I thought. 

so, i haven't used a physical cd since 7.04...could I use that, or should i create a newer cd?

---

### Post by snowpine on 2010-09-30
> **pjizz said:**
> haha, that's what I thought. 

so, i haven't used a physical cd since 7.04...could I use that, or should i create a newer cd?

7.04 cannot handle your ext4 partitions, use 10.04.

You can create a Live USB if you don't want to burn a CD for whatever reason.

---

### Post by pjizz on 2010-09-30
okay i found a 9.04 disc I made for whatever reason...it sees the ext4 partitions, but i can throw up a 10.04 live usb no problem.

one problem, though, is that I'm not exactly sure how to go about resizing the partitions correctly.  the /, swap, /root and /home partitions are all part of a larger 40 gb extended partition, sandwiched between a 40 gb win7 partition on the left and the large Data partition on the right.  i can see how to shrink partitions, but then i have just a new unallocated partition.  is there a way to append that space to the / partition, effectively growing it so that there is enough room for future distro upgrades, or do i need to slice up a big chunk of the data partition and make a new / partition?

thanks, again, for your help.  this is what makes ubuntu fun!

---

### Post by snowpine on 2010-09-30
Once you've created empty space, you can "slide" partitions left or right into the empty space. This will take a long time and you should make sure you have a backup just in case the power goes out or something. :)

---

### Post by pjizz on 2010-09-30
Okay, i see now that I can do that.  I had to first turn the swap off.  However, i am growing /dev/sda3, i.e. the full extended partition.  how do I ensure that the partition that receives the extra legroom will be the / partition?

---

### Post by pjizz on 2010-09-30
AHHHHHH i see...by clicking in the correct spot you can grab the whole partition and drag it...very nice.  i was about to write down all my partition sizes and drag each end individually...this is much better, thank you

---

### Post by snowpine on 2010-09-30
Good luck! Remember that it will take a little while, so go make a sandwich or something. :)

---

