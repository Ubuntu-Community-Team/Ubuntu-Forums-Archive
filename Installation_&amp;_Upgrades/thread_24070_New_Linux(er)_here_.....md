---
title: "New Linux(er) here ...."
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by guitarista on 2005-04-05
Hi there ,
Well first off , I'd like to say that Ubuntu is simply great (!) I've been usin' the Live CD ( Hoary 5.04 RC ) for a week now and it rocks indeed .
Alright , lookin' forward to installin' it on Friday 8th , I've got a question though concernin' the installation seeing that I'm not quite well aquainted with Linux stuff , so be indulgent .
I've a single S-ATA drive with 3 partitions :
1. WinXP Pro _ SP1 (10 GB )
2. Proggies ( 10 GB )
3. Storage  ( 40 GB )
There are still 90 GB unallocated space left .
My question is , what would be the best way to install Ubuntu ? I've just read some threads about troubles caused by Grub ( MBR stuff and so .. ) , do I have to use a boot manager ?
Thanx in advance .

---

### Post by tdell on 2005-04-05
Should be fairly simple and straightforward. I had a similar setup. 

Since you have XP already installed, Ubuntu will install itself in the unallocated space. Easiest thing is to let it format and partion that space automaticlly.

Grub will see XP and set itself up properly, problems with grub usually happen when trying to install another OS AFTER Ubuntu.
I ran that way for a month and a half when I realized I never used XP anymore and did a new format and install to get rid of XP.

The only difficult thing I think you will run into is your monitor setup. 

Ubuntu does not seem to recognize the correct defaults.
If your monitor looks screwy or you cannot get the correct refresh rates, just open a terminal and enter this:

sudo dpkg-reconfigure xserver-xorg

You can accept all the defaults until you get to the end where you should select the advanced option here you would enter the Horiz & Vert rates of your monitor if you do not know what they are check your manual or the manufacutrers website.

Good luck.

Tom

---

### Post by guitarista on 2005-04-05
Thanx for the prompt reply m8 .
Ok , now what about /home , /swap ? Are these partitions I should set to get Ubuntu up and runnin' well ? And how "Big" are they supposed to be ?

---

### Post by Leif on 2005-04-05
OK, if you are aware of /home and /swap, maybe you should manually allocate space instead of the automated procedure. People generally choose /swap to be 1-2x their RAM. I'd give / 20 gb, and the rest to /home.

---

### Post by guitarista on 2005-04-05
Right , but do I have to set the partitions before/during ( will I be prompted to do so ? ) installation process ? 
To be quite honest , I'm not gonna use the lot ( 90 GB ) for Ubuntu you know ....
I guess I'll create a partition ( FAT 32 ) accessible from both OSs as well .

---

### Post by guitarista on 2005-04-06
Alright , I guess I've got the answer  ;) 
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html)

Cheers .

---

