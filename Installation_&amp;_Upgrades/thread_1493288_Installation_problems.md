---
title: "Installation problems"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by theairsickness on 2010-05-25
Hi!

I'm extremly sorry in advance if this has been brought up before.
But i've really tried searching, and i've done it extensivly.

I'm trying to install ubuntu x64 in all different version, everything from 8 till 10.04.
But I never succeed.

I'm having the common problem of that when I get to the partioner, the installation hangs.
This happeneds with the alternate and the live cd.

I have had this problem before, but somehow back then I managed to get it working.
Can't remember how though.

Anyhow, I have replaced my harddrive with an 'old' seagate drive that was in my macintosh.
And i've done everything from trying to change partition table, to delete the MBR without any success.

So i've turned myself to the forum, something I usually don't do. I am one of those happy campers that usually find everything through google.

Anyhow, you might want some specs.

It's an intel quad processor 
Asus P5QE motherboard.
And the seagate harddrive

If you need more extensive hardware specs, i'll bring them forward.

All the help i appriciated!

Thanks

---

### Post by darkod on 2010-05-25
Are you able to run the 10.04 cd in live mode?

If you can, open Gparted and try to write new partition table, just in case. If the disk was used in a Mac the partition table is probably GPT and that doesn't go away with formatting. You need to write DOS partition table over it.

Alternatively, do:

sudo fdisk -l

and it will show the partition types and usually there is a message if GPT is used.

Once you are sure that's out of the way, let us know if any specific issues appear when trying to install.

---

### Post by theairsickness on 2010-05-25
Yea, I can get into the livecd, even though it says that something has failed and it want to start a desktop session instead.

So i've installed a MSDOS partition table on it.

No difference, it still hangs when you try to go past the keyboard.

It's starting to get a little bit annoying, I'm not getting any problems if I try to install windows on it.

Any more tips?

Thanks

---

### Post by rob45 on 2010-05-26
Hi im no expert in ubuntu....can you just clarify for me..when you say the pationing bit do you mean the first part...where it asks you how how much of the disc you want to use....im gathering ..i think that this hard drive is empty so are you defining partions or are you just telling it to use all free space...thats your best option..i think...to let it use all free space.

---

