---
title: "hdd formating problem"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by vicks_libran on 2007-09-13
hey mates
this is my first post in forum and i need ur help
i downloaded ubuntu a month ago but due to lack of hdd partioning knowledge am afraid to install ,
coz i heard lot that during ubuntu installation one wrong click while selecting hdd partion can make my hdd empty
i never used or saw any linux OS running pc...
so what is "/" and swap
kindly guide me :-
i ve 80 GB sata hdd
4 partion of 15-15-25-25 GB each
on D drive i installed my XP PRO
means on 2nd 15GB partion, 3rd partion (25GB)has softwares and my personal datas, and 4th partion (25GB) has songs and games 
My 1st pation (15 GB) i use as xtra for my downloads 
but i wanna install on ubuntu on 1st partion(15GB)

now can u plz tell me which partion/option sud i choose during installation...
how can i recognize my 1st partion(15GB) in ubuntu???
plz guide me mate

> While insalling it say that u have 2 formate u r harddisk.
There was 3 options
1'st say resize the partion (use free space)
2'nd say erace all data
3'rd say manulay
when i choose 3'rd one there was many option's
i was unable 2 install it

---

### Post by djchandler on 2007-09-13
> **vicks_libran said:**
> hey mates
this is my first post in forum and i need ur help
i downloaded ubuntu a month ago but due to lack of hdd partioning knowledge am afraid to install ,
coz i heard lot that during ubuntu installation one wrong click while selecting hdd partion can make my hdd empty
i never used or saw any linux OS running pc...
so what is "/" and swap
kindly guide me :-
i ve 80 GB sata hdd
4 partion of 15-15-25-25 GB each
on D drive i installed my XP PRO
means on 2nd 15GB partion, 3rd partion (25GB)has softwares and my personal datas, and 4th partion (25GB) has songs and games 
My 1st pation (15 GB) i use as xtra for my downloads 
but i wanna install on ubuntu on 1st partion(15GB)

now can u plz tell me which partion/option sud i choose during installation...
how can i recognize my 1st partion(15GB) in ubuntu???
plz guide me mate

You have a unique problem here, in that you wish to install Ubuntu on the first Primary Partition. If XP is not on a Primary Partition as well, that could make things go bonkers. You can't just wipe out your C: Primary partition.  If it was me I would copy over, and I mean make an exact copy, of your D: drive to your C: partition. You'll need to use the disk manager re-assign their designation, and my XP box is downstairs, and I'm upstairs right now, so I can't tell you exactly how.

There's a guy here that used to work for Microsoft, and that's who really needs to help you. I'll send him a PM and see if he's available. Don't do anything yet, until you see a post from wheredidrealitygo.

I forgot to mention. He lives in eastern Canada. He very well could be asleep now. You may have a wait for him, but it will be worth it.


DJ

---

### Post by wheredidrealitygo on 2007-09-13
"/" is your root filesystem, it's basically like your C: in Windows, it's where all your files are installed

Swap is your memory file (like a paging file in windows, it's not RAM, but space on the HDD used as RAM when RAM is all used up), and usually Ubuntu makes a separate partition just for it.

your best bet will probably be to go into windows, and check out the size of your XP HDD and how much space it is using on it's 15gb partition. (right click D:, select properties, look at pink/blue pie chart)

then, when you go into Ubuntu (to install it, this is assuming your going to be using Ubuntu feisty fawn, 7.04, the livecd)

when you get to the partitioning point in Ubuntu, go into manual, and it'll show you all of your current partitions and how much space each is taking up.

use your logic (if necessary write down the figures and post screenshots here) and judge which one of the 15 giggers is using up same size as your XP partition.

Remember: formatted partitions are less than actual capacity, so they may look like 16/17ish gigs.

if it's the D:/ one, it'll assumably be either /dev/sdb1 (if it's a SATA drive)

then all you have to do is logically wipe the other one (so ignore both 25giggers, and your XP one which you've judged from the used up space that you saw in XP), the thing is, you're going to need a swap partition, so delete your Ubuntu partition (if it's first partition, presumably /dev/sda1) and then make two, one of about 12 gig's in ext3 filesystem, and another of about 3 in swap filesystem (using up your 3 gigs left over from your 15, cause you need a swap partition).

you should be good. when deciding to install your bootloader (grub) to the MBR (master boot record), don't delete XP, as XP holds access to your MBR, so you wouldn't be able to boot into anything until you fixed it.

Good Luck!!

---

