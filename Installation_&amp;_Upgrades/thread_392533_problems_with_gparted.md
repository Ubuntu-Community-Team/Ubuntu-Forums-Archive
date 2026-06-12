---
title: "problems with gparted"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by mardawi on 2007-03-24
Hi,

I'm trying to have a dual boot system (windows/ubuntu). But every time i try to install ubuntu, Windows can no longer see it's NTFS partition and gives me the lovely blue screen when booting. When i try to reinstall windows, it shows my hd as a single "unknown" partition.

I've tried installing windows and ubuntu in almost all possible scenarios (resizing the windows partition, leaving unpartitioned space for ubuntu, creating NTFS partition for windows after installing ubuntu.. etc). I think there is something wrong gparted is doing, is there another program that can fix my hd partitions after installing ubuntu?

Thanks.

---

### Post by chewearn on 2007-03-24
Are you trying to install dual boot on a single harddisk?  Or on two harddisks (each harddisk holding one OS)?

---

### Post by mardawi on 2007-03-24
on a single hd. it's on a laptop, so i can't install another hd.

---

### Post by chewearn on 2007-03-24
Ok, the normal/safe way to install dual boot on single HD:

First install Windows
During first part of Windows installation, make sure you already create partition of the right size in the Windows setup; leave the remaining HD space unallocated

Second, install ubuntu
Choose the option to automatically install ubuntu in the largest continuous free space

Apology if you have already tried it this way.

---

### Post by mardawi on 2007-03-24
Yes, i've tried that already with no luck!

is it possible that gparted is doing something wrong with my hd?

---

### Post by chewearn on 2007-03-25
Apology again, I have never encountered the problem you described with GParted.

Could you post your make and model of laptop?  Maybe someone else in this forum might have the same hardware, and can comment.

Another method I can suggest is use a newer version of GParted (comes in a 50MB liveCD):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

That means, the steps are:
First install Windows
During first part of Windows installation, make sure you already create partition of the right size in the Windows setup; leave the remaining HD space unallocated

Second, create Linux partitions
Create ext3 and swap.

Third, install ubuntu
Choose manual, select the partitions created in second step as root and swap.

---

### Post by mardawi on 2007-03-25
Thanks a lot for the link.

I've downloaded the iso image, burned it, and booted from it. I've tried creating an ntfs partition for the windows installation but windows still can't find any partitions (i currently have ubuntu installed). Then I tried using the testDisk utility in the live CD and it gave me some errors about over lapping partitions or something... Could that be the problem?

I have a ThinkPad T40, 40 gigs HD and 1.5 gigs ram.

---

### Post by louieb on 2007-03-26
Well I guess I jump in and if were mine this is what I would do.
Have on hand 3 CD's.[LIST]
[*]GParted 3-3.7 or later (some ealier versions had a problem shutting down)
[*]Windows install disk. (XP service pack 2 I hope, if not post back with your windows version)
[*]Ubuntu install disk. (which version?)[/LIST]Use the GParted CD first. Delete all the partitions on the drive leaving 100% unallocated space.
Now you are going to create 4 partitions you are just going to have to decide how much of the drive to give to each.[LIST=1]
[*]1st partition for widows let GParted format it fat32 or NTFS it really doesn't matter. You are going to let the windows install format it later. (minimum size 10 gig)
[*]2nd partition for Ubuntu format it ext3 again it really doesn't matter. You are going to let the Ubuntu install format it later. (5 to 7 gig)
[*]3rd partition for Ubuntu's /home format it ext3. use all but 1/2 to 1 gig of the remaining space.
[*]4th partition for Linux swap. format it Linux swap. With a gig and a half of memory a 1/2 gig swap should be plenty.[/LIST]Click on the apply button and let GParted do its stuff. When its done leave the GParted CD in and reboot the computer. If everything looks ok then it time to install windows.  Haven't install XP in a while but you should be able to tell it to install itself in the first partition and let it format the partition. 

When  you get Windows installed and running.  Post back and I'll go through how to use the partitioner in the Ubuntu installer. Can't tell you until I find out which version of Ubuntu and if you have:  the live CD or the alternate CD.

---

### Post by mardawi on 2007-03-26
I've downloaded and burned gparted-livecd-0.3.4-5.iso from [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) just yesterday, is this good enough?

I have Ubuntu 6.10 LiveCD, and Windows XP SP2 installation CD ready.

Should i start now?

---

### Post by louieb on 2007-03-26
You have the latest GParted CD. It  looks like your in good shape to start. 

When you get done installing XP and have verified it works. You can start installing Ubuntu. Enter the stuff it asks for until you get to the partitioning screen. At that point you are going to choose manual partitioning. 
The first screen will look like the GParted screen. Since you have already partitioned your drive you won't do anything on that screen. The next screen is where you tell where to mount the partitions. 
It may have guess right at the mount points for the 4 partitions. There will be some drop down lists on that screen 2 lists for  each partition. also there will be a check box asking if you want to format the partition.  
One of the columns will list the partition and look like /dev/hda1 or it may be /dev/sda1 any way before you leave that screen it should look something like this:
```

partition        mount point           format box
/dev/hda1     /media/windows      format box unchecked      
/dev/hda2     /                              format box checked      
/dev/hda3     /home                     format box checked
/dev/hda4     swap                       format box checked

```Once you get it looking like this your ready to install. Just go for it and see what happens. It should work .:guitar:

---

### Post by mardawi on 2007-03-27
Thank you AstalaVista... Thank you louieb.
I finally got ubuntu and windows to work! :guitar:

It seems it was actually a problem in GParted, what i've noticed lately it was written on my hd that it has 16 heads but when viewing the device info in GParted it showed 255 heads (I have no idea what that is!). so, i think GParted was partitioning my hd is a way that windows can't read!

I've done the following if anyone is interested:
[LIST]
[*] booted from Windows CD and Deleted the unknown partition that Windows was showing 
during the setup.
[*] Created a 10gig ntfs partition and installed windows on it.
[*] Bought PartitionMagic for $70 ( a wrong decision since a new hd wouldn't cost much more!)
[*] Created the linux partitions with PartitionMagic in the way that louieb advised.
[*] Booted from ubuntu 6.10 liveCD
[*] luanched GParted from Administration>Gnome partition manager and reformatted the ext3 linux partition to ext3 (this was required becuase ubuntu installer will refuse to install the root system files on the partitions that were formated with PartitionMagic)
[*] selected manual partitioning during the installation.
[*] Did nothing in the partitoiner and just clicked next
[*] Selected the mounting points as louieb advised.
[/LIST]

After that.. everything went normal and now i have both Windows and Ubuntu on my ThinkPad T40

---

### Post by louieb on 2007-03-27
> **mardawi said:**
>  it was written on my hd that it has 16 heads but when viewing the device info in GParted it showed 255 heads 
Even though the drive has 16 physical heads a lot of hard drives report to BIOS that they have 240 or 255 heads. Don't ask me why. I did a Google search on **255 heads** and it seem to have something to do with some DOS limitations.   

:popcorn:Glad you got it going. How do like the T40? I am finally going to buy  me a laptop.  The wife and both kids have theres, now its my turn.

---

### Post by mardawi on 2007-03-27
I have both T23 and T40, and thinking about buying a T60 in the next few months. This series costs a lil' bit more than other laptops but totally worth every dollar! they are very slim and light, and they don't get damaged quickly.

Check this link for more information about T40 and Linux:
[http://bellet.info/laptop/t40.html](http://bellet.info/laptop/t40.html)

---

