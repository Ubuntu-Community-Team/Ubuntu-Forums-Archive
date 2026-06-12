---
title: "Is this a good partition setup?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by krolben on 2007-04-19
Hi all

I'm about to install a new Ubuntu Feisty Server, but I'm unsure about the partitioning layout. Would really apprecite some feedback.

The server will be used as a home file/music server and as a small webserver. Maybe also as a mail server in the near future.

It's a Mini-ITX system and I've got these disks:
1 Internal flash drive, 1GB
2 external ATA drives, 320 GB each, connected through USB

This is the partition table I'm planning to implement:
/boot: 200 MB on the internal flash drive
/swap: 800 MB on the internal flash drive
/home: 220GB on external drive 1
/var: 40GB on external drive 1
/: 60 GB on external drive 1
/backup: The entire external drive 2

Is this an ok layout?

---

### Post by chakkaradeep on 2007-04-19
> **krolben said:**
> 
/home: 220GB on external drive 1
/var: 40GB on external drive 1
/: 60 GB on external drive 1


You could very well reduce the / partition to 30 GB which is more than enough and increase the /home with 30 :)

And If you RAM is 1 GB, you can set swap for 2 GB

---

### Post by rillip on 2007-04-19
What you've outlined seems like a pretty good plan.  I don't see the need to up the swap space; 1x your ram would let you go to hybernate.  I see a lot of people suggest 1.5 - 2x as much as your ram, but if you think about it, you're trying to do so much you need double the ram you have?  Some swap is appropriate for background applications, but if you need  more swap than you have ram, you need more ram!  Putting it on that flash drive will be schnazzy.  Also nice that it's on a seperate bus, should provide some really good througput.

60gig does seem a bit on the large size for root, but it won't really hurt anything.

---

### Post by krolben on 2007-04-19
> **rillip said:**
> Some swap is appropriate for background applications, but if you need  more swap than you have ram, you need more ram!  Putting it on that flash drive will be schnazzy.  Also nice that it's on a seperate bus, should provide some really good througput.

I take it that schnazzy means "good" :) 


I've tried to install with this setup, but the installer crash every time I get to the GRUB installer. During install it says that it can't install to the drive. LILO succeeded, but I afterwards I couldn't boot the system.

I'm now back at Edgy, trying out that version with the same setup...

---

