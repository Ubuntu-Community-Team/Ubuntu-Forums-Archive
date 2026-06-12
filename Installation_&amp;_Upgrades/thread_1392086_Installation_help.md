---
title: "Installation help"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by MagnusTP on 2010-01-27
hello=)

after some research i found out that i wanted to use ubuntu full time one my main-PC, maby the laptop too, but the reason i made this thread is that i dont really have a clue, is it like windows that i make one partition with windows and several more with games and movies and sutch? Ive red something about "swap" disck and stuff so i really need some one to show me how to "install" it by that i mean to set up my partitions.like one with swap 2000MB and so on, i found one manual but that one just got me stuck. I have an 320gb hard drive and a 120, the 320 i want as my "main" one

thnx all hope 4 fast answer=)

MagnusTP

---

### Post by dabl on 2010-01-27
Here's a place to start:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by MagnusTP on 2010-01-27
hello dabl thanx fo helping but, its not really what im loking 4 i have read all that befour but its how im going to partition my harddrives

MagnusTP

---

### Post by darkod on 2010-01-27
If you plan to install ubuntu onto the 320GB disk taking up the whole disk (without sharing it with windows), all you need to do is boot with the ubuntu cd, Install Ubuntu option, in step 4 tell it to Erase and use whole disk and in the drop down list select the 320GB disk.
It will install by default one bigger / (root) partition and one smaller swap partition.
Unfortunately if you want to control the sizes of the partition you have to use Manual Partitioning in step 4, and I don't know if you are comfortable with that.

---

### Post by MagnusTP on 2010-01-27
darkod, that woudent be a problem aslong as i knwo witch partitions i need to make... if i coud tell me what i need, and what you recomend

MagnusTP

---

### Post by NardDawg on 2010-01-27
I think ive read somewhere that the swap partition is suposed to be double your memory

---

### Post by hhlp on 2010-01-27
when you come across with partion in ubuntu instalation select manual instaltion :

select the foloow :

20gb for / (root partition)
1.5 x Ram swap
rest of the spaces for /home

---

### Post by MagnusTP on 2010-01-27
1.5 x  u mean 1500mb?

---

### Post by dabl on 2010-01-27
The Kubuntu OS needs a minimum of 6GB, to allow for some growth via upgrades and software packages.  If you keep your data on a separate partition, and symlink that partition to your /home directory, then there's not much reason to go much larger.  On the other hand (and a bit riskier, for a newbie's data) you can just use the entire disk, except for the swap, and let your data live with the OS.

If you want to use "Suspend to Disk", then your swap space needs to be a little bit larger than your installed memory size.  Otherwise, unless you're going to go crazy encoding videos on a quad core CPU, there's no reason to make swap larger than 2GB.  Here's some points on swap:

[http://kubuntuforums.net/forums/index.php?topic=3099574.0](http://kubuntuforums.net/forums/index.php?topic=3099574.0)

---

### Post by MagnusTP on 2010-01-27
now im just

swap: 2gb
/ 40gb
/home the rest like 280gb

that looks cinda right?

Thanx for the help evry one

MagnusTP

---

### Post by darkod on 2010-01-27
> **MagnusTP said:**
> now im just

swap: 2gb
/ 40gb
/home the rest like 280gb

that looks cinda right?

Thanx for the help evry one

MagnusTP

Yeah, looks right. You could also make swap bit bigger, you have the space. Depending on your RAM you should have 2GB swap partition or 150% of your RAM size, if bigger. But this is only if using hibernate function otherwise even 2GB is fine.

---

### Post by dabl on 2010-01-27
That'll work.  ;)

---

### Post by MagnusTP on 2010-01-27
> **darkod said:**
> . But this is only if using hibernate function otherwise even 2GB is fine.


yea i dont know if im going to use it, i saw the post right after i made the instalation i made the swap 2gb

---

### Post by darkod on 2010-01-27
> **MagnusTP said:**
> yea i dont know if im going to use it, i saw the post right after i made the instalation i made the swap 2gb

Don't worry about it. Also, if your ram is less than 2GB hibernate should still work with 2GB swap.

---

### Post by MagnusTP on 2010-01-27
yeah ok=) on this machine its 2gb, so its no problem i think=) well starting to love ubuntu already, reading the pocked book, and want to learn as much as possible=) thnx for the help guys

---

