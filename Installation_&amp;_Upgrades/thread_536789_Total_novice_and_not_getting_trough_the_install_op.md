---
title: "Total novice and not getting trough the install options at all...."
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2007-08-28
I'm trying to install Ubuntu 7.04 on a partition on a third harddrive on my system.
The first two (one on wich there is a WinXp OS...which needs to stay intact) are older ATA disks. The third one is a newer Sata disk on wich I have a 50Gig partition that is formatted as NTFS but wich I would like to use for Ubuntu.

When I hit the install button I am asked for my language and keyboard layout.
Then I go directly to how the install choices of the harddrive, I seem to be missing the page where I have to fill out my personal details and passwords.

The next screen is one where Ubuntu tells me to prepare my harddrive.
option 1 is to rezise my SATA disk (wich is called a scsi disk ?, and is divided into two partitons, one being250 gig and one being 50 gig), why doesn't it take the windows partition by the way ?
option 2 is the guided option where I get to choose between the 3 disks, but that mentions it uses the whole disk and I want it to be only a partion so that doesn't help
option 3
Since I want a dual boot system I should be choosing the manual method.
when I choose that I get a view containing all the partitions on the various disks.
I think /dev/hda1 ntfs /media/hda1 is the windows partion and  /dev/sda2 ntfs media/sda2 is the on I'd like to use.
should I delete the partition or edit it ?
if I choose edit I get a screen asking me the size of the new partition and how I'd like to use it, I guess it should be ext3.
It also asks the mounting point, it's default is media/sda2, the other options are /DOS and /windows.
when I try to do something it tells me all changes are permanent.
how should I continue here ?
I don't get the option to install root, swap and home files and I haven't got a clue where to mount to, media/da2 or windows to be able to dual boot.

help is urgently needed !

---

### Post by vikramsharma on 2007-08-28
Don't know if this would help, when I have to make a dual boot system I delete the partition so I would have one NTFS partition and unformatted space which I would use for the purpose of installation.  You can use the disk management utility provided in Windows XP to delete the partition you want to use for installing.  So when you want to install Ubuntu, you can go for the "Use Free Space" option.  One more thing for linux to be bootable,the linux partition would have to be primary.  I hope what I said in here was helpful and that I haven't confused you even further.

---

### Post by kellemes on 2007-08-28
If you want to go manual with the 50Gg partition you better delete is first..
Then you can create new partitions one by one..

There are a gazillion ways of doing this but this is one..
1- One swap partition of 2 times your memory with a maximum of 2Gb.
2- One partition of 10Gb and mount as / (ext3)
3- One partition of 20 and mount /home (ext3)
4- One partition for sharing maybe? (ext3=available through Windows also, just install ext3-driver)

Listen, if you need to resize partitions in the future you can do this easily.

---

### Post by Hagar55 on 2007-08-28
thanks for the help by the way, I deleted the 55 gig partition in windows. Then choose the use free space option from the installation menu.

Now when I go in windows disk manager I see two unrecognised partitions, one is 52 gig big and the other is 2.5 gig big.

I'm guessing that the 2.5 is the swap folder.
What is the other one, root or home ?
And why aren't there 3 partitions for Ubuntu  (root, swap and home) instead of 2 ?

Am I missing something here ?

How do I see what the different partitions are in Ubunt ?

---

### Post by merlinus on 2007-08-28
You will have to manually create the /home partition.  Only / (root) and /swap are created automatically.

More info here:

[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

-merlin

---

### Post by Hagar55 on 2007-08-29
I don't feel like reinstalling Ubuntu over again.
Is there a way to resize the root partition and use 35 Gig of it for a new home partition ?

If so is there a defragmentation I need to do, and if so how.
And what program do I use to resize/ create the new partition ?

---

### Post by merlinus on 2007-08-29
Info here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

but there are a number of folks who have had problems following this successfully.

No need to defrag linux partitions.

Use gparted live cd to resize and/or move existing partitions:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Hagar55 on 2007-08-31
I downloaded the ISO of gparted and burned it.
When I boot it starts of well, but stops at the last screen before (according to the documentation of the website) it should swithch to graphical.
so I'm stuck with gparted ~#_

anyone have any idea what is going wrong, or does it just take very very long for it to swtich to graphical ?

---

