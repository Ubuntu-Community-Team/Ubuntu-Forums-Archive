---
title: "A newbie wondering how to create a new partition"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by Cecil on 2005-01-31
Okay, this will be the first time I've installed a new OS alongside an existing one. Currently, my hard drive just has one big partition, and the unpartitioned space is only ~5MB. As I'm afraid of accidentally erasing data off of my WindowsXP partition, could someone give me a tutorial on how to take part of Windows partition, specifically the free space, and make it into a new partition in the Ubuntu setup? I'm sorry if I'm fretting over nothing, I've never done something like this before, and I just want to do it right.

---

### Post by ctt1wbw on 2005-01-31
I would suggest using a program like Partition Magic.  It's fairly simple and straightforward.  Your linux os will have a "/" or a root partition and what is called a swap partition.  But beforehand, I would highly highly recommend you defrag your XP system a few times and then backup your important information.  :)

---

### Post by Cecil on 2005-01-31
[QUOTE=ctt1wbw]I would suggest using a program like Partition Magic.  It's fairly simple and straightforward.  Your linux os will have a "/" or a root partition and what is called a swap partition.  But beforehand, I would highly highly recommend you defrag your XP system a few times and then backup your important information.  :)[/QUOTE]Yeah, thanks, but I have already done it. A little searching took me to the program you suggested to me, and I have Ubuntu installed alongside Windows, now.
Thanks, anyway.

---

### Post by Kokosnuss on 2005-01-31
Is a swap partition necessary? And if, can I store other data on it, too?

---

### Post by Rancoras on 2005-01-31
[QUOTE=Kokosnuss]Is a swap partition necessary? And if, can I store other data on it, too?[/QUOTE]
Yes, it's necessary.  No, you can't store other data on it.

---

### Post by Kokosnuss on 2005-01-31
Really? Do I really need a 'swap'-partition or can I also use the '\'-partition? When I attempted to install Ubuntu yesterday, I didn't need to specify a 'swap'-partition.

Anyway, what do I need the 'swap'-partition for? I thought it would be a facultative option for an outsourced, virtual RAM...

Greetz
Felix

---

### Post by Rancoras on 2005-01-31
I guess if you have enough RAM, then you probably wouldn't need a swap.  I've always been told to have at least a small one.

---

### Post by Jad on 2005-01-31
Well, Swap seems to be a must
[http://twiki.iwethey.org/Main/NixPartitioning](http://twiki.iwethey.org/Main/NixPartitioning)

---

