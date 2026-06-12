---
title: "partition &amp; install questions"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by souldances on 2007-05-04
hi.  i've resisted micros**t upgrades vehemently, so i've got a windows me system (i can manipulate it a bit so i stuck with it) that i want to keep available at first because there is a network shared printer connected to my computer and i'm not clear whether it will still be available to the rest of the networked computers (one also windows me and one windows xp) when i'm using ubuntu.  my hard drive currently has primary partition 6.34gb (2.92 used) and extended partition with 3 logical drives, all fat32 format (formatted from win me boot floppy) and all logical drives in the extended partition basically full.  do i need to reduce my primary partition (where windows is) as much as possible and create separate logical drives for ubuntu and the swap?  is the 3.4gb remaining enough for these?  i was going to make 512mb for the swap and the rest for ubuntu.  i don't want to lose any data from the existing logical drives in the extended partition when i gparted it.  from what i'm reading in the other threads, ubuntu needs it's own logical drive, which would be in the extended partition area if i'm correct that the primary partition can only contain one logical drive (that's how it worked when i first partitioned it at any rate).  i'm using the ubuntu 6 edgy cd (burned from iso) because i can't run ubuntu 7 as a live cd - i get an error message text over the splash screen "disk error 20, ax=4200, drive ef" and a pop-up "error reading boot cd".  i get the same error messages whether i select run/install or check cd.  i can explore the cd contents from windows, but i only get the initial "launching browser" splash screen when i mount the disk in windows then nothing...  anyway i'm all confusulated and don't know what to do in gparted to get things ready for installing ubuntu - please help.

---

### Post by tommcd on 2007-05-04
If your fat32 logical partitions are all full, and you don't want to remove any of the data, then your only option is to instal to the 6.34GB partition. The ubuntu installer can resize that partition to make room for ubuntu. I would give ubuntu 3 GB (barely enough) and leave the rest for windows, since you said windows was apready 2.92 GB. The swap file can be 2x amount of ram, but since you are low on hard drive space, you can make swap 256mb if you are low on space, how much RAM do you have?
About the errors on the fiesty disk, you may want to try burning it again at a very slow speed, and check the md5sums:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) for burning iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) for md5sum
Hope this helps, and welcome to the forums!

---

### Post by souldances on 2007-05-04
thanks for the welcome.  :-)  i have 1.5gb ram, so i'd guess the smaller swap file will suffice.  am i correct that the swap file requires its own logical drive too?  does the ubuntu installer automatically resize and create what it needs without deleting anything?  it looked to me like it was going to have at the entire physical drive if i let it decide what to do, so i started to do a manual resize and decided i'd better ask questions first & make changes later rather than lose the data in the extended partition logical drives.

i'll try reburning the fiesty cd at a slower rate and do the md5sum check - i let it burn at whatever speed nero chose to use and didn't do the check, so that sounds like the prime suspect there.

is the ubuntu computer likely to communicate with the windows machines on the home network such that we can continue to share files and printers (i haven't found any info about networking with windows machines)?  if so, i'd be willing to kill the windows and give ubuntu room to breathe as i really can't think of any other reason to keep win me - ubuntu's got everything i need already (or it's available in the programs repositories).  i think this is something i can do after the ubuntu install, too, it's just a little trickier that way...

---

### Post by tommcd on 2007-05-04
With a hard drive that small it would be better to use the entire 6.34GB hard drive for ubuntu. That way you will have enough room to install programs plus store files in /home directory. Ubuntu will be able to read and write to your fat32 data partitions, so you can still use them.
When you get to the partitioning part you can choose "automatically resize partitions",  or whatever it says, but I'm not sure how it would handle a drive with all those partitions. Your best bet is to choose "manually edit partition table". Delete the 6.34GB partition, then repartition the now free space. Make a / (root) partition and a swap partition. The swap can be 500mb, and the rest for root. You could also create a separate /home partition, but with a drive that small you may be better off just setting one big partition for root, which will then create a /home directory inside it. You could also back up the data on the fat32 partitions, then delete them when you install ubuntu, then use that now free space for a /home partition. Then just copy the data onto /home when you are finished installing.
As for a home network, I have no experience with that. There is a separate networking forum here. There is a program called samba that is used for networking. I don't know anything about it though.
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29)
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)
Write back if you need to. Good luck.

---

### Post by tommcd on 2007-05-04
Almost forgot. See this site. It has an excellent guide to installing and partitioning:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by souldances on 2007-05-04
thanks so much for the pointers and links.  it looks like i'll be able to network with at least the xp machine, so i think i'll wipe the 6.34gb, split it into 512mb swap and the rest / root and send micros**t packing.  probably won't get to it till at least this evening - i'll post my results when i've had at it.  thanks again  :-)

---

