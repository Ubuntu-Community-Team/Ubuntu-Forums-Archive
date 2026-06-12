---
title: "Installation without Swap Partition"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by Mel_Blakey on 2015-01-23
I have just installed Ubuntu 14.04 using a USB stick onto a HDD  which already had Windows 7 installed to its own partition + 2 other  partitons, containing Windows Recovery, the other HP Tools(?).

I  wanted to keep Windows (Dont Ask!). So (following the insatll guide),  prior to install I reduced the size of its partition, created a new  partion and formatted it to ext4 using Gparted.

The installer never gave me the  option to install alongside Windows and I went staright for 'Something  Else'. I selected the drive that I wanted Ubuntu to be installed to and  clicked continue.
It then said that I need to give the partition a  mount point. So, I selected / from the dropdown as it seemed to be the  most logical. I clicked continue again and I was warned that I had not  assigned a swap partition.
For the life of me I could not get it to both 'give the partition a mount poin and 'assign a swap partition'.
After several attempts I decide to continue without creating a swap partition.

Now  that it is installed it all seems to work OK. I get the Grub menu,  Windows is working as well as can be expected and Ubuntu is running like  a dream.

So...to my questions:- 

"What are the consequences of not having a swap partion?" "What exactly is its purpose?"

"Should I create one now" and if the answer is yes "How?"

You  will have guessed early on that I am a novice. But, one thing that I  have learnt by reading through this fourum is that you guys like some  system info to work on, so, here goes:-

[COLOR=#000080]HDD Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End       Size      Type      File    Label         Flags  Partion  
 1          1049kB  210MB   209MB   primary  ntfs   SYSTEM   boot    /dev/sda1
 2          210MB   163GB   163GB   primary  ntfs                              /dev/sda2
 4          163GB   295GB   132GB   primary  ext4                             /dev/sda4
 3          295GB   316GB   20.7GB  primary  ntfs    Recovery            /dev/sda3
unalctd                            3.9GB    unalloctaed

Laptop:      HP Compac Presario CQ57 
Memory:     3.7GB
Processor:  Intel® Pentium(R) CPU B960 @ 2.20GHz × 2
Graphics:    Intel® Sandybridge Mobile
Disk:          130.0GB

BIOS not UEFI

Ubuntu 14.04LTS x 64

[/COLOR]
Thanks & Regards

Mel 'B' - Cheshire UK

---

### Post by tokyobadger on 2015-01-23
For desktops with a lot of RAM you could probably get away without (I have for around 10 years), but for laptops where suspend etc are important for users, you should go for the swap

As to how, I'd re-run the USB installer, at the something else option I'd carve out  something like 8 to 12G (laptop Ubuntu veterans please chime in) as a partition, assign it as swap and carry on.

---

### Post by Bucky Ball on 2015-01-23
You might want to check out [this]("https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F") informative page regarding /swap partitions.

Easy enough to create one. If you have Gparted installed (it's in the repos if you don't) use the 3.9Gb unallocated space at the end of the disk to create one. Right click on it and then choose 'New'. You don't need to set a mount point for it. Just make it 'swap space' and the system will do the rest. That's about it. Good luck and just ask if you get stuck. ;)

PS: Just thought of this, sorry. Following the creation of a /swap, you will need to add it to /etc/fstab. We can give you a hand with this if you need one.

PPS: You only really need about 2Gb swap but I generally stick to the rule of making it as large as the installed RAM. The 3.9Gb you have will do nicely.

---

### Post by oldfred on 2015-01-23
You probably have the 4 primary partition limit issue. If you made the / (root) partition logical, then you could have added as many added logical partitions as you want.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Bucky Ball on 2015-01-23
Good point, oldfred, and I should have noticed. If you installed in BIOS mode, as you mention in your first post, then the four partition limit is quite possibly why the system won't let you create a /swap, if that is the issue you're having.

---

### Post by Mel_Blakey on 2015-01-24
[TABLE="width: 500"]
[TR]
[TD][COLOR=#000080]Number
[/COLOR][/TD]
[TD][COLOR=#000080]Size[/COLOR][/TD]
[TD][COLOR=#000080]Type[/COLOR][/TD]
[TD][COLOR=#000080]File System[/COLOR][/TD]
[TD][COLOR=#000080]Label[/COLOR][/TD]
[TD][COLOR=#000080]Flags[/COLOR][/TD]
[TD][COLOR=#000080]Partition[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]1[/COLOR][/TD]
[TD][COLOR=#000080]209MB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]SYSTEM[/COLOR][/TD]
[TD][COLOR=#000080]Boot[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda1[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]2[/COLOR][/TD]
[TD][COLOR=#000080]163GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda2[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]4[/COLOR]
[/TD]
[TD][COLOR=#000080]132GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]EXTN[/COLOR][/TD]
[TD][COLOR=#000080]UBUNTU[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda4[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]3[/COLOR]
[/TD]
[TD][COLOR=#000080]3.20GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]RECOVERY[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda3[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]3.9GB[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]Unallocated[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[/TR]
[/TABLE]


Thank You ALL for your input. After reading your posts and the stuff in the links I think that I now have an understanding of the situation. The way I see it is this:-

HDD's can have 3 types of partition. Primary (max 4), Extended & Logical (I don't know what the difference is, but at this stage I don't need to know).
At the moment I have four drives. All of them are 'Extended'. So to quote my new friend from FCM, I am out of pie.

Am I right in assuming that the solution is to convert No4 into an Extended* drive into which I can create 2 Logical drives - 1 Root (/) for Ubuntu formatted to EXT3 + 1 formatted to Linux Swap?

* Will I need to format the Extended drive? If so, to what?

Thanks and Regards

Mel 'B' - Cheshire UK
_________________
PS
A short history of this drive is: (*No need to read if you don't want to. but.*..)
Last Monday my laptop finally went pop. So I bought another dud (same as, but a couple of years younger) off ebay and I have managed to fix it with a donor part from my old machine.
This is the HDD that came with it and it has Windows7 installed along with MS Office. I converted to Ubuntu 9 months ago and I love it so much that I had no regrets about wipin MS off my old drive. But, there is one programme that I really miss, MS Publisher. So, if I can keep it, that would be great!

---

### Post by Bucky Ball on 2015-01-24
> **Mel_Blakey said:**
> 

Am I right in assuming that the solution is to convert No4 into an Extended* drive into which I can create 2 Logical drives - 1 Root (/) for Ubuntu formatted to EXT3 + 1 formatted to Linux Swap?

No. Number 3 is an extended partition already (you don't have four drives, you have four partitions). Therefore, you would have a logical partition inside that (which would be the Ubuntu / partition as a logical). You can boot from the Live USB and shrink that logical partition by 4Gb using Gparted, then create the /swap partition using that free, unallocated space inside the extended partition (3).

You then have two logical partitions inside the extended partition 3; / and /swap.

Just to clear up another point: you can have four partitions per physical drive. Doesn't matter whether they are primary, extended or a combination of both. The difference with the extended partitions is that you can have as many logical partitions inside one as you like (or as the hardware can handle, theoretically). They don't count. 

Therefore, you could have three primary partitions and an extended partition, as an example, and inside that extended partition you could have ten logical partitions. So, essentially you can have two types of partitions to make up the four, primary or extended, and inside the extended partitions you can have a heap of logical partitions (or logical drives as they are also known). 

So the max is four, but doesn't matter what type of four, primary or extended or a combination of both. Difference is, four primaries is four partitions, and that's it. Extendeds have the advantage of being a 'container' for multiple logical partitions. Extended partitions are NOT, in and of themselves, a partition that can be used to put things ON. They are containers you can put virtual drives IN.

Hope that helps and makes sense. ;)

PS: Look carefully at the screenshot of my Gparted window. I only have the four partition limit, but as you'll note, the use of extended partitions and logical drives expands my options considerably. I have eight of them inside my extended partition.

---

### Post by plucky on 2015-01-24
> 

"Bucky Ball beat me to it."

;)

---

### Post by tokyobadger on 2015-01-24
Edit: also too slow :-)
Edit #2: why ext3 instead of ext4?

---

### Post by Mel_Blakey on 2015-01-24
> **tokyobadger said:**
> why ext3 instead of ext4?
Sorry...my fault! I got the ordering mixed up. In my attempt at tidying  up the list I got 4 & 3 the wrong way round. It is now correct  (edited).

---

### Post by Mark Phelps on 2015-01-24
You can eliminate the first partition by using EasyBCD to "migrate" the Windows boot loader files into the second partition.  

It's relatively easy to do:
1) Download and install EasyBCD
2) Click on the BCD Backup/Repair button
3) Click on the Change boot drive option in the BCD Management Option section
4) Select the "drive" letter containing your OS files.

Once this is done, you can remove the first partition as you will now be booting from the second.

This will then allow you to create another partition.

---

### Post by tokyobadger on 2015-01-24
> **Mel_Blakey said:**
> Sorry...my fault! I got the ordering mixed up. In my attempt at tidying  up the list I got 4 & 3 the wrong way round. It is now correct  (edited).
I meant the filesystem ext4 when you format

---

### Post by Mel_Blakey on 2015-01-24
> **Bucky Ball said:**
> You can boot from the Live USB and shrink that logical partition by 4Gb using Gparted, then create the /swap partition using that free, unallocated space inside the extended partition (3).

You then have two logical partitions inside the extended partition 3; / and /swap.

I've just tried this and once again it has objected in the same way it did when I tried to use the 3.9GB unallocated space.

**''It is not possible to create more than 4 primary partitions**''
 If you want more etc....


It now looks like:-

[TABLE="class: cms_table, width: 500"]
[TR]
[TD][COLOR=#000080]Number
[/COLOR][/TD]
[TD][COLOR=#000080]Size[/COLOR][/TD]
[TD][COLOR=#000080]Type[/COLOR][/TD]
[TD][COLOR=#000080]File System[/COLOR][/TD]
[TD][COLOR=#000080]Label[/COLOR][/TD]
[TD][COLOR=#000080]Flags[/COLOR][/TD]
[TD][COLOR=#000080]Partition[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]1[/COLOR][/TD]
[TD][COLOR=#000080]209MB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]SYSTEM[/COLOR][/TD]
[TD][COLOR=#000080]Boot[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda1[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]2[/COLOR][/TD]
[TD][COLOR=#000080]163GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda2[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]4[/COLOR][/TD]
[TD][COLOR=#000080]132GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]EXTN[/COLOR][/TD]
[TD][COLOR=#000080]UBUNTU[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda4[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD="align: center"][COLOR=#000080]4GB
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]Unallocated
[/COLOR][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][COLOR=#000080]3[/COLOR][/TD]
[TD][COLOR=#000080]3.20GB[/COLOR][/TD]
[TD][COLOR=#000080]primary[/COLOR][/TD]
[TD][COLOR=#000080]NTFS[/COLOR][/TD]
[TD][COLOR=#000080]RECOVERY[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]/dev/sda3[/COLOR][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][COLOR=#000080]3.9GB[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]Unallocated[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[TD][COLOR=#000080]
[/COLOR][/TD]
[/TR]
[/TABLE]

---

### Post by Mel_Blakey on 2015-01-24
Thanks Mark. I'll check EasyBCD out.

---

### Post by oldfred on 2015-01-24
You cannot use the 3.9 as that is not adjacent to the extended and then you cannot move it inside the extended partition. You can only have one extended partition.

It does look like the 4GB unallocated can be used. If it is not inside the extended, expand the extended to include it and then you can create another logical partition.

Please post using fdisk and/or parted from terminal in live installer or your install.
sudo parted -l
sudo fdisk -lu

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mel_Blakey on 2015-01-24
oldfred
Thanks for the links. I'll check them out.

In the meantime, here is the info you requested:

Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   163GB  163GB   primary  ntfs
 4      163GB   291GB  128GB   primary  ext4
 3      295GB   316GB  20.7GB  primary  ntfs

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5524a0d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   318222335   158906368    7  HPFS/NTFS/exFAT
/dev/sda3       576468992   616818687    20174848    7  HPFS/NTFS/exFAT
/dev/sda4       318222336   568080383   124929024   83  Linux

Partition table entries are not in disk order

---

### Post by oldfred on 2015-01-24
Then you do not have an extended partition. 
You will have to delete sda4, the Linux partition and re-install using / & swap as logical partitions. And then both of those will be in one extended partition.

If you have configured system, be sure to backup /home and any data you want to save. And if you installed lots of apps you can export a list of them to make it easier to reinstall.

---

### Post by Bucky Ball on 2015-01-24
Yea, I see from you last post that they are all primary. This: 'EXTN' threw me in your previous table. In the last table, it is clear you have four primary partitions. Changes the game somewhat ...

---

### Post by SeijiSensei on 2015-01-25
First, you only need to create a separate partition for swap if you want to have the machine hibernate.  Otherwise you can just create a swap file on the current filesystem and use that instead.  See this: [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/).

---

### Post by Mel_Blakey on 2015-01-26
Hello All

I decided to have a day off it yesterday as my head was getting fuzzy.

In the end it looked like I had four options:

Delete partition 4 (/dev/sda4) and start anew.
Take Mark's advice and eliminate the first partition.
Use SeijiSensei's idea of creating a Swap File. or
Do Nothing!

As this is the fastest computer that I have owned (with it's 4Gig) and Ubuntu is responding so fast that I have to hold the lappy down, the last option really was favourite.
Anyway just to be on the safe side I eventualy decided on creating a Swap File, as there was never going to be a time when I put the Lappy into Hibernation.
The only diference to SeijiSensei's advice was that I did a bit more research and found and used this offering instead [https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
The reason? *Because it is more recent.*

The Swap File is definately there because it shows up in 'System Monitor'.
The only thing that I am not too sure about is the last section **Tweak your Swap Settings**.
It mentions Swappiness (60) & vfs_cache_pressure (100)

I have left them at their defaults (figures in brackets). But, if anyone has any knowledge of this I would appreciate your input.

Once Again

**THANKS!** and Regards

Mel B - Cheshire UK

---

