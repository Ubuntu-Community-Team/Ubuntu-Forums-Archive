---
title: "[SOLVED] installing Ubuntu as the only OS ...and failing"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by kerrymorgan1 on 2007-08-14
specs of my computer:
2g ram, amd4000+, 500g Sata HD, 8600GT XXX edition
How old: arrived yesterday

I installed Ubuntu 7.04 yesterday and got carried away and excited i think i stuffed up big time.

i wanted to do some advanced crap ...... yeah shouldn't have now im trying to fix it.
when i put in the CD the menu comes up to select i have selected everything and the result is the same "Blank" for about 5 mins
it says something like 
"kernel alive"
"kernel directing tables" 
before it goes blank but it goes dead the cpu is still running
after 5 mins it starts as usual.
the first time i did this on the computer it was instantanious 

what do i do to fix it? i have installed Windows XP just last night after all the dramas i had
somebody please help!!!!!!:confused:

---

### Post by merlinus on 2007-08-14
If you installed xp after ubuntu, then it overwrote grub.  Or when you installed xp, did you tell it to use the entire disk?  In that case, you will have to reinstall ubuntu.

If not, you can reinstall grub from a terminal after booting with the live cd.  Enter these commands one at a time:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```Substitute results from find for (hdx,x).

Then you should have a grub menu on startup.

-merlin

---

### Post by kerrymorgan1 on 2007-08-14
firstly you're the man......... secondly what do you mean replace find with (hdx.x)?
i'm gonna do the dual boot thing right now just trying to figure out the partition thing
should i install grub first? i hope i didn't destroy my new computer

---

### Post by merlinus on 2007-08-14
It sounds like you used the entire disk to install xp, and therefore destroyed your ubuntu installation.  If so, then you need to reinstall from the live cd.

When you get to the partitioning menu, you can re-size your windows partition to make room for ubuntu.  With 500G, you have lots of space!

Depending upon the programs you want to install, and the kinds of files you will be creating (music, photos and videos take up lots of space), you can leave 100G for xp.

Then in the freed-up space, make an extended partition.  In that extended partition, make logical partitions of 30G for /root, 20G for /home, 1.5G for /swap, and the rest leave for storing data.

Here is a good link for info:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

### Post by kerrymorgan1 on 2007-08-14
I entered "sudo grub" into the terminal it spits out something but then when i type in "find /boot/grub/stage1" it says file not found what do i do now?

---

### Post by merlinus on 2007-08-14
As I said, when you installed xp it took over your entire hdd.

Follow instructions at the link I provided.

-merlin

---

