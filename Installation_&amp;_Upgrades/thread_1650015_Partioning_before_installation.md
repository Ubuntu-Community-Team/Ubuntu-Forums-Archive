---
title: "Partioning before installation?"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by BKbroila on 2010-12-20
Even though I've read several tutorials and documents, they're kind of vague as to whether or not I should partition my HDD before installing Ubuntu side-by-side with Win7.
So when I'm in Win7, should I make a partition for Ubuntu? Or should I create the partition while I'm in the process of installing Ubuntu? If I should partition my HDD before installing, it should be formatted NFTS, correct? 
This is REALLY bugging me, as I've already tried formatting the HDD while in the installation process, but really messed up badly, which ended up in a complete wipe of my HDD....

And I also plan on having 80GB for Ubuntu. So how much should I allocate for '/' '/home' and swap? I know that I should try to have as much as possible for /home, but with swap and / what would be good sizes?

Thanks

---

### Post by Quackers on 2010-12-21
First thing to check in Win 7 is that you don't have more than 3 primary partitions and one extended partition. 4 primary partitions is the limit (and an extended partition counts as a fourth).
I would say that all you need out of the Win 7 installation is some free space to install Ubuntu into. This would be created usually by resizing the C: partition (though other means can be available).
I would create the new partitions whilst in the Ubuntu installer - for a number of reasons. 
The first is that if the partitions are previously created you may be tempted to use the "install alongside" option in the installer. With the 10.10 installer this is a very bad idea. It is fraught with danger!
Secondly partitioning for Windows should be done with Windows. Partitioning for Linux should be done with Linux-based programmes.

Partitions for Ubuntu are nowadays normally in the ext4 format - NOT NTFS

My root (/) partition is approx 12GB and it is barely half full.
Use the rest of the space for /home (if required) and swap space.

---

### Post by BKbroila on 2010-12-21
> **Quackers said:**
> First thing to check in Win 7 is that you don't have more than 3 primary partitions and one extended partition. 4 primary partitions is the limit (and an extended partition counts as a fourth).
I would say that all you need out of the Win 7 installation is some free space to install Ubuntu into. This would be created usually by resizing the C: partition (though other means can be available).
I would create the new partitions whilst in the Ubuntu installer - for a number of reasons. 
The first is that if the partitions are previously created you may be tempted to use the "install alongside" option in the installer. With the 10.10 installer this is a very bad idea. It is fraught with danger!
Secondly partitioning for Windows should be done with Windows. Partitioning for Linux should be done with Linux-based programmes.

Partitions for Ubuntu are nowadays normally in the ext4 format - NOT NTFS

My root (/) partition is approx 12GB and it is barely half full.
Use the rest of the space for /home (if required) and swap space.

Uhh I just looked at Disk Management, and I apparently have 4 Primary partitions already..... What's considered a Primary partition????

And I have no idea what that 3rd partition is. It looks like 3GB of useless space. I did try installing Ubuntu, but in the process of re-installing Win7, I completely wiped my HDD clean

---

### Post by Quackers on 2010-12-21
The 4 primary partition limit refers to any one hard drive. The most you have on any one disc is 3. You could currently install Ubuntu into the unallocated space at the end of your first drive.
The "third" one you refer to appears to be a dvd.

---

### Post by oldfred on 2010-12-21
You show an expansion drive 1 of 465GB with one NTFS partition. I would think about shrinking that partition and installing Ubuntu on that drive. It avoids the issues of all 4 partition used on your drive 0.

Just to expand on quackers recommendations.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With two drives you have to use manual partitioning so you get the choice to install grub (Ubuntu's boot loader) into the sdb drive (drive 1 in windows). That way you can leave windows boot loader in sda and go back to booting it if need be. After your install set the sdb drive 465GB as first boot in BIOS.

Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by BKbroila on 2010-12-21
Sorry my bad. I had an external HDD and a CD connected. So it looks like the attached pic.
So with that setup, I have 80 GB unallocated. Should I partition that into something, and install Ubuntu onto it? Or should I do NOTHING and just go right into installation?

And I do plan on using Hibernate. But I feel like your last recommendations are optional (???)

---

### Post by Quackers on 2010-12-21
Acording to the screenshot you have 58.01GB free - not 80GB
If you plan on using hibernation your  swap space should be very slightly larger than the amount of ram you have. For example 2GB of ram would be ok with 2.1GB of swap space.
Whether you partition now is up to you. I personally use the Ubuntu installer and select "specify manually" to do it, but as oldfred says the installation may be quicker if you partition first. However, I don't know if Windows can partition in ext3 or ext4 - I think not.

---

### Post by JBAlaska on 2010-12-21
Yup use the manual partition option in Ubuntu install, first create a extended partition for the whole 58GB, then make a / (root) ext4 partition, a swap partition, and a ext4 /home partition.

Note: if you need to access your Linux partitions in windows, you will need to use ext3 filesystems.

---

### Post by oldfred on 2010-12-21
Do not use windows to create extra partitions. It will convert to SFS which is a proprietary windows only LVM logical volume manager. It is a one way conversion, windows says you cannot convert back (without erasing drive and reinstalling).

You cannot create Linux partitions in windows. Use windows tools for windows and use Linux tools for Linux except sometimes you use Linux tools to fix windows.:)

---

### Post by BKbroila on 2010-12-21
I feel like the biggest moron right now..
Where do I get the option to create an extended partition? I've selected to manually create a partition. And after that, there's a table of the partitions and unallocated space. When I click on the unallocated space, I have options for about of space and the type. I looked for extended, but it wasn't there.... Am I suppposed to individually create the swap, root, and /home partitions??? This is causing quite a dilemma for me...

---

### Post by Quackers on 2010-12-21
Logical type should do it

---

### Post by Quackers on 2010-12-21
Sorry, what program are you in please?

---

### Post by BKbroila on 2010-12-21
Program???
I'm trying to install Ubuntu 10.10...
I thought it really didn't matter if it was logical or primary
So yeah, how do I get to the extended option?

---

### Post by BKbroila on 2010-12-21
Better yet, I'm in Ubuntu live right now. So should I use GParted??? I feel like that would be much easier...

---

### Post by Quackers on 2010-12-21
You don't want another primary if you've already got 3!
I've forgotten - what options are there for partition type? Primary or logical?

---

### Post by BKbroila on 2010-12-21
yep, just primary or logical.

---

### Post by Quackers on 2010-12-21
If you want to create the partitions in gparted here is a guide. It's an oldish one but should get you through ok.
[http://www.dedoimedo.com/computers/gparted.html#mozTocId466365](http://www.dedoimedo.com/computers/gparted.html#mozTocId466365)

However, if you create them now you will need to select the mount points in the installer later.

---

### Post by theasprint on 2010-12-21
Hi,

In fact one of the users (amjjawad) has made a tutorial which I think is very simple and easy-to-understand.

Here is the link: [http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

---

### Post by BKbroila on 2010-12-21
FINALLY.
Ugh. Last question (hopefully): should root be bigger than home? In all the pics I see, root is larger...

---

### Post by Quackers on 2010-12-21
None of my root partitions are bigger than 12GB and none of those are more than half full.

---

### Post by theasprint on 2010-12-21
Hi,

Yes, I am sure that root should be the largest.

This is because root is the partition where all your stuff is being kept.

Just like Windows C drive something like that.

Home and swap partition are for the system.

*Ohya, you can spread the tutorial to as many people as possible.

Enjoy Ubuntu :D

---

### Post by BKbroila on 2010-12-21
> **theasprint said:**
> Hi,

Yes, I am sure that root should be the largest.

This is because root is the partition where all your stuff is being kept.

Just like Windows C drive something like that.

Home and swap partition are for the system.

*Ohya, you can spread the tutorial to as many people as possible.

Enjoy Ubuntu :D


Oh shiznitt....... I'm really enjoying this, but made /home about 3 times as big as root... 
Well thanks for everyone's help! It was a long night for me...

---

### Post by Elfy on 2010-12-21
> **BKbroila said:**
> Oh shiznitt....... I'm really enjoying this, but made /home about 3 times as big as root... 
Well thanks for everyone's help! It was a long night for me...

That's fine :)

I'm just going to toss another pig in the ring though - I do not use a seperate /home - but I don't use my /home to store my data - that all goes to seperate data partitions - symlinked to /home.

---

### Post by Elfy on 2010-12-21
> **theasprint said:**
> Hi,

Yes, I am sure that root should be the largest.

This is because root is the partition where all your stuff is being kept.

Just like Windows C drive something like that.

Home and swap partition are for the system.

*Ohya, you can spread the tutorial to as many people as possible.

Enjoy Ubuntu :D

No.

Root is the whole thing - /home is inside of / 

Home is where your data goes - sort of like Docs and whatever it is in windows.

Either have no seperate /home in which case it should be the larger or make it (home) larger.

---

### Post by BKbroila on 2010-12-21
Yeah I'm doing that as well so I'm not too worried. Time to learn a whole new OS of computer nerdy terms!!!!!!!!!!!!!!!!!!!!!!!! 
Hoorah

---

### Post by Quackers on 2010-12-21
Enjoy yourself :-)
If you are happy please mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

### Post by theasprint on 2010-12-22
Hi,

Ok I'm really sorry about this:

>  Root is the whole thing - /home is inside of / 

A lesson learnt. REALLY SORRY!!

---

### Post by theasprint on 2010-12-22
Hi,

Sorry, just for learning: 

How is /home inside the root (/ ) partition?
Because in the tutorial, and the bootinfoscript i see, Ubuntu has 3 partitions.
One is the swap, then root and home partitions. So it seems like they are different.

So how should users allocate the space in a HDD? (Proportion of root, home and swap partitions)

---

### Post by Elfy on 2010-12-22
> **theasprint said:**
> Hi,

Ok I'm really sorry about this:



A lesson learnt. REALLY SORRY!!

> **theasprint said:**
> Hi,

Sorry, just for learning: 

How is /home inside the root (/ ) partition?
Because in the tutorial, and the bootinfoscript i see, Ubuntu has 3 partitions.
One is the swap, then root and home partitions. So it seems like they are different.

So how should users allocate the space in a HDD? (Proportion of root, home and swap partitions)

It's about partitions as you say.

You have / which contains all the other locations such as /home /bin etc..

Open a terminal 

cd /
ls 

They are all under / - you COULD have them all on seperate partitions if you so wished.

or not ...

My /home is not - used to be but I don't find it useful anylonger to split it.

You said 
> 
This is because root is the partition where all your stuff is being kept.
> 
Home and swap partition are for the system.

A bit mixed up there - home is where a users files are kept - if you had 10 users their files would be under their username in /home

/ is where everything is - but that doesn't mean that it is all on the same partition.

> 
Yes, I am sure that root should be the largest.Using this to work with we could have a 1Tb / and a 10Gb /home which would be the wrong way round :)
> 
A lesson learnt. REALLY SORRY!! 
Sorry, just for learning: No need to apologise and aren't we all learning as we go through life :)

---

### Post by Quackers on 2010-12-22
In a normal installation home is just a folder inside the root system. It only becomes a separate partition if you create a separate /home partition and give it a mount point of /home

---

### Post by theasprint on 2010-12-22
Hi,

For further clarification.

People separated their /home partition because of?

Also if /home is seperated, then root will be for the programs, and /home will be for the user settings and documents and music, photos etc correct?

So how much space should be given for the root folder if /home is seperated?
I mean how much space should the installation files for programs take?

---

### Post by Elfy on 2010-12-22
[> Also if /home is seperated, then root will be for the programs, and /home will be for the user settings and documents and music, photos etc correct?Yes

> People separated their /home partition because of?Some people do this so that if they do a clean install they can use manual partitioning and then reuse /home but NOT format it - so all their personal data will be there in the new install.


> So how much space should be given for the root folder if /home is seperated?When I used to do this I generally gave / 10Gb - it was never full. Now I have for some reason an 18Gb / with home - I've used less than 6Gb - all my data is in seperate partitions and drives. I would expect that I could trim this to 10Gb and it be enough for me. 

However if you work with DVD's and they get chucked in /tmp that could quickly get used ...

---

### Post by Phanes on 2010-12-22
I dual boot with windows 7 and set my partitions this way...from the install disk i went to advanced. click on the blank/free space and add a new partition. i set 500mb as /boot 20gb as just / then 5gb as swap. the remainder i used as /home.... hope this helps

---

### Post by oldfred on 2010-12-22
I do not recommend a separate /boot unless you have an older system with the BIOS limit of boot having to be inside the first 137GB. Those with servers, LVM or RAID may also want a separate /boot.  But normal desktops do not need it.

When I first started using Ubuntu I just had root, swap and a shared NTFS partition for data with XP. I still have my shared  but use XP very little.

I now have the separate /Data for all my files, but now keep /home inside the / (root) partition also. It now just has my user settings and is less than 1GB so it is easy to backup. My entire root is about 6GB use in a 20GB partition since all my data is in other partitions. But I just found my usage had ballooned as I forgot to mount my backup partition before running the backup and the backup defaulted to root. Time to move some things around.:)

---

