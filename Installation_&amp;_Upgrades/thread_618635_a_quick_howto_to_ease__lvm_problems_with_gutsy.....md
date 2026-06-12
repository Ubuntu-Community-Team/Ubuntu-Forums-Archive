---
title: "a quick howto to ease  lvm problems with gutsy.....hope this helps"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by porphiron on 2007-11-20
Right folks, all this may seem obvious to most, but it wasn't to me.

Background:

I wasn't going to upgrade my media server to gutsy just yet as it sort of worked fine with feisty.
  The only problem was, I use lvm to strap a load of drives together and lvm under feisty was a bit of a bitch, with the only gui without a lot of faf was the evms gui and to be frank......it stinks.

I then began to run out of space so opted to use an external HDD....yeah not the best idea but i'd also run out of ide slots so...feh...i know some people have had issues but i tested it and it seemed to work fine and i made sure that even if the drive was lost at boot, the whole lvm setup would be remounted at the end, by a little script in rc.local (basically sleep10;mount <mountpoint>)...again this may seem a trifle rubbish, but it worked for me. 

Originally I had been a suse user up to 9.3 but after the debarcle that was 10 and all the tat thereafter I dropped it like the  joke dog turd that turned out to be real. evmsgui was a total pain but i had managed to get another external hdd to work in an lvm volume on another machine and hoped i could replicate the trial and error that to took to get it working, and some how, i actually managed it..or so i thought. 

All worked ok until i reached the end of the internal hdd space and the computer should have started using the external section but no joy no matter what, even tho evmsgui stated the partiton was using both internal and external drive space I kept hitting the wall of the internal drive space so....to the meat of the matter i opted to install gutsy to see if it would help...it did....eventually

Hopefully helpful bit:

I used the alternate install cd of xubuntu (i always use the alternate cd as there is a vast array of install options, it seems flexible and hell bent on shoehorning itself onto yer system!).

I hit my first snag when using the partition editor it stated that the external drive had no lvm partiton (ERK!)....no worries i just selected the option to use the drive as an lvm drive...all well and good...the install worked fine.

once done i installed the lvm2 package and gparted (I'le come to this in a bit)

great,all the lvm volumes showed up, including the one that caused most of my hairloss, but the problem was df -h was showing only half of what the problem partiton should have been but gparted showed the whole lvm partiton as it should have..........yes you read that right GPARTED NOW READS LVM VOLUMES AS A PROPER DRIVE PARTITON AS WELL AS BEING ABLE TO VIEW EACH PHYSICAL  DRIVE ATTACHED!!, which means lvm partitons can be shrunk or grown just like any other partiton and so, lvm volumes are now transparent within x/ubunutu, problem was it was saying the volume was full!!.......well for the sake of experimentation i was willing to trash the drive to bring you this info.

I decided to let gparted run riot on the partiton and fsck it.

I waited, drive lights blinked and I waited some more, drive lights went out and a list of errors
sprouted and the drive lights blinked again....i popped another can open and....waited until..

lo behold i now have a properly working lvm volume........

GUTSY RAWKS MAN!

I hope people can pick bits of usefull info from this mountain of drivel, as there seems to be a lot of lvm questions unanswered in the forum.

cheers 

Porph!

footnote:

Am now pondering wether its possible to grow an lvm volume onto another drive using GPARTED...will let you know

---

### Post by stokkes on 2007-11-21
If I'm not mistaken (and by no means am I an expert in this area), but wouldn't Reiser be a good FS to go with?

You could add the drive to the LVM and just "grow" the partition with resize_reiserfs? I know many people who do this with hardware based RAID arrays (using OCE).. basically, they add a drive to the array, fdisk the array disk, delete the partition, recreate it (making sure it always starts on the same cylinder) and then just run resize_reiserfs on it to grow/fill the space.

EDIT:
the above method DOES NOT erase your data. In case anyone who's reading this doesn't know, you need to run fdisk to delete/recreate the partition (starting on the same cylinder, otherwise you will most certainly muck up your data) in order for Reiser to detect the extra space given to it by the addition of another disk.

---

