---
title: "Installing Ubuntu with 2 Hard Drives"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by mustang on 2006-02-18
Hi all,

I would hope I'd know the answer to this question but I don't want to take any risks so here I am.

I have two hard drives on this computer right now:

**C: Drive -- Primary -- Contains WinXP (FAT 32) -- 31GB/40GB used**
**D: Drive  -- Secondary -- Contains some files that I would like to keep (FAT 32) -- 59GB/148GB used**

Now I have a lot of free space on D and plus it doesn't contain anything crucial to my WinXP install so naturally I'd like to install Ubuntu on that.

Now I went to [URL="http://users.bigpond.net.au/hermanzone/p2.htm"]this
[/URL] guide and tried to follow the instructions but I got stuck.

I got to this step
[IMG]http://users.bigpond.net.au/hermanzone/p2/i0916op.gif[/IMG]

**Note that's just the picture from the guide, mines a little different**

Here's where I get stuck: that prompt above only shows me an option to Resize my primary (40GB) hard drive and use the free space on it. It doesn't give me an option to resize my bigger D drive and use the free space on it (which is what I would like to do). 

How can I get the partitioner to include that option as well? If that is not possible, do I have to manually edit the partition table (which is something I'd rather not get into)??

Thank you very much,

Manish

---

### Post by Xecuter on 2006-02-18
What i did was make a partition on the D: drive for 20GB. You might use something else. So when i ran the ubuntu setup I devided the new partition into: 
 - 5GB for the root system
 - 2GB for the swap partition (twise my amount of RAM, some say you only need 512MB)
 - And the 13GB to the /home system, where all personal files will be stored.
You have to press "Manually edit partition table" to do this.

Hope it helps :)

---

### Post by jsestri2 on 2006-02-18
Just a thought...

I have 2 SATA drives with essentially the same setup, (winXP on one drive and the other is actually brand new), and when I was installing ubuntu, I was getting a lockup at GRUB installation 0%. I had to unplug the winXP drive in order to get past that point.

I don't know if this will effect you, but I figured I'd point it out, so you don't have to go searching the net like I did, and then guess to solve the problem.

---

### Post by mustang on 2006-02-18
[QUOTE=Xecuter]What i did was make a partition on the D: drive for 20GB. You might use something else. So when i ran the ubuntu setup I devided the new partition into: 
 - 5GB for the root system
 - 2GB for the swap partition (twise my amount of RAM, some say you only need 512MB)
 - And the 13GB to the /home system, where all personal files will be stored.
You have to press "Manually edit partition table" to do this.

Hope it helps :)[/QUOTE]

How did you make the partition on your D Drive for 20gb? 

I'd like to avoid manually doing anything at all costs. Is there no way possible for the partitioner in Ubuntu to resize my D drive and use its free space?

---

### Post by jsestri2 on 2006-02-18
The best way to accomplish that is most likely something like PartionMagic that can be used under Windows, or i believe can be run from a boot disk...

Resizing partions on a single drive is always a risk though. and thus you probaly want to back up anything you can. When I looked I found nothing that will just do it for you for the simple user, so make sure you know what you're doing before trying anything.

I actually had the same issue, and I ended up just getting another drive. If you can affoard the price there are some really good deals out there on harddrives. A week ago I saw a 250GB seagate for only 80$, so something like that may be your best option.

---

### Post by mustang on 2006-02-18
[QUOTE=jsestri2]The best way to accomplish that is most likely something like PartionMagic that can be used under Windows, or i believe can be run from a boot disk...

Resizing partions on a single drive is always a risk though. and thus you probaly want to back up anything you can. When I looked I found nothing that will just do it for you for the simple user, so make sure you know what you're doing before trying anything.

I actually had the same issue, and I ended up just getting another drive. If you can affoard the price there are some really good deals out there on harddrives. A week ago I saw a 250GB seagate for only 80$, so something like that may be your best option.[/QUOTE]

Thank you for the reply jsestri2 but there's no way I can buy a new hard drive right now. 

As for using partition magic, I've had bad experiences years ago with it and I'd rather not use it again. I don't have a DVD burner on here and no other computers on the network so I'm not in a position to backup material either.

Is there really no easy way to install Ubuntu in my situation? I'd imagine tons of other people have been through my position...

---

### Post by cilynx on 2006-02-18
The Ubuntu 5.10 Live CD has 'gparted' on it.

Boot the Live CD and use gparted to resize the drive.  It's all pretty like PartitionMagic, it just actually works.

---

### Post by jsestri2 on 2006-02-18
As far as I know, the ubuntu partioner is a fairly simple partioner, and the option to resize the drive safely is not there. That leaves you with the two options I suggested. I don't happen to know of any other possibilities. The one thing i'd have to say is that if you have a good disk defragmenter you make be able to get your data on the D drive pushed to the beginning of the partion since you said you don't have any windows important files on it (meaning the defragmenter should be able to move everything), making a resize with something like PartionMagic fairly safe.

Going back to the third hdd idea, a quick search turned up this 20GB hdd, you may be able to find a better price, this was just the very first i found: [http://www.newegg.com/Product/Product.asp?Item=N82E16822148051](http://www.newegg.com/Product/Product.asp?Item=N82E16822148051)
this would give you your 20GB for under 50$.

Unfortunately these are the only options I know of. If anyone else has any ideas, please jump in.

---

### Post by Xecuter on 2006-02-18
I had to buy a new hddd since the first one is only 40GB.

But if you do this:
[QUOTE=jsestri2]The one thing i'd have to say is that if you have a good disk defragmenter you make be able to get your data on the D drive pushed to the beginning of the partion since you said you don't have any windows important files on it (meaning the defragmenter should be able to move everything), making a resize with something like PartionMagic fairly safe.
[/QUOTE]
I think you'll get a lucky ending. Because a fragmented disc have files stored all over, and the last time you used PartitionMagic you might have cut of some files, which would be a problem.

---

### Post by cilynx on 2006-02-18
GParted handles all of the frag issues for you.  Thus the "actually works" comment.  It takes it quite a while to resort your data, but the end product is fantastic.

---

### Post by mustang on 2006-02-18
[QUOTE=cilynx]GParted handles all of the frag issues for you.  Thus the "actually works" comment.  It takes it quite a while to resort your data, but the end product is fantastic.[/QUOTE]

I downloaded an Ubuntu live disc and started gParted. When I went to hdb1 (my d drive), I right clicked and went to resize. 

However, it would not let me resize the D drive. It gave me: "Unable to read the contents of this filesystem!" I googled around a bit and I found out that gParted (atleast natively) doesn't support NTFS and gives this same error. But my D drive is FAT32 so I am confused. Furthermore, it says my D drive is completely empty so obviously it is not reading the drive correctly.

Any help would be appreciated.

Note: It was able to read my C drive (hda) fine and would even allow me to resize it.

---

### Post by Herman on 2006-02-19
I would guess (from what I have read) that some partitioning software you might have used some time ago has written something on the partition table of this hard disk that none of the 'parted based partitioners agree with or want to look at. It could be that it is something outside thier tolerance range. It is probably not safe to partition this disk.

It "*might*" be okay to use the same partitioner you used once before to do it, since that one is the one that wrote the suspect partition table, it should be able to change it. Obviously Windows seems to recognise it alright. 

You should have your data backed up before doing any partitioning. Sometimes further changes to an already dodgy partition table will throw it out completely. :-k (Herman)

---

### Post by mustang on 2006-02-19
[QUOTE=Herman]I would guess (from what I have read) that some partitioning software you might have used some time ago has written something on the partition table of this hard disk that none of the 'parted based partitioners agree with or want to look at. It could be that it is something outside thier tolerance range. It is probably not safe to partition this disk.

It "*might*" be okay to use the same partitioner you used once before to do it, since that one is the one that wrote the suspect partition table, it should be able to change it. Obviously Windows seems to recognise it alright. 

You should have your data backed up before doing any partitioning. Sometimes further changes to an already dodgy partition table will throw it out completely. :-k (Herman)[/QUOTE]

Herman, thank you for your reply.

Your remarks are interesting. The only software I've used to partition the hard drive was the Western Digital CD that came with the hard drive. 

I should probably follow your advice and backup everything. Since I can't right now, I'll probably have to foreinstall the Ubuntu installation for now.

One last q---do you think using the gParted live disc would remedy anything? Perhaps there is a newer version on the disc than the one on the Ubuntu live disc.

---

### Post by Herman on 2006-02-19
> I should probably follow your advice and backup everything. Since I can't right now, I'll probably have to foreinstall the Ubuntu installation for now.
One last q---do you think using the gParted live disc would remedy anything? Perhaps there is a newer version on the disc than the one on the Ubuntu live disc. Here is just my opinion from reading on these matters, and adding my own observations to experiences reported by users at these forums. This will not be scientifically factual, and someone may correct me on this. I am just learning myself.
[http://www.ranish.com/part/primer.htm]("http://www.ranish.com/part/primer.htm")
[http://www.ata-atapi.com/hiwtab.htm]("http://www.ata-atapi.com/hiwtab.htm")
It seems to me that different brands of partitioners 99.9% agree with each other on what is to be written to the partition table when they partition our disks. Normally one brand of partitioner has no problems with what another brand has done. 
There many other types of partitioners out there in the big world and it would fill a large book if all were tested and evaluated. Some are popular and widely used, others are more obscure. (Even to other sofware developers).
We users cannot usually see what the partitioning software has actually written on the partition table and would be not able to make any sense out of it anyway. We only get to see what the software tells us.
It could be that there is no 'right' or 'wrong', just the odd difference of opinion by the people who write the software, (or a tiny bug or two here and there). I would imagine that most designers of partitioning software do try to make theirs compatible with the majority of others though.
Nevetheless, even a tiny variation in the way different one partitioner handles a task can lead to disagreements or incompatabilities, (fortunatley this is relatively rare).
This does not necessarily mean someone's hard disk is 'bad' or one brand of partitioner is 'right' and the other is 'wrong'. There is just something there that isn't agreed on. 
I have had the experience after using a whole coctail of different partitioning softwares (I decided to try out as many as I could), and had a corrupted partition table by the end of it. (I think it might be something like going to a party and mixing your drinks. It makes you ill, whereas if you just stick with one drink you might not be so bad.) Maybe the discrepancies added up rather than cancelling each other out or something. In the end I deleted all the partitions and reformated from scratch with the Ubuntu installer's partition and that cured the problem. Now I stick with the 'Parted based partitioners. The Ubuntu installer's partitioner and QTParted and GParted are all 'Parted based partitioners, so will all be compatible with each other. Other linux compatible partitioners should be okay too.
It seems like a few of us around here has a favorite partitioning software and feel loyal to it much like sports fans encouraging their favorite team.
One thing most of us at this forum have in common is we all use Ubuntu, and it's the Ubuntu installer that needs to be able to recognise the partitions in the end. 
Another thing most of us have in common is our disks were often formatted by various other partitioning softwares originally and Ubuntu is installed after another operating system (and who knows what other partitioning software). Wisely, the Ubuntu installer is designed to be very safe, and simply won't offer you the dodgy hard-disk so you can't get in trouble. That's what I think happened in this instance. 

Nowadays with such nice large hard disks around people are collecting larger amounts of data. They have no-where convenient to back it up and store it. Even though partitioning is reasonably safe, they are still taking a risk. If someone has a large amount of data it is even more important to back it up than a small amount of data. 
I think that the only convenient way to back up such a large amount of data would be to use another similarly sized hard disk. Lots of people don't want to spend the money on another similar sized hard disk. It isn't Ubuntu's fault if they neglect to back up their data and lose everything. Data that cannot be backed up might not be worth collecting in the first place. Lots of other things can happen too, hard disks can fail by themselves etc. Everyone is well warned to back up their data. It's only human not to bother. I'm human too. Mostly I get away with it. Sometimes I learn lessons.

GParted livecd-0.2 is very good, I use it all the time. It probably would fix your problem and make your partition agreeable to the Ubuntu installer, but you might have to delete the partition and re-create it for that, I think. (That would destroy all your data, but you would have a Ubuntu and Windows compatible partition after that, after replacing all your data again.)
:-D There, that's what I think. Sorry for being so verbose. (Herman)

---

