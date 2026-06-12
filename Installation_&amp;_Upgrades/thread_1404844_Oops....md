---
title: "Oops..."
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Coda_ on 2010-02-11
...I upgraded to 9.10 a month or so ago, and I hadnt been happy with it, so I decided to reinstall 9.04 from my disc...when I did this though, It simply installed in addition to 9.10...so I downloaded Partition Master, to go in and delete the partitions....I deleted one, it was renamed unallocated...then I deleted the other two, inserted the Ubuntu disc, and rebooted, only to get the following message?...

> GRUB Loading stage 1.5





GRUB loading, please wait...
Error 22

...so I just want to know how royally f!@#ed this computer is now?...I cant even get to XP...how can I repair this?...

...all help is appreciated...

---

### Post by Satoru-san on 2010-02-11
ooo... I am sorry to hear that you decided to delete your partitions. That was the wrong choice. However there is still hope that you may not have deleted something important.

What you need to do is boot the livecd. I know you said that it came up to grub, that just means that your boot order selects the harddrive over the cdrom

hit f10 or f12 when you see the POST screen. It will bring up a menu to choose live cd.

select the option to use and not make changes to hard disk

then when it boots you are going to go into your programs menu it is the one on the top on the left and open a terminal.

once you have done that, you need to do this

```
sudo fdisk -l
```it will output something like this, you need to paste that here

```
localhost Satoru # fdisk -l

&#12487;&#12451;&#12473;&#12463; /dev/sda: 40.0 GB, 40007761920 &#12496;&#12452;&#12488;
&#12504;&#12483;&#12489; 255, &#12475;&#12463;&#12479; 63, &#12471;&#12522;&#12531;&#12480; 4864
Units = &#12471;&#12522;&#12531;&#12480;&#25968; of 16065 * 512 = 8225280 &#12496;&#12452;&#12488;
&#12487;&#12451;&#12473;&#12463;&#35672;&#21029;&#23376;: 0x0003c014

&#12487;&#12496;&#12452;&#12473; &#12502;&#12540;&#12488;     &#22987;&#28857;        &#32066;&#28857;    &#12502;&#12525;&#12483;&#12463;   Id  &#12471;&#12473;&#12486;&#12512;
/dev/sda1   *           1           4       32098+  83  Linux
/dev/sda2               5          97      747022+  82  Linux &#12473;&#12527;&#12483;&#12503; / Solaris
/dev/sda3              98        4864    38290927+  83  Linux

```Then that will let us know if you still have a windows partition and also if you can still save your linux and we can also find out how to fix it.

ONCE YOU HAVE DONE THIS DONT SHUT DOWN YOUR COMPUTER.

EDIT2: you can connect to the interent from the live cd, and this will help us help you repair your computer.

---

### Post by Coda_ on 2010-02-11
> **Satoru-san said:**
> ooo... I am sorry to hear that you decided to delete your partitions. That was the wrong choice. However there is still hope that you may not have deleted something important.

What you need to do is boot the livecd. I know you said that it came up to grub, that just means that your boot order selects the harddrive over the cdrom

hit f10 or f12 when you see the POST screen. It will bring up a menu to choose live cd.

select the option to use and not make changes to hard disk

then when it boots you are going to go into your programs menu it is the one on the top on the left and open a terminal.

once you have done that, you need to do this

```
sudo fdisk -l
```it will output something like this, you need to paste that here

```
localhost Satoru # fdisk -l

&#12487;&#12451;&#12473;&#12463; /dev/sda: 40.0 GB, 40007761920 &#12496;&#12452;&#12488;
&#12504;&#12483;&#12489; 255, &#12475;&#12463;&#12479; 63, &#12471;&#12522;&#12531;&#12480; 4864
Units = &#12471;&#12522;&#12531;&#12480;&#25968; of 16065 * 512 = 8225280 &#12496;&#12452;&#12488;
&#12487;&#12451;&#12473;&#12463;&#35672;&#21029;&#23376;: 0x0003c014

&#12487;&#12496;&#12452;&#12473; &#12502;&#12540;&#12488;     &#22987;&#28857;        &#32066;&#28857;    &#12502;&#12525;&#12483;&#12463;   Id  &#12471;&#12473;&#12486;&#12512;
/dev/sda1   *           1           4       32098+  83  Linux
/dev/sda2               5          97      747022+  82  Linux &#12473;&#12527;&#12483;&#12503; / Solaris
/dev/sda3              98        4864    38290927+  83  Linux

```Then that will let us know if you still have a windows partition and also if you can still save your linux and we can also find out how to fix it.

ONCE YOU HAVE DONE THIS DONT SHUT DOWN YOUR COMPUTER.

EDIT2: you can connect to the interent from the live cd, and this will help us help you repair your computer.



alright, I did that and got this...

> 
Usage: fdisk [-bssz] [-u] DISK                           Change Partition Table
           fdisk -1[-bssz] [-v] DISK                        List Partition table(s)
           fdisk -s PARTITION                                Give partition size in blocks
           fdisk -v                                                 give fdisk version

Here disk is something like /dev/hbd or /dev/sda
and partition is something like /dev/hda7
-u: give start and end in sector (instead of cylinder units)
-b 2048: (for certain MO disks) use 2048 by the sectors

---

### Post by Satoru-san on 2010-02-11
> **Coda_ said:**
> alright, I did that and got this...
:)
[s]That happens to be a lowercase L not a 1 as in one.

try it again, you may have to put sudo infront of it if it gives you a permission error.[/s]

```
sudo fdisk -l
```[s]l as in laugh[/s]

looks like for some reason your fdisk doesnt have the L option..

try this instead 

```
cfdisk
```and tell me what shows up on the screen.

---

### Post by Coda_ on 2010-02-11
> **Satoru-san said:**
> :)
That happens to be a lowercase L not a 1 as in one.

try it again, you may have to put sudo infront of it if it gives you a permission error.

```
sudo fdisk -l
```l as in laugh


...oops....today really hasnt been my day...

---

### Post by Coda_ on 2010-02-11
...alright...

> 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
units= cylinders of 16065 * 512= 8225280 bytes
Disk identifier:0xald5ald5

Device Boot            Start             End         Blocks           Id        System
/dev/sda1   *             1              11809      94855761         7           HPFS/NTFS 

---

### Post by Satoru-san on 2010-02-11
> **Coda_ said:**
> ...alright...
Good! That is Excellent! 

The only problem that you cant boot your XP is the fact that it doesnt have a bootloader.

You can install linux now in the unpartitoned space.

You have done it before, so do the same thing again, once you get it installed, post here and we will help you upgrade to the latest and gratest version correctly.:p

---

### Post by Coda_ on 2010-02-11
> **Satoru-san said:**
> Good! That is Excellent! 

The only problem that you cant boot your XP is the fact that it doesnt have a bootloader.

You can install linux now in the unpartitoned space.

You have done it before, so do the same thing again, once you get it installed, post here and we will help you upgrade to the latest and gratest version correctly.:p


...so I cant get to XP anymore?...

---

### Post by Satoru-san on 2010-02-11
> **Coda_ said:**
> ...so I cant get to XP anymore?...
XP is still there :) you just need to install ubuntu again to get grub which will then allow you to boot XP :)

---

### Post by Coda_ on 2010-02-12
> **Satoru-san said:**
> XP is still there :) you just need to install ubuntu again to get grub which will then allow you to boot XP :)

...yea, I got it...thanks a lot for all your help...


...Ive another question though, when I did this earlier, I tried running all the updates, and it told me there wasnt enough memory, thats why I deleted the partitions...will I have the room now?, or did this just take me back to where I was before?...

...also, before, at start up, I had two options (ubuntu or XP), and there was a countdown clock that would count down and automatically start xp....now there is a different list, with 3 ubuntu options (ubuntu 9.04 Kernal 2.6.28 -11 generic, Ubuntu 9.04 Kernel 2.6.28 generic (recovery mode), and ubuntu 9.04, memtest86t)...its there a way to make it like it used to be?

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...yea, I got it...thanks a lot for all your help...


...Ive another question though, when I did this earlier, I tried running all the updates, and it told me there wasnt enough memory, thats why I deleted the partitions...will I have the room now?, or did this just take me back to where I was before?...
There is a big differnece between memory and disk space, though I think you mean diskspace

You have a 100 gb drive, which is PLEANTY for ubuntu, however I have to do some math real fast to see how much you saved for ubuntu, but deleting your partitions did not make your harddrive any bigger, so you will have the same space problem, unfortunatly..

---

### Post by lindsay7 on 2010-02-12
You may still have windows on the drive.  I would so a couple of things before you install Ubuntu. It looks like, at least from what I see, that if there is unallocated space left on the drive it is very small and Ubuntu will not like being on that small space.  I would load the install cd and run Gparted. you can find it under Systems/application,  Take a screen shot of this if you can and post it or at least tell us what it shows.  If I am correct, you may need to repartition the windows drive to give you the space that you need.  The other thing to do is to install the windows mbr now to get you going with windows so you have a system.  Do you have the windows xp intall disk handy?

---

### Post by Satoru-san on 2010-02-12
now see that doesnt make any sense.. your partiton is 
46316.289550781 megs which means your freespace is only 4.5 gigs O_o

If anyone else is reading this, can you help me out here o_O

---

### Post by lindsay7 on 2010-02-12
> **Satoru-san said:**
> now see that doesnt make any sense.. your partiton is 
46316.289550781 megs which means your windows partition is only 4.5 gigs O_o

If anyone else is reading this, can you help me out here o_O


How are you getting that the windows partiton is 4.5 gigs?

Any way, if he will give us the info from gparted we will know.


TO CODA,

Did you reinstall Ubuntu??

---

### Post by Satoru-san on 2010-02-12
@[lindsay7]("http://ubuntuforums.org/member.php?u=762393") I told him to, well kind of, I hope he checks in here, before he does.

---

### Post by ironclaw on 2010-02-12
I calculated that the Windows partition size is 90.5 GB from the fdisk output...
11809 * 8225280 / 1024^3

According to this, there is only 2.7 GB of unallocated disk space. Did I make a mistake?

---

### Post by Coda_ on 2010-02-12
...Ive looked, but I cant find Gparted...System-Administration right?...


...I installed Ubuntu, but Im getting a message trying to use the update manager that says there isnt enough free space...

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...Ive looked, but I cant find Gparted...System-Administration right?...


...I installed Ubuntu, but Im getting a message trying to use the update manager that says there isnt enough free space...
>_< so that means that you cant even install gparted to see how much space you really have.

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...Ive looked, but I cant find Gparted...System-Administration right?...


...I installed Ubuntu, but Im getting a message trying to use the update manager that says there isnt enough free space...

I think you should boot into a live CD, and shrink the Windows NTFS partition (i.e., /dev/sda1) with gparted. Then reinstall Ubuntu into a larger free space.

---

### Post by Coda_ on 2010-02-12
...I downloaded something called "Partition Master" on XP, with that suffice?...

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...I downloaded something called "Partition Master" on XP, with that suffice?...
gparted is MUCH more powerful, and we know that it works and that you will not have a problem with that windows program breaking things.

Resizing partitions is delicate, you have to be careful or you lose everything, I have lost everything in the past when I was trying to "grow" a partition.

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> I think you should boot into a live CD, and shrink the Windows NTFS partition (i.e., /dev/sda1) with gparted. Then reinstall Ubuntu into a larger free space.


...I think I can do this, how difficult is it?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...I downloaded something called "Partition Master" on XP, with that suffice?...

NTFS does not support online resizing, so you can't shrink the file system while you are in Windows. So I think the best option would be to shrink the file system with a live CD. I'm a bit curious about how you got Ubuntu 9.04 running before, though - there doesn't seem to be enough free space. Did you resize the NTFS partition recently?

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> NTFS does not support online resizing, so you can't shrink the file system while you are in Windows. So I think the best option would be to shrink the file system with a live CD. I'm a bit curious about how you got Ubuntu 9.04 running before, though - there doesn't seem to be enough free space. Did you resize the NTFS partition recently?

...not that I'm aware of...

...alright, so I'll boot from the live cd, how much should I downsize?...

---

### Post by lindsay7 on 2010-02-12
Ironclaw, that is what I was coming up with, less than 4 gigs.

If you use the Ubuntu install cd you will find Gparted there, it will not be on the installed Ubuntu, it needs to be downloaded from synapic and you do not have much space.  Load the install cd and look for it under system/administration.  You can also download the gparted program form their web site and burn it to a cd. I think you burn it as an ISO file so that it will start up your computer and you can use it from there. It is much easier to just use the ubuntu install live cd. You can use it to repartition your drive.  You need about 15 gigs to be safe and have room for data and programs.

---

### Post by lindsay7 on 2010-02-12
Great, I just saw the other posts, I think we are all on the right track.

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...I think I can do this, how difficult is it?...

The [Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition") has a good guide. Look [here]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition") in particular for file system resizing.

With gparted, it's a completely graphical and automated process.

---

### Post by Coda_ on 2010-02-12
...I booted from the disc, but still dont see "Gparted"...I do see something called Partition Editor...is that close enough?...


...edit* nevermind...Partition Editor is Gparted right?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...I booted from the disc, but still dont see "Gparted"...I do see something called Partition Editor...is that close enough?...


...edit* nevermind...Partition Editor is Gparted right?...
Yes, that is gparted. I think it was renamed to gparted in the menu for Ubuntu 9.10.

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> Yes, that is gparted. I think it was renamed to gparted in the menu for Ubuntu 9.10.


...alright, I have it open, what do I do?...

---

### Post by lindsay7 on 2010-02-12
Good, click on the drive and use the slider to resize, look at the menu bar when this is done and it should give you an install button on a check mark.. I do not remember exactly.  You can them make a new partition by deleting the old small partition and using the unallocated space or grow the old small partition into the space you created from the windows or larger partition.

---

### Post by Coda_ on 2010-02-12
> **lindsay7 said:**
> Good, click on the drive and use the slider to resize, look at the menu bar when this is done and it should give you an install button on a check mark.. I do not remember exactly.  You can them make a new partition by deleting the old small partition and using the unallocated space or grow the old small partition into the space you created from the windows or larger partition.

...alright, I read in the guide that you cant add space unless you take it away from the place next to it...if ubuntu is far left, and xp far right, and theres something in the middle, how to I go about making the ubuntu part larger?...

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...alright, I read in the guide that you cant add space unless you take it away from the place next to it...if ubuntu is far left, and xp far right, and theres something in the middle, how to I go about making the ubuntu part larger?...
That isnt good that ubuntu is on the left, it will be harder to resize ntfs.

How big does it say ubuntu is?

---

### Post by Coda_ on 2010-02-12
> **Satoru-san said:**
> That isnt good that ubuntu is on the left, it will be harder to resize ntfs.

How big does it say ubuntu is?

...Im sorry, I had it backwards, Ubuntu is on the far right, NTFS is on the far left...


[IMG]http://tinypic.com/r/11rd3qq/6[/IMG]


[IMG]http://tinypic.com/r/11rd3qq/6[/IMG]

---

### Post by lindsay7 on 2010-02-12
The first thing to do is shrink the Windows partition. Just leave the the space that is created as unallocated.  You can see if the partition in the middle can be moved over or you can grow it into the unallocated space.  That will make it larger. From there you can now shrik that partition and leave the unallocated space on its left hand side. Then you can grow the partition you need for ubuntu.   What is the middle partition anyway.  You could delete that if it is not needed and use its space.

---

### Post by lindsay7 on 2010-02-12
Well that makes things easier.  You use the same logic anyway. You will just have fewer steps.

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...Im sorry, I had it backwards, Ubuntu is on the far right, NTFS is on the far left...
That is good to hear, how big is the NTFS partition and how big is ubuntu?

Basically just drag the ntfs one smaller and the make it so there is **20 gigs of unused space**, if there is still any linux partiitons delete them, it is easier to reinstall, and a better idea.

---

### Post by Satoru-san on 2010-02-12
> **lindsay7 said:**
>   What is the middle partition anyway.  You could delete that if it is not needed and use its space.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

THAT IS PROBABLY THE SWAP!!! **dont delete that**

---

### Post by Coda_ on 2010-02-12
...I think there are only 2 things on it, the second has 2 sub items (/dev/sda 5, and /dev/sda6)...


...ntfs is 90.66gb with 15.78 gb used, and 74.88gb free, and ubuntu (i think) is 2.33gb with 2.11gb used, 227.84 mb free, and the swap is 172.54mb

---

### Post by lindsay7 on 2010-02-12
Look at this for reference.  And that is correct, that partition could be the swap partiton. you will want to keep that.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by lindsay7 on 2010-02-12
By the way, when you get done with this. If you still can not boot into Windows, you will just need to reinstall the windows mbr. Do you have the windows install disk handy.  If not we will need to work around that too.


Here is the info to do that.  You will need to download a program called Super Grub and burn it to a disk.

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by Coda_ on 2010-02-12
...so I am resizing the ntfs one...I lessend it by 21167mib (which is about 20 gigs right?)...does that sound right?...

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...so I am resizing the ntfs one...I lessend it by 21167mib (which is about 20 gigs right?)...does that sound right?...
Perfect :)

---

### Post by Coda_ on 2010-02-12
...alright, now there is a section of unallocated...I should click the /dev/sda2...and extend it the 20 gigs right?...

---

### Post by northrup on 2010-02-12
Yeah, that's about right.

And yes, if there's no swap partition to begin with, use the unallocated space to create one.  Otherwise, the computer will likely run out of memory, which will cause lockups.

---

### Post by northrup on 2010-02-12
You mean unallocated?  Yes.

---

### Post by Coda_ on 2010-02-12
> **northrup said:**
> You mean unallocated?  Yes.

...yea...


...how do I add the free space to the ubuntu partition?...do I have to apply first?...

---

### Post by northrup on 2010-02-12
You should be able to just drag the edge of the Ubuntu partition to fill up the free space.  Remember to save some for a swap partition.  I'd save about 1 or 2 GB (1024 to 2048 MB).

Only click on "Apply" when you're all done adjusting the sizes and you're ready to actually make GParted work it's magic on your hard disk.

---

### Post by Satoru-san on 2010-02-12
> **Coda_ said:**
> ...do I have to apply first?...
dont apply untill you are all done, or it will take 2x as long. do that at the very end once you have it perfect.

---

### Post by Coda_ on 2010-02-12
> **northrup said:**
> You should be able to just drag the edge of the Ubuntu partition to fill up the free space.  Remember to save some for a swap partition.  I'd save about 1 or 2 GB (1024 to 2048 MB).

Only click on "Apply" when you're all done adjusting the sizes and you're ready to actually make GParted work it's magic on your hard disk.

...when I click the ubuntu partiton (which includes the swap and the ubuntu stuff), the resize/move button isnt clickable...



...edit- what do I do with the unallocated space?...

---

### Post by Satoru-san on 2010-02-12
Yea, I dont think you can grow ext3. He Might have to reinstall.

---

### Post by northrup on 2010-02-12
Swap should be a seperate partition.  The one you're trying to move is the one that's an "extx" ("x" being either 3 or 4).  If there's already another one labeled "swap", then great.

As for the issue with resizing, try moving everything as far to the left as possible, then filling the space on the right with the rest of your Linux partition.

---

### Post by Coda_ on 2010-02-12
> **Satoru-san said:**
> Yea, I dont think you can grow ext3. He Might have to reinstall.

...how would I go about doing that?...

---

### Post by northrup on 2010-02-12
@Satoru: You're right.  @Coda:

Delete the ext3 partition.
Move everything else to the far left.
Create a swap partition if there isn't one already.
Create a new ext3 partition that fills all the remaining unallocated space.

And remember to back up any files you hold dear that were on your Ubuntu partition BEFORE clicking on "Apply".

---

### Post by Coda_ on 2010-02-12
> **northrup said:**
> @Satoru: You're right.  @Coda:

Delete the ext3 partition.
Move everything else to the far left.
Create a swap partition if there isn't one already.
Create a new ext3 partition that fills all the remaining unallocated space.

And remember to back up any files you hold dear that were on your Ubuntu partition BEFORE clicking on "Apply".


...alright, I tried that and it told me that it was "unable to delete /dev/sda5; please unmount any logical partitions having a number higher than 5"...what does that mean?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...I think there are only 2 things on it, the second has 2 sub items (/dev/sda 5, and /dev/sda6)...


...ntfs is 90.66gb with 15.78 gb used, and 74.88gb free, and ubuntu (i think) is 2.33gb with 2.11gb used, 227.84 mb free, and the swap is 172.54mb

I'm quite sure that there is an extended partition containing sda5 and sda6. The NTFS partition should be a primary partition.

So, first, unmount the swap partition by right clicking it and selecting unmount. Second, grow (expand) the extended partition. That is, the partition that contains sda5 and sda6. Third, grow the ext3 partition (containing Ubuntu). You might also want to grow the swap partition if it's only 170 MB in size.

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...alright, I tried that and it told me that it was "unable to delete /dev/sda5; please unmount any logical partitions having a number higher than 5"...what does that mean?...
It means that a logical partition in the extended partition is mounted. Right click on each partition and select unmount.

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> I'm quite sure that there is an extended partition containing sda5 and sda6. The NTFS partition should be a primary partition.

So, first, unmount the swap partition by right clicking it and selecting unmount. Second, grow (expand) the extended partition. That is, the partition that contains sda5 and sda6. Third, grow the ext3 partition (containing Ubuntu). You might also want to grow the swap partition if it's only 170 MB in size.


...I right clicked the swap, and hit something called "swapon"...then some stuff happened, then I was able to expand the /dev/sda2 into the free space...does all this sound right?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...I right clicked the swap, and hit something called "swapon"...then some stuff happened, then I was able to expand the /dev/sda2 into the free space...does all this sound right?...
That's strange... swapon actually **mounts** the swap partition. You should hit swapoff...

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> That's strange... swapon actually **mounts** the swap partition. You should hit swapoff...

...your right, it says swapon now...so I guess everything is good now?...should I go ahead and apply?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...your right, it says swapon now...so I guess everything is good now?...should I go ahead and apply?...
Just make sure you didn't delete anything important. If everything looks right (i.e., there should be 3 partitions now: a Windows partition that has been shrunk in size, an ext3 or ext4 partition for Ubuntu that is at least 10 GB in size, and a small swap partition), then you can click apply. Make sure you don't interrupt gparted while it's working, because that will quite likely lead to data loss.

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> Just make sure you didn't delete anything important. If everything looks right (i.e., there should be 3 partitions now: a Windows partition that has been shrunk in size, an ext3 or ext4 partition for Ubuntu that is at least 10 GB in size, and a small swap partition), then you can click apply. Make sure you don't interrupt gparted while it's working, because that will quite likely lead to data loss.

...there are 2 main partitions, xp (/dev/sda1),which is 69.99gb, and ubuntu (/dev/sda2) which includes the unallocated partition, ext3, and the swap, all which equals 23.13gb...

...am I good to go?...

---

### Post by ironclaw on 2010-02-12
> **Coda_ said:**
> ...there are 2 main partitions, xp (/dev/sda1),which is 69.99gb, and ubuntu (/dev/sda2) which includes the unallocated partition, ext3, and the swap, all which equals 23.13gb...

...am I good to go?...
Wait, what is the size of the ext3 partition? You should resize it to fill up all the unallocated space. Everything else looks good.

---

### Post by lindsay7 on 2010-02-12
When you are done your drive should look something like this.


[ATTACH]146840[/ATTACH]

---

### Post by Coda_ on 2010-02-12
> **ironclaw said:**
> Wait, what is the size of the ext3 partition? You should resize it to fill up all the unallocated space. Everything else looks good.

...yea, I forgot that, Its dont now though...im gunna apply...how long should it take?...

---

### Post by Coda_ on 2010-02-12
> **lindsay7 said:**
> When you are done your drive should look something like this.


[ATTACH]146840[/ATTACH]

...yes, except my the extended and the ext3 is switched on mine...

---

### Post by lindsay7 on 2010-02-12
A few minutes,  be patient. Just let it run.

---

### Post by Coda_ on 2010-02-12
...I think I got it...I want to thank everyone that helped out...one of the great things about ubuntu is the community available to help out...

---

### Post by lindsay7 on 2010-02-12
Good job, can you boot into windows now and is Ubuntu booting like you want?

---

### Post by Satoru-san on 2010-02-12
We are happy to help.

Make sure everything works first then hit the thread tools button and choose mark as solved.

Cheers :):popcorn:

---

