---
title: "Adding 3rd HDD, Disk Management ?"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by zaarch on 2010-01-18
Hi,

I have an IBM thinkcentre with two HDD (160GB, 1TB). Now, I am planning to add an additional 1.5 or 2TB drive.

No big issues there. I can auto mount the drive.

Here is my dilemma -  I have a folder called "Share" accessed by users via Samba. Now once I add the second drive, which will have similar data like "Share"...

However when accessed via samba..i want users to see one bigger folder and not two smaller folder..one from each drive.

Since i cannot take the data off the first drive, i assume doing raid out of the question.


Hope it makes sense.
Zaarch

---

### Post by ttoilleb on 2010-01-18
May I suggest you read the following - [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm) - 
LVM is *Logical Volume Manager*.  

After reading this, I would suggest the following sequence of events.

1. Setup PV and LV on the new drive   
2. Copy the current *Share* directory to the new LV space.
3. Define space on the existing drive (this will wipe out all the existing data)
4. Add the space define in 3.  to the LV on the new drive
5. Adjust directory names as needed

The above will be clearer after reading the documentation.

If you want the drives to be set in a RAID that is also discussed in the documentation.

This is what I did to create a single logical volume spanning 2 physical volumes (I - 250gb and 1 - 500gb usb drives.) used for backups on 9.04 that is connnected to by a Windows Vista desktop and a 9.04 laptop.  

It works real well as long as you follow the instructions


HTH

---

### Post by zaarch on 2010-01-19
Thanks HTH.

This is pretty much what I need. 

Two physical volumes, one logical volume! That's how I should have worded it.

However, I am not in a position to move my data (even for temp purposes), therefore,  I need a solution where I need not wipe clean the 1st volume.

Any ideas?

Zaarch.

---

### Post by ttoilleb on 2010-01-19
Doing some digging, I found fhe following - [http://www.linuxquestions.org/questions/linux-software-2/creating-an-lvm-volume-group-with-a-mounted-ext3-partition-682202/](http://www.linuxquestions.org/questions/linux-software-2/creating-an-lvm-volume-group-with-a-mounted-ext3-partition-682202/)

So it appears that without moving the data, you can't.

Not knowing the restrictions on moving the data, it is impossible for me to make any other suggestions.

HTH (Hope this helps)

---

### Post by zaarch on 2010-01-19
hahah ...thanks for the help.

HTH (hope this helps)..

i thought..it was your nom de plume.

Zaarch ( zaarch)

---

