---
title: "Setting up of Partitioner freezes"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by trothigar on 2007-07-01
I get all through the first 3 steps of installation and then when it is setting up the partioner it goes straight to 46% (Scanning disks) and then stays like that and stops being responsive.

Please help.

---

### Post by Pumalite on 2007-07-01
We need more info. In general what I would do: if dual booting with XP; defrag several times, get rid of all temp files and then set up partition. If installing to another drive I would use Gparted and clean and format that drive to ext3 first, then install to it and use 'Guided>Use Entire Disk'. Your problem might me of a different nature though; you might have little memory: 256 of RAM or less>Xubuntu Alternate CD. Or you might have a corrupted file. Check your iso. Do checksum, burn at 1x, etc. If dual booting with Vista, you have to partition FROM Vista.

---

### Post by dabl on 2007-07-01
Concur with Pumalite's advice regarding XP and dual boot.

If there's difficulty with partitioning, I recommend making a GParted Live CD by downloading and burning the ISO from here:  [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then, boot the GParted CD and you can focus on getting your drive partitioned exactly as you wish.  Once you have that done, you can boot the Ubuntu live CD and install without dealing with partitioning.  Just let Ubuntu format the applicable partions as you install it.  I also recommend the "Alternate Install" Ubuntu CD, for more control over the process.

---

### Post by trothigar on 2007-07-01
My harddrive has just one blank ext3 partition on. I have 1Gb of ram. I can partition fine with gparted on the fiesty live cd. Could it be a corrupt install disk?

Thanks

---

### Post by dabl on 2007-07-01
> **trothigar said:**
>  Could it be a corrupt install disk?

Yes it could.  To find out for certain, download the ISO image again, and burn a new CD, but this time set your burn speed down to 4X, and don't forget to verify the checksum number aka md5 number.

:)

---

### Post by kombucha on 2007-07-01
I'm having a similar issue, except mine gets to 100% of setting up the partitioner, the progress dialog disappears and it locks there. I already have it partitioned as I want it (I'm dualbooting XP and K/Xubuntu already and just want to fresh install Xubuntu over the existing Linux partitions), so I'd be more than happy to skip the partitioning, but it doesn't get that far. I suppose I can try the alt-install disk? I've reburned the iso and am checksumming right now.

---

### Post by dabl on 2007-07-01
> **kombucha said:**
>  I suppose I can try the alt-install disk?

After the first time I used the Alternate Install CD, I've never gone back to the Live CD.  The Alternate provides much more control over the process.

Using the Alternate Install CD, you can just skip partitioning, select your mount points for each partition, have it proceed to format each partition, and proceed with installation.  :)

---

### Post by trothigar on 2007-07-01
I don't have another OS to check the disk on or to burn another cd. I ran the integraty  check on the disk and it came up with two errors.

Now I am installing from a kubuntu 6.06 cd which I have (Slightly annoying because I would l like gnome).

---

### Post by dabl on 2007-07-01
Well, at least you know what happened.  I find Feisty better (more stable and runs the USB stuff better) than Dapper and Edgy on my hardware, which is relatively new.  Others are perfectly satisfied with Dapper.

It is possible, or so I read, to install the Gnome desktop and have the choice to boot into either environment.  I'm not the expert to say exactly how -- something about a metapackage for each one, and the Kubuntu one is named kubuntu-desktop, but I don't know the name of the Gnome metapackage.  Search and you will probably find it. Here's some information along those lines: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)   ;)

---

### Post by trothigar on 2007-07-01
Thanks. I am going to upgrade to fiesty. Your are right in saying the metapackages are ubuntu-desktop and kubuntu-desktop.

---

### Post by kombucha on 2007-07-01
Well I'd recommend installing from that disc, then downloading a newer iso and trying again from scratch. I think that's probably the easiest way?

I got mine working, took two tries with the alt-install disc. :D

---

### Post by Herman on 2007-07-01
Hello everyone,
My tips for anyone installing Ubuntu is to md5sum your downloaded .iso and then after it's burned to disk, check the integrity of the CD. 

If you still have problems partitioning and installing it might be caused by a dirty CD or DVD drive. This has happened to me a few times. A CD or DVD drive can be fine for regular use, like making music CDs or copying files.
I don't know why, but having a good clean lens in the CD drive is particularly important for installing Ubuntu. Maybe it has something to do with the level of file compression used in the Ubuntu install CDs or something, I'm not sure. All I do know is I have experienced similar problems myself a couple of times and cleaning the CD/DVD drive seems to solve the problems right away. 
My wife's desktop needed the DVD drive removed and taken apart and cleaning out before I could install Feisty in it. It was a bit tricky to get it back together again, I would only recommend attempting that if you are used to fixing things and you have all the right tools and you enjoy tinkering.  
Last night I had to clean the lens in my laptop, that was a lot easier because the lens in my laptop sides out in the CD drawer.
I used some compressed air and a Q tip (or cotton bud), with some methylated spirits on it. 
[Smart Computing Article - How To Maintain Your Optical Drives]("http://www.smartcomputing.com/editorial/article.asp?guid=&bJumpto=true&Isfrm=IN&article=articles/webonly/techsupport/24w10/24w10.asp&ArticleID=31106")

[Cleaning your DVD drive]("http://www.llamma.com/xbox/Repairs/cleaning_your_dvd_drive.htm")

...or just go buy a new one, they're reasonably cheap these days. 

I suspect that dirty CD or DVD drives would account for a large percentage of Ubuntu installation problems, especially when it freezes or stalls or you get one of those lovely red screens with a warning message. Cleaning the DVD drive has worked for me.

Regards, Herman :D

---

### Post by trothigar on 2007-07-02
In I did download the alternate install disk and it worked. Thanks.

---

