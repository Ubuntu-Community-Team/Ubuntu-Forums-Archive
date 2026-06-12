---
title: "setting up a partition on raid0, 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by ApakSL on 2012-04-26
Hi, I've tried searching the forums and google, but I cant find any info for my particular problem. Also, I'd like to apologize in advance for butchering all the lingo, I'm not too familiar with all the different types of partitions.

I have 2 hdd's in raid0 partitioned by my mobo's raid controller into 2 volumes with win7 installed on one of them. I'd prefer not to mess with that setup because I dont have an easy way of backing up all my stuff.

I partitioned off a chunk of unallocated space on one volume with the hopes of installing ubuntu on it as can be seen **_[COLOR="Red"][here.]("http://i216.photobucket.com/albums/cc153/apaksl/computermanagement.jpg")[/COLOR]_**

I'm having trouble going through the manual partition menu (12.04 64-bit, alternate install disk). I've never installed linux before, but I get the impression that the installer is only seeing one of my two drives even though I told it to enable raid. [COLOR="red"]_**[Here's a pic.]("http://i216.photobucket.com/albums/cc153/apaksl/2012-04-26125827.jpg")**_[/COLOR]

I would imagine it should either show two 1tb hdd's or show two volumes of differing size (one is 500gb, the other is 1.5tb), or even better, show my unallocated space of 300gb.

Thank you for reading and for any help :)

-Nick-

---

### Post by jadtech on 2012-04-26
i belive as I understand it and im no expert at all never did this type of set up .. 

raid is 2 hard drives how ever the alternate cd sets up a fake raid, raid uses both disk for all the same info they are mirrors of each other, ubuntu will only use one primary  disk to install it dose not use both like windows ..

---

### Post by ApakSL on 2012-04-26
does that mean that I should use the regular setup disk then? would the regular setup disk find an unallocated partition on my raid volume?

---

### Post by jadtech on 2012-04-26
no the regular disk wont work for you , as far as I can tell what you have is how its supose to be,  though waiting if you like for someone who has done this to confirm what you have there is correct :)

---

### Post by darkod on 2012-04-26
Actually you are supposed to use the alternate cd for better raid support. But the live cd can also read fakeraid (bios raid) arrays.

You are right, it seems it detects it only as one single disk. The other is not shown even as a separate disk. Very weird...

And the disk that it detects, it detects it as LVM, not as raid.

Are you sure you have a standard fakeraid, not some kind of windows software raid?

You can try booting into live mode with the live cd and see if that shows the array. You may need to activate it first in live mode with:
sudo dmraid -ay

I am not sure.

---

### Post by ApakSL on 2012-04-26
So, yeah, I guess mobo raid controllers are "fakeraid". I never knew that. I am sure that the raid is set up through the bios, though. Thanks for the input

---

