---
title: "Formatting (entire) harddisk"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by bjorn1000 on 2010-10-26
**Hello. **My computer with Ubuntu has gone bad. I would really like a fresh start, so I'd like to format the entire harddrive, but I can't find DOS. I tried to find it through my Live CD, but **I am a newbie**. Can anybody please help me, step by step? :confused:
Ubuntu 10.04 LTS

Please see my pictures of what happends in this URL (red text in english).
[https://sites.google.com/site/abildamine/001](https://sites.google.com/site/abildamine/001)

---

### Post by oldfred on 2010-10-26
You should not need DOS to do anything.

If you use liveCD and boot into it. Can you use gparted (system, administration, gparted) to see drive? If you can does it show an error like red or yellow symbols saying the partition has errors? If not try deleting everything. If you want you can try creating partitions for / (root) & swap. Also this would let you create a separate /home partition. Then during the install you use manual install and choose the partitions.

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by bjorn1000 on 2010-10-30
Hello, Oldfred, and thank you for trying to help me.
I've tried to understand more of the tutorial of GParted, but I feel I'm standing still:
I try to start the prosess, but I fail to get any further.
Please check out how far I've got along, and see my comments on this URL (with my step-by-step pictures).

[https://sites.google.com/site/abildamine/002](https://sites.google.com/site/abildamine/002)

---

### Post by P4man on 2010-10-30
From the livecd, try system | administration | disk utility
Select your harddrive, and click on SMART DATA. Have it run the self test. I suspect the problem you had with ubuntu that "went bad" is the same problem preventing the reinstall: a bad harddrive.

---

### Post by bjorn1000 on 2010-10-31
> **P4man said:**
> From the livecd, try system | administration | disk utility
Select your harddrive, and click on SMART DATA. Have it run the self test. I suspect the problem you had with ubuntu that "went bad" is the same problem preventing the reinstall: a bad harddrive.

I found the **Disk Utility**, but can't find a option called **Smart Data**. 
The option "**Check Filesystem**" is awailable on the **CD/DVD Drive**, and on the **704 MB File**.

Do I have to **Format Drive** before I can use **Self test**? If so: What should I choose regarding size and so furth?

[COLOR=Red]Please see picture at this URL:[/COLOR]
[https://sites.google.com/site/abildamine/003](https://sites.google.com/site/abildamine/003)

---

### Post by P4man on 2010-10-31
it says smart status: not supported. Check if your bios has the option to enable SMART monitoring. Formatting isnt needed nor will it help.

---

### Post by oldfred on 2010-10-31
If you only have one drive you do not have to choose drive. Under partition choose new and then you should be able to create partition(s).

---

### Post by bjorn1000 on 2010-11-01
> **P4man said:**
> it says smart status: not supported. Check if your bios has the option to enable SMART monitoring. Formatting isnt needed nor will it help.

Thank you, [COLOR=Red]P4man[/COLOR]. 
The test gives result = Passed, please see picture at
[COLOR=Blue][https://sites.google.com/site/abildamine/004](https://sites.google.com/site/abildamine/004)
[/COLOR] 
I will now try to create partitions, like [COLOR=Red]Oldfred[/COLOR] says.
But what should I call them, and what size should it be?
Should I just follow the adwise at GParted partitioning software tutorial?
It has so many different examples, [COLOR=Black][COLOR=DarkGreen]it feels[/COLOR] a little [COLOR=DarkGreen]like a jungle[/COLOR]...[/COLOR]

---

### Post by P4man on 2010-11-01
Passed means it completed the test. Overall assessment is that your disk is having bad sectors. How much of a problem that is is hard to say, especially since I cant read the actual value, but a healthy disk should report zero or close to zero.

---

### Post by bjorn1000 on 2010-11-02
I guess the disk is destroyed. I only get errors, like "couldn't create partion" and so on.
Hopeless. :-)
Guess the next step is to flash my Mastercard to some salesman somewhere.

---

### Post by pizza-is-good on 2010-11-02
I couldn't read the screen shot, but if you can't format the drive, and if it has bad sectors, chances are the drive is useless now...

So yes, sadly, it looks like you do need a new hard drive. Fortunately, hard drives are really cheap nowadays... (As opposed to a few years ago)

All the best,

~pizza

---

### Post by P4man on 2010-11-02
> **bjorn1000 said:**
> I guess the disk is destroyed. I only get errors, like "couldn't create partion" and so on.
Hopeless. :-)
Guess the next step is to flash my Mastercard to some salesman somewhere.

Yep, thats what I feared.Anyway, sorry for your loss, but on the bright side, like mentioned above, you can buy a fast terrabyte drive for the price of a few beers nowadays (if its for a desktop at least).

BTW, what a great idea it was to include that disk/smart utility on the livecd.  Even if its not perfect.

---

