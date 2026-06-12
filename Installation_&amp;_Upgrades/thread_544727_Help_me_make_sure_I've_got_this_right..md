---
title: "Help me make sure I've got this right."
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by Cloudy on 2007-09-06
Okay, so here's the deal. I wanna do a fresh install of Feisty Fawn on my Ubuntu partition, and I have the Installer open now looking at my partitions. They look something like:

> 
/dev/sda/: 

/dev/sda1 - SWAP
/dev/sda2 - NTFS - 175GB Windows XP
/dev/sda3 - Ubuntu partition
/dev/sda4 - unused partition, 5GB


So, I decided to edit & format the Ubuntu partition but when I do this it asks me if I want to import any accounts and shows a list of XP user accounts. I'm being careful here because I share this computer with others who do not know anything about linux and there's quite a lot of music, games, etcetera on the XP partition. 

So, I designated sda3 as the root partition ( / ) and when I clicked continue it asked me if I wanted to import anything and gave me a list of XP folders and user accounts. My question is this: is this normal procedure? If I set sda3 to my root partition and install Ubuntu there, I'm not losing anything in XP am I?

I'm assuming that I'm not losing anything in XP, but I wanted to double check and just make sure this is standard procedure before continuing. Paranoia always gets the best of me.

Thank you for your help

---

### Post by merlinus on 2007-09-06
I have found is that ii is best to not import anything from xp.

And no, nothing in xp will be altered, as long as you install to sda3.

Also, do not make sda1 swap, but keep it as windows, which wants to be first on the hdd.

You also may wish to make sda3 an extended partition, and then create logical partitions within that for / and /swap.  And if you leave sda1 as windows, then make sda2 extended instead.

-merlin

---

### Post by Cloudy on 2007-09-06
> **merlinus said:**
> I have found is that ii is best to not import anything from xp.

And no, nothing in xp will be altered, as long as you install to sda3.

Also, do not make sda1 swap, but keep it as windows, which wants to be first on the hdd.

-merlin

That (SWAP at sda1) actually seems to be something from a previous partition, it seems.

---

### Post by merlinus on 2007-09-06
It may have been an OEM restore partition.  As long as xp is running okay, then leave sda1 as /swap, but I suggest making sda3 extended, etc., as in my last post.

-merlin

---

