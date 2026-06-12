---
title: "partition ruined hard disk"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by pangil on 2007-10-26
hi, i have 2 PCs at home that were previously running windows. i installed ubuntu on one PC, liking ubuntu, i tried installing it on the other PC. when i did a manual partition on the other PC with these
preferences:
#1 - primary - 4GB - /
#2 - logical - 1GB - swap
#3 - logical - 15GB - /usr
#4 - logical - 20GB - /home

the installation went ok. but after restarting i got this error:
GRUB loading stage1.5 Read Error

i tried repeating the installation this time using guided partition and using the entire disk but i still got
the same error.
thinking that it there was probably something wrong with my installer, i installed debian. and i got the
very same error.
frustrated at having spent hours trying to get it to work, i went back to windows. when windows restarted during the installation i had a read error.
so now i got 1 useless computer because it looks like the hard disk is ruined.
could the partitioner have ruined my hard disk? is there still a way to fix it?

---

### Post by pangil on 2007-10-26
hi, i ran gparted to completely remove all of the partitions and started a fresh install using the
default settings.
i still got the same error:
GRUB loading stage1.5 read error

unfortunately my hard drive did not come with a diagnostic CD.
i'm really new to linux and i really don't know how to run super grub. can i get some help
concerning this? are there any other methods that i can try to fix my problem?

---

### Post by pangil on 2007-10-26
hi, i tried almost everything. tried to fix the mbr with super grub. even tried to fix mbr using XP's installation disk but none of them worked. 
i can't believe ubuntu would ruin my hard drvie like that. and now there's no way to recover from this error. i probably have to trash my hard drive now. 
this is just great. really cool partitioner.

---

### Post by kvonb on 2007-10-27
No partition software can physically damage your hard disk,it's impossible.

I would say that you simply used a sector that was on it's way out, pure coincidence.

All is not lost though, you need a disk repair prog, find out what brand of drive it is and go to their webpage and search for a recovery tool.

Run a full surface scan which should fix any problems.

Alternatively, buy a copy of Steve Gibson's excellent "Spinrite6".

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

It has recovered many hard drives for me, and is a great tool, well worth the money.  I've even used recovered hard disks in a few servers without any problems.

Then simply create a dummy partition over any permanent bad sectors in order to avoid them.

For example, if the start of your disk is bad, create a small partition, big enough to contain them, and just don't use it.  Create your regular partitions after it.

---

### Post by Dread Knight on 2007-11-09
Same just happened to me. The only thing i haven't tried is the windoze xp installer.. because i don't have the cd. Running ubuntu feisty livecd right now.

Need help :(

I think the "linux laptop hdd killer bug" isn't just for laptops...

---

