---
title: "Wizard corrupted my hd during partition"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by Lucas Scoppio on 2008-10-05
hello folks... unfortunatelly I`ve lost all my data today, just a few minutes ago, I was trying to install the ubuntu in my HP Pavilion ze4900 but when I did started the partition of the swap partition the wizard told me that he could not complete the task and sudenly ended... when I first read the ~hd drive C~ partition format it was there ~swap~ and i could not reach any of the archives in it anymore... at the moment im running the ubuntu via CD and downloading to the pendrive any program that may help me but I dont know how to install or run anything in the way i am right now...

 i need help with haste (a few vital files have been lost)

---

### Post by cariboo on 2008-10-05
IF you run the partitioner editor, System-->Administration-->Partition Editor, what do your partitons look like? Do the partitions seem to be in the right order? Open a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and post the output in your next post.

Jim

---

### Post by Lucas Scoppio on 2008-10-05
The partition is ready as a 39GB Swap partition!!!


all I can see in the sudo fdisk -l is

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   82  Linux swap / Solaris

Disk /dev/sdb: 2051 MB, 2051538944 bytes
50 heads, 49 sectors/track, 1635 cylinders
Units = cylinders of 2450 * 512 = 1254400 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1636     2003336    b  W95 FAT32


(he turned my HD in a swap T_T )

---

### Post by Lucas Scoppio on 2008-10-05
i have lost 17GB of data(incuding 2 months of hardware and software development, yeah, shame on me, ive not done any backups), and since this is a notebook i cant place my HD in another pc to recovery the files... I trully need help...

---

### Post by iponeverything on 2008-10-05
see if you can mount the partition with the live CD

mount /dev/sdb1 /mnt

then 

cd /mnt

to see if your data is there.

---

### Post by Lucas Scoppio on 2008-10-05
actualy im using the ubuntu live CD and my Gparted is telling me that the partition is "clean"... and there is nothing inside this mnt folder.

---

### Post by caljohnsmith on 2008-10-05
I would give testdisk a try and see if it can possibly find your previous partition. But before doing that, you never mentioned--what was on the drive before you ran the Ubuntu installer? Did you have Windows? Did you have multiple partitions, and if so, what were they?

---

### Post by tspan on 2008-10-05
Perhaps you were lucky and only partition type was set to 82 (swap) without damage to actual data. In that case you could use cfdisk to change it back (7 for NTFS, 83 for linux, etc.) and then mount it.

Maybe not all of your data was destroyed. You could use some disk imaging / data recovery software to recover your files. I never did it myself on a broken partition so I cannot be of more help. Perhaps [this]("http://en.wikipedia.org/wiki/Data_recovery") could help.

Wish you luck.

---

### Post by Lucas Scoppio on 2008-10-05
I had before the windows XP SP3 running...

only one partition with 39GiB

I'm almost shure that i havent lost my data since I havent installed NOTHING in my computer since the bug... but i need fast help doing that... I have to go to work tomorrow morning and I have to make a choice now... try everything that is possible until I recover my data or just give-up and do everything using the data I have on the internet to reassemble my work :(

---

### Post by caljohnsmith on 2008-10-05
OK, from your Live CD, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give; post the output of that screen. Then do "proceed", N for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. If that screen shows any NTFS partitions, you might be able to recover the partition. Please post the output of that screen too.

P.S. I have to get going in about 5 minutes and won't be back until tomorrow morning (~10 hrs), so I won't be able to help you until then if you still need it. If you don't have any success with testdisk, you can use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" (part of the same testdisk package) to do a deep scan of your HDD and recover files. It's fairly self-explanatory, just run it with:
```
sudo photorec
```
and go through the prompts. good luck.

---

### Post by Lucas Scoppio on 2008-10-05
> **caljohnsmith said:**
> OK, from your Live CD, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:


Its in system>admin>soft... but ok... (i messed up a little till i found out)
 How do I download it? i tried the add/remove but could not find, now im searchng over the "software sources" if there is any tab telling something about "test apps" etc... When you say to enable all "repositories" you mean by marking every single box right? ok... if is it then 'im done (I might remember you that the only "hd" i have now is a pen-drive of 2GB, im running the LIVE CD Ubuntu.

> 
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give; post the output of that screen. Then do "proceed", N for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. If that screen shows any NTFS partitions, you might be able to recover the partition. Please post the output of that screen too.

P.S. I have to get going in about 5 minutes and won't be back until tomorrow morning (~10 hrs), so I won't be able to help you until then if you still need it. If you don't have any success with testdisk, you can use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" (part of the same testdisk package) to do a deep scan of your HDD and recover files. It's fairly self-explanatory, just run it with:
```
sudo photorec
```
and go through the prompts. good luck.

Damn... I'd really needed your help buddy :(

---

### Post by Lucas Scoppio on 2008-10-05
Actually i tried it in my other computer, im also running the linux here...

 I cannot download the TESTDISK cus my livecd is "out-dated" :(

(im in troubles:p)

edit::

maybe not... I did the update of the software list and now the testdisk is installed and running... let me see if i can figure out how to use this program...

I'm havving troubles with the Testdisk... im finding only 2 folders with the same strange name... O.o

 ALSO

 I cant "SAVE" anything cus I dont have enough SPACE in my memory... (since ALL my HD was the same partition) Please... help... >.<

---

### Post by Lucas Scoppio on 2008-10-06
I did it, I transfered everything to my iPod, but I give up, the testdisk cant find a lot of extensions that I have which belong to my most precisous files (the Isis, "Proteus", circuit schematics)... also, ive found a lot of thing that I've deleted with Del+shift and a ton of the archives were duplicated!!! Weird...

ok guys, thanks for helping, but ive to find a few specific files that are diferent extension than those the testdisk can find... so im sending my computer to a technic... =\

edit::

well well... back to work guys, the tech said he cannot help, so, lets makes some bits spin! (lol)

 any tip about any kind of program that may help me with this problem? the Testdisk is out of the ring.

---

