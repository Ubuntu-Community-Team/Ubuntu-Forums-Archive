---
title: "Ubuntu cant detect my C drive on install"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by 2598matt on 2008-06-29
Okay I'm trying to install Ubuntu onto this old crap computer and its good so far till be get to where we must select a "partition" and appairinlty your supposed to click the C drive but its just blank.. Any help?

---

### Post by untermensch on 2008-06-29
Can you be a bit more specific? is it not finding the drive at all? or does it not see the used\free space? you know not all drives are called C correct?

---

### Post by 2598matt on 2008-06-29
Its just blank... I hit forward and it will say "Please choose a partition" or something like that but there is nothing to select... Your supposed to click a radio button or something and hit forward but there's just nothing.. Just white blank field...

---

### Post by untermensch on 2008-06-29
So, when you get to step 7 or whatever it is that you get to the partition table, there are no devices to choose?

---

### Post by 2598matt on 2008-06-29
Exactly. I cant find any answers for this...

---

### Post by untermensch on 2008-06-29
What type of partition is currently on the "c" drive? fat32 or NTFS?

---

### Post by 2598matt on 2008-06-29
Umm what do you mean?

---

### Post by 2598matt on 2008-06-29
Its FAT32

---

### Post by untermensch on 2008-06-29
eek. So, is there anything there that says like /hda1? or anything like that?

---

### Post by 2598matt on 2008-06-29
One minute i'm going to go check the computer... Maybe its just slow as a sloth...? BRB

---

### Post by untermensch on 2008-06-29
Are you installing off of a livecd? Maybe you should try the alternate CD, it's usually a little better at picking up hardware.

---

### Post by 2598matt on 2008-06-29
Nope... Nothing... Just blank...

---

### Post by untermensch on 2008-06-29
I definitely would recommend the alt cd at this point. It's pretty good about detecting bad hardware. =p as I already said

---

### Post by 2598matt on 2008-06-29
> **untermensch said:**
> Are you installing off of a livecd? Maybe you should try the alternate CD, it's usually a little better at picking up hardware.

Yes im installing off a live CD but what do you meen by alt. CD?

---

### Post by untermensch on 2008-06-29
It's basically the bare bones of an Ubuntu install. There's no pretty GUI affects or nice things you can do. It's all basic graphics and simple white and black. But it gets the job done.

---

### Post by 2598matt on 2008-06-29
How do you get it?

---

### Post by untermensch on 2008-06-29
There should be a link on ubuntu.com 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

At the bottom where you select the location there is a small box, beside it tells you to click if you want the alternate cd. Check that box, and you'll have to burn the iso and put it on a cd and begin install.

---

### Post by zakirs on 2008-06-29
try downloading it from the ubuntu page there is a check box for it

---

### Post by 2598matt on 2008-06-29
When done installing will it still look like Ubuntu?

---

### Post by untermensch on 2008-06-29
burning the ISO or installing from the alt?

Yes everything will be identical once it's installed. The only difference is you don't have the RAM hog of a live cd, and it's actually a little faster.

---

### Post by 2598matt on 2008-06-29
Okay thanks... Ill go burn the image.. And if everything is'nt all well, ill come back and ask for help... But thanks guys. :)

---

### Post by untermensch on 2008-06-29
No problem =p glad I could be usefull. If you need more help start a new thread, or post on this one again (I'd advise the second one). Hope the alt. cd works for you though, and you wont have to come to this post.

---

### Post by 2598matt on 2008-06-30
Nope still doesn't work... I'm about to just give up... Ubuntu is way more complicated setting up then its worth to have it..

---

### Post by untermensch on 2008-06-30
NO! that's crazy talk. I had a lot of problems installing, I actually ended up using wubi. maybe you should try wubi ? I thought just like you.. to much work, but now I love it! wubi would be good especially since you're already mad at Linux and are more likely not to use it.

---

### Post by 2598matt on 2008-07-02
Okay... That's what I was thinking about doing... First I got to buy a modem and a phone cored for upstairs... HERE I COME HIGH SPEED! WOOT! (Just one problem... My windows got formatted so.. idk how I'm going to use wubi... :( )

---

### Post by untermensch on 2008-07-02
reinstall windows? not sure on that one =[

---

### Post by 2598matt on 2008-07-02
omfg it is hard as hell... Ive tried over.. let me see.. 1.. 2.. 50!!! TIMES!!!!!! I'm just thinking of getting these old 98's from my work and using the Live CD on them...

---

### Post by untermensch on 2008-07-02
why just use the liveCD from them?

---

### Post by 2598matt on 2008-07-02
I dont wanna hook up the internet up to them.. im lazy

---

### Post by david_s_02330 on 2008-07-09
I'm experiencing the same problem.

I've tried installing Ubuntu twice on two different drives.

I'm using Ubuntu version 8.04 AMD64.

Neither disk is recognized by GParted version 0.3.5.

Both drives are EIDE type.

---

### Post by 2n01cal on 2008-07-09
Hey, I have similar problem, now I am writing from LiveCD Ubuntu 8. My GParted is showing that whole my 250GB disk is unalocated with no partitions, but this is wrong. I have 4 partitions there and Windows is working fine.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a93b30f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20480000 7 HPFS/NTFS
/dev/sda2 2550 15298 102400000 7 HPFS/NTFS
/dev/sda3 15299 30402 121316160+ 5 Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4 15299 17847 20474811 7 HPFS/NTFS
/dev/sda5 17848 30402 100835328 7 HPFS/NTFS


But Gparted is showing all space Unalocated, so I can't install Ubuntu =/ Ubuntu 7 was fine and 6 also.

---

### Post by 2n01cal on 2008-07-09
ok, sorry, solved. I deleted empty partition 3 and formated it back to NTFS and everything is ok now.

---

### Post by david_s_02330 on 2008-07-10
My issue was solved by changing the jumper settings on the drives.

My jumper settings were set to "Master with Slaves". However, I didn't have any slaves. Once I changed the jumper settings, gparted recognized the disks and associated partitions.

---

### Post by Jericon on 2008-07-13
I am having this same issue.  Cent OS 5.2 Install DVD recognizes the drives no problem.  Ubuntu Alt CD stops after doing something with PCI.  I have 2 SATA Drives, one is already ext3 formatted (Storage) and the other has 1 partition for Windows on half the drive, the other half is unformatted.

I have checked the Jumpers on my drives, they are all set correctly (no jumpers = full speed).

Any ideas?

---

