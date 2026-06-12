---
title: "Install program can't see the HDD partitions"
date: 2004-11-28
forum: Installation &amp; Upgrades
---

### Post by sherbyx on 2004-11-28
I've just burned a CD with UBUNTU 4.10.
All worked well but at the "partitioning menu" the program can see the HDD but it can't see any of my partitions. I've got:
1 - FAT32
2 - FAT32 - WIN 2000
3 - FAT32 - other WIN 2000
4 - linux swap
5 - linux ext 3 -  with Mandrake 10.
I just want to format the partition 5 and install UBUNTO instead of MDK10 but my only option is to erase the entire partition table and rewrite it, destroying my data.
What should I do?

---

### Post by FLeiXiuS on 2004-11-28
Sounds like the partition tables are already screwed  up if Ubuntu recognizes them as 1 drive.  Your best bet would be to backup your data and reformat / repartition.

---

### Post by sherbyx on 2004-11-28
Thanx for the answer, but this is not an option.

---

### Post by sherbyx on 2004-11-28
The strange thig is that any other ditribution or any other windows or partitioning program can see my partition table as it is.

---

### Post by Xian on 2004-11-28
When you say "any other...partitioning program" does that include parted? Can you run parted from another distro and get no error messages while reading your disk?

---

### Post by wallijonn on 2004-11-28
Do you have more than 4 bootable partitions? Is the Mandrake on it's own root (instead of writing to the MBR) and is it set to bootable?

---

### Post by sherbyx on 2004-11-29
No, when I say "any other partitioning program" I don't refer to parted I refer to mandrake's programm, partition magic, fdisk & cfdisk and maybe other distribution of linux.
I don't have Mandrake anymore. As mater of fact I've deleted the MDK partiton. Now it's free space and the installer doesn't see it.

---

### Post by Xian on 2004-11-29
I would surmise that the problem is with Parted not being able to properly read your disk due to some partition geometry errors. This will generally not effect cfdisk, fdisk, and other windows applications like acronis and partition magic. It is generally caused by some brand of partitioning software not setting the disk geometry correctly during a write session.

The true test of this would be to try and run Parted during a linux session (perhaps on a Live CD if you have no HD installation at present), and see if it returns some error messages while reading your disk. Parted is what the Ubuntu CD uses and I am unaware of a way to bypass this step by using a different partition tool during installation. You can go into verbose mode and run Parted from the command line while installing by using the Function keys, and perhaps you should do this if for no other reason than to further troubleshoot this problem. 

If this is the issue I can only think that to correct you would have to start your partitioning from scratch.

But I would first attempt to verify by using the methods suggested or some other means.

---

### Post by scotty on 2004-12-01
To clear things up a little, I too am having the same troubles.  I use Ubuntu at home and would like to put it on my work machine.  When I run the installer it only see the whole Western Digital HD and will not allow me to work with partitions.  My objective is to trash Slackware and go to Ubuntu.

I tried a Mepis CD this morning to be able to run QParted as posted above.  QParted could not access hda at all.  Ubuntu's partition tool cannot either.  However, cfdisk under Mepis can access hda and show the partition table.

Now, there's about 12-13 gigs of information on this HD that isn't able to be easily moved off the WinXP side of the drive, so backup-repartition-reinstall is a hassle to say the least.

Is there any way out of this hole so that I can trash Slack and not WinXP?  I like Ubuntu a lot and it's brought me back to Debian after a LONG absence.

Thanks,
Mail or post,
Scott Strungis

---

### Post by Xian on 2004-12-01
Aside from having a professional assist you in reconstructing the proper disk geometry I do not personally know of any way to correct this problem other than to backup/repartition the HD.

If you Google this subject regarding parted and geometry partition errors, you'll quickly see how problematic a repair can be.

Of course, you could just do a complete walk-around and install the latest version of Gnoppix to your HD. It is based on the Ubuntu packages and will set up a Warty desktop that is identical to the Ubuntu CD. There are a few binary packages that are native to Gnoppix which remain, but these can easily be removed with Synaptic. Just set your repo's to Warty and you are basically set.

Gnoppix doesn't have a HD installer on the live CD disk, but on the Gnoppix forums is a link to the installer binary package that will allow this procedure to be completed. It is dependent upon another .deb file but that is also available.

---

