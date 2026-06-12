---
title: "re-install keep data"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by yarayara on 2007-05-04
Im a complete newbee to linux. Everything was fine for the last 3 months until i decided I was ready to upgrade my dapper version to edgy... bad idea.

Nautilus went crazy, it only shows little squares instead of letters and I dont know how to repair it, so I guess re-installing dapper is the way to go.

So, Im a smart newbee... I was clever enough not to install everything in the same partition, so my HD looks like this:

1- WIN OS
2- WIN DATA
3- BOOT
LOGICAL 4- EXT

5-BOOT  500M
6-USR   10GB
7-VAR   5GB
8-TEMP   1GB
9- /   5GB
10-SWAP   2GB
11- /HOME   77GB

I read some where it was smart to do this. Now that I have to re-install, im worried about not doing it right, deleting my partitions, etc...

so actually, not very smart.

how do i reinstall without loosing my data??

thanks!
-yarayara

---

### Post by scrooge_74 on 2007-05-04
When you go and reinstall tell the system to use your partition system you already have.  Tell it to format only those partitions that are going to be use over again.  

Your
/home

and WiN partitions should stay as they are.  Then you tell the system to mount /home as the /home partition of the system

---

### Post by reckless2k2 on 2007-05-04
Without simplifying it too much, pop in the disc and when you get to the partitioner, map and format everything but the HOME partition. OBVIOUSLY, don't kill your windows partitions. Only remap and reformat the linux partitions that pertain to the linux OS. IF all your valuable linux data is stored in HOME partition, just make sure to map that and NOT format it. 

Before the re-install, make sure to boot into recovery mode and view your fdisk or /etc/fstab so you know what is mapped to what. 

Understand? 

Someone else should be able to confirm what I'm saying but the overall process is pretty simple.

---

### Post by yarayara on 2007-05-04
great!

Im a little slow (better the safe side), so will put it this way:

1- WIN OS
2- WIN DATA
3- BOOT
LOGICAL 4- EXT

5-BOOT 500M
6-USR 10GB
7-VAR 5GB
8-TEMP 1GB
9- / 5GB
10-SWAP 2GB
11- /HOME 77GB

I keep my settings as shown before and format everything except win, windata and home. 

Else, boot, usr, var, tmp, / and swap I have to reinstall as before.

In this way, I will keep my files, email and in general, everything (right).

One more question:
the reason I used separate partitions for boot, ust, var, tmp, / and swap was because I read I could need this separate partitions for a reason I cant remember (Im a newbee).

so the question is, it is ok to format *all* other partions (besides win, windata and home)?

thanks again, Ill keep reading!

---

### Post by yarayara on 2007-05-04
gosh, another question:

for my windows partitions (OS and DATA), which mounting points should I  use?

also, I have a partion 4 which is Primary and it holds the other 7 logical ones.... should I mount partition 4 (and where) or not??

thks!

---

### Post by scrooge_74 on 2007-05-04
you can also just put together all those linux partitions back into one so you only have for linux a swap partition, a /home partition and a good size / partition.

The win partition let ubuntu recognize it then latter you can add read/write support to it so you can see everything from inside linux

---

