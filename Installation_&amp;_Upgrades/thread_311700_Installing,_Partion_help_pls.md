---
title: "Installing, Partion help pls"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by DizzyBro on 2006-12-03
Ok well i get thru most of th installation, when it asks about hte partitions. i have 3, 1 (my winxp) 102 gigs, 2 (my games partition i made :P) 25 gigs, and 3 (for ubuntu) 25 gigs.


it asks for like which should be a swap and a root or something? i dont understand. i want to install it all to the 3rd drive...and it asks for like a code in the left hand side of the thing or something which by default have been 

these are probably spelt wrong.

/music/spm1
/music/spm2
/music/spm3


can someone tell me what i have to do?

---

### Post by sitedesign on 2006-12-03
If you select manual partitioning then you will see the partitions with the sizes against them, you should be able to then decide which one to use.

It should be as simple as selecting the 3rd partition in numeric order:
/dev/sda1 (windows)
/dev/sda2 (games)
/dev/sda3 (Ubuntu)

hope that helps.

If not then write down the list presented to you and post that back here.

---

### Post by DizzyBro on 2006-12-03
yeah, i do manuel, and i select the ubuntu drive. but then it prompts me for a root as "/" and some swap thingy...now what

---

### Post by sitedesign on 2006-12-03
set aside say 10GB for root / and set it as ext3
then create a swap partition as type swap of say 1GB as extended
then the rest as home as ext3 type extended.

---

### Post by DizzyBro on 2006-12-03
set aside say 10GB for root / and set it as ext3
then create a swap partition as type swap of say 1GB as extended
then the rest as home as ext3 type extended.


ok well with the ubuntu partition, can i set it as both root and swap? and how do i set them as ext3?

and i still don't understand the root / thing...do i just put in / for that partition?

---

### Post by Gremlinzzz on 2006-12-03
theres another way create a 10gb partion then delete it. this will make it free space.then when installing ubuntu at partion choice choose largest continuous free space.then ubuntu will do the rest.swap home the whole nine yards.

---

### Post by yuanfangcan on 2006-12-03
Maybe partition automatially is better. if you chosse partition automatically, you only need to tell it where do you want to install ubuntu, then the install process will partition swap and / automatically on the partition you just decided.

---

### Post by DizzyBro on 2006-12-03
> **yuanfangcan said:**
> Maybe partition automatially is better. if you chosse partition automatically, you only need to tell it where do you want to install ubuntu, then the install process will partition swap and / automatically on the partition you just decided.

ok i donno what ur talking about. this isn't the beta and umm...i am talking about mounting the Preparing Mounting points section.

i have never seen partition automatically, and i made my patitions with norton partition magic 8 pro

---

### Post by Gremlinzzz on 2006-12-03
seems i misunderstood. i thought you were trying install ubuntu as a dual boot.my post just suggested you let ubuntu set up the partition.

---

### Post by DizzyBro on 2006-12-03
..i am dual booting...but i already had the partition set up. i jsut wanna install it to drive X (empty one for Ubuntu) but the only way i can is by figuring out how to mount the stuff or w/e. asks me where to mount them and i have no idea what to put to put everything in drive X

---

### Post by jonyboy1000 on 2006-12-03
Do you mean that you see a square at the top of the install box (which shows your 3 partitions?). If so click next and it will then ask you where you wish to mount them. You will still need to create a swap partition though.

---

### Post by DizzyBro on 2006-12-03
YES! i do mean that part, but I DONT KNOW HOW TO MOUNT THEM/WHERE!!

---

