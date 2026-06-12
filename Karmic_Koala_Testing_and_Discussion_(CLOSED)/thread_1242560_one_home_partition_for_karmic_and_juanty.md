---
title: "one /home partition for karmic and juanty?"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frustphil on 2009-08-17
I'd like to help testing karmic in real setup. But first I want to know to what extent it would mess up my /home if something bad would happen. I don't have enough extra space for another /home partition.

---

### Post by inportb on 2009-08-17
Some configuration files would be erased/rewritten, and the result may not be compatible with Jaunty. Also, switching between Jaunty and Karmic may cause one to wreck the configuration for the other.

Why do you need another dedicated home partition?

---

### Post by frustphil on 2009-08-17
> **inportb said:**
> 
Why do you need another dedicated home partition?

:) Thank you...

---

### Post by dino99 on 2009-08-17
I'm testing distro since Edgy & have always use one /home shared with several Os without any trouble, but i regularly save my work on a separate partition ( in case of big pain)

So, it's up to you to decide what is important or not.

---

### Post by plun on 2009-08-17
There is an excellent guide at Psychocats howto move /home to an
separate partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

**Note** that its written for **Ext 3 **and you now can choose **Ext 4**

You then always chooses "Manual partitioning" during install and also defines it as /home, (and no format !!!)

---

### Post by frustphil on 2009-08-17
> **frustphil said:**
> :) Thank you...
@inpotb: lol thought you were being sarcastic. 
just realized that. y would i and mess my /home partition for jaunty? lol
thank you...

---

### Post by Kobalt on 2009-08-17
What I usually do for such situations is to create a new user for the testing distro. This way you can use the same /home partition but don't mess each distro settings...

---

### Post by slakkie on 2009-08-17
I use my /home for 8.04-9.10. Only issue I have is 4.2 .kde dir (9.04) differs from 4.3 (9.10) and off course also for KDE3.5.10 (in 8.04)

You can make a tarball of your . dirs and backup restore where needed.

---

### Post by meborc on 2009-08-17
i never use separate /home partition... i usually mess the configs up so bad that it is easier to reinstall :)

all data is on separate data partition of course

---

### Post by almostlinux on 2009-08-17
> **Kobalt said:**
> What I usually do for such situations is to create a new user for the testing distro. This way you can use the same /home partition but don't mess each distro settings...
 
That's a nice idea .. multiple users but one home to rule them all  :lolflag:

---

### Post by frustphil on 2009-08-17
I messed up my jaunty /home partition and I ended up refomatting it. Fortunately I have all files saved. Now if I only knew how to point grub(or is it grub?) back to that partition as my home.

> **plun said:**
> There is an excellent guide at Psychocats howto move /home to an
separate partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

**Note** that its written for **Ext 3 **and you now can choose **Ext 4**

You then always chooses "Manual partitioning" during install and also defines it as /home, (and no format !!!)

It didn't work for me nor the last two alternatives. I am now writing this using Karmic. The only glitch I see so far is menu-bar won't allow dragging items onto Docky.

---

