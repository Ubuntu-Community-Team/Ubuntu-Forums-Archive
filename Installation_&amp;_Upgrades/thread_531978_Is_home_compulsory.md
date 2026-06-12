---
title: "Is /home compulsory?"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by bdsatish on 2007-08-22
Hi,

     During the partitioning process, is it compulsory to create /home ?
If yes, how much GB should i allocate to it?

I'm thinking for 20 GB for complete ubuntu install. SO, i thought,
18 GB for  / ("root") and 2GB for swap.. Is it ok ?

---

### Post by Dark Star on 2007-08-22
20 is more than enough for Filesystem .. and For swap just double the size of swap with the amt of Ram.. Suppose I have 256 MB ram so I would put 512 Mb space for swap though I had 1 Gb :lolflag: .. Btw more space for File system is not good ... You even can put 25 Gb if you add more programs :D

---

### Post by bdsatish on 2007-08-22
OK.. dats gud!

But will a "/home" be automatically created if I create "/"  ?

---

### Post by Dark Star on 2007-08-22
Yep :) "/" for file system will always creat a /home for user :D Just like Docs and Settings :D

---

### Post by bdsatish on 2007-08-22
Thanks dude !  
 :popcorn:

---

### Post by Dark Star on 2007-08-22
> **bdsatish said:**
> Thanks dude !  
 :popcorn:
My pleasure. .Do check out forum for further problem :D

---

### Post by bdsatish on 2007-08-22
Just to elaborate.....

What are the compulsory partitions ( i.e. "/"  , "swap", etc. ) that must be present in a minimum ubuntu-install ?

"/" and "swap" are enough right ?

---

### Post by Outrunner on 2007-08-22
Yes, / and swap are the only necessary partitions. However, it is recommended to create a separate /home partition as well(If you decide to reinstall, you will be able to do so without deleting your previous programs/config files).

---

### Post by bdsatish on 2007-08-22
Oh K.. If dat is the case, how much GB is ideal for "/home" (assuming i create one) ?

---

### Post by TheMono on 2007-08-22
Personally, I like to have about 6 gig for the / partition - it normally does it for what I need installed. Really, you will have most of your data on your /home partition, so you are better off figuring out how much you'll be installing program-wise (in my case, about six gig), and then just use the rest for /home

---

### Post by Outrunner on 2007-08-22
> **bdsatish said:**
> Oh K.. If dat is the case, how much GB is ideal for "/home" (assuming i create one) ?

How big is your HD? Anyway, generally, it's good to make it as big as possible. Like you can give the / partition 15GBs and the swap partition 1GB and give what's left to the /home partition.

---

### Post by bluenova on 2007-08-22
> **Outrunner said:**
> How big is your HD? Anyway, generally, it's good to make it as big as possible. Like you can give the / partition 15GBs and the swap partition 1GB and give what's left to the /home partition.

15Gb is un-necessary, a basic install will only need 2Gb. I'd say 6Gb will be the most that is needed for /.

---

