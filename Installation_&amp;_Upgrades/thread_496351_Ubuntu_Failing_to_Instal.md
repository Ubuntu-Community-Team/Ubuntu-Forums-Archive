---
title: "Ubuntu Failing to Instal"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Dr Zolygon on 2007-07-09
I had a really sloppy setup for my partions on my last install so i decided to do a fresh install
 partitions i made are:

ext3 / 10GB Primary Begenning
ext3 /home 150GB Primary Begenning
swap 3GB Primary Begenning

When i try to install i get an error during the "creating ext3 file system for /home" that says "Failed to create a file system The ext3 file system creation in partition #3 of IDE1 master (hda) failed."

Im not sure what could be causing the problem. I set the partitions to format so I cannot think of what might be wrong.

Any help is appreciated.

---

### Post by jskracht on 2007-07-09
I had the same problem and I can't remember exactly what I did, but I suggest not giving up and going back and trying different things, also do not be to serious on how prefect the partitioning is. 

Just keep trying, mabye even download the gparted live cd as a last resort.

---

### Post by Pumalite on 2007-07-09
Use Gparted for sure. It's the best partitioner there is:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Also make your swap smaller; 3gb is a waste. The rule is twice your memory, but that applies up to 512MB; after that 1 GB is enough. You'll probably never use it.

---

### Post by Odrodzona-Sarmacja on 2007-07-09
You need to make ready these ext3 partitions with that _alternative_ partitioning program (in windows you may wish to use "partition magic"), so during install you will be required only to choose from already existing ext3 partitions which one you want for "/" and "/home/".

if you chose also to have dual boot with windows you may also wish to correct in that alternative partitioning manager the "/home/" partition from "partition" to "xpartition" or your windows system may go crazy, when you boot it.

Any attempt for formating more ext3 partitions then "swap" or "/" during install will fail install. It is a known bug in Ubuntu installer from what i gather here in forum.

---

### Post by hasmind on 2007-08-16
YES I GOT IT TO WORK!
Sorry, let me explain.. I had exactly the same problem as you did, and then I finally got it to work! With me, when I got into the ubuntu live CD I was looking around, and I mounted some random drive accidentally. Then, after the error message I got, I looked on the web for a solution: THERE IS NO SOLUTION ON THE WEB! (as far as I can tell). The simple solution is: unmount any drives that are on your desktop (by right clicking, then selecting unmount). 
lolz, I'm a complete linux noob but i DID figure this one out, and I made a user in this forum just to help out... hope I did!

---

