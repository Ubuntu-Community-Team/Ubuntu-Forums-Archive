---
title: "NVraid possible for kubuntu (feisty)?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Mack1 on 2007-05-06
Hi,

I've installed kubuntu 7.04 (feisty) and it works like a charm. 
I am dual-booting it with windows xp pro.

Under windows xp pro i have drivers running so i can acces my nvraid configuration.

My kubuntu / windows xp is installed on a s-ata disk while 2 other 320gb seagate disks are in a
nvriad (1) configuration. Keep in mind that my OS isn't installed on the raid drive(s)!

However, when i fire up windows xp from scratch, it sees the raid and it works fine. But when i 1st
boot up kubuntu, no raid drives are found and when i reboot into windows xp the raid drives are also
not present in windows xp....

I'm at a loss, is there anyone who can help me getting my nvraid drives to work in kubuntu like they
do in windows? Preferably without the need to reformat them (although i think that's manditory...)

More and more my windows box is only used for gaming and i'd really like to be able to use everything on
kubuntu!

Thx for replies...!

---

### Post by Mack1 on 2007-05-11
Anyone?

Someone must know how to get it going?

---

### Post by RAOF on 2007-05-11
It is possible, try [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) - NVraid is essentially software-raid, and dmraid supports it.

---

### Post by Mack1 on 2007-05-17
hi roaf,
thx for the reply.

i wll take a look at it!
as far as i see now it's only for also booting from the raid, this i do not want.
i want to run a fileserver using 2 harddrives in raid 1 config and the os uses a seperate 80gb sata2 drive.

thx again i will have a read. 

if anyone knows how to get it running wihout booting from the raid drives plz let me know...

---

### Post by Mack1 on 2007-05-18
Right, the strangest thing happened.

I tried to run compiz on my feisty kubuntu system, which only partialy worked.

Being a noob i decided to reinstall kubuntu.

Once it was reinstalled, VOILA! my raid drive was there! don't know how but now i can 
read from it just fine. it is ntfs so writing is still not done but reading is ok.

Strange, because he wouldnt even see the drive @ the last install....

---

