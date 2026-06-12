---
title: "Ubuntu dual boot partitioning and file rearranging"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-11
All right, I'd like to create a dual boot on my laptop. Yeah, I know, heard it before, read these pages. I at least think I have slightly more specific questions...

I just started the install process for ubuntu, and played with fire by rearranging the partitions in the drives. Afterward I got cold feet and aborted but the partitions had already been made, but fortunatly my windows system appears to be fine.

Here's my situation: right now there's an odd 39MB partition at the beginning of the drive that I'd like to get rid of, but I don't know what's on it so I'm a bit worried about destroying it. Any ideas as to whether this is of any significance?

I did create a ~60GB partition that has basically all the windows stuff on it; it's the boot partition, so it's got the entire windows install and all of my files, some of which I'd like to be able to access in Ubuntu. I created a 10GB partition for the Ubuntu install. I then made a 5GB partition for swap.

I do know that I can probably downsize swap and upgrade the Ubuntu / drive a bit to allow for more add-ons. What I would like to know though, is how I could put all the Windows installation files and windows programs on a separate partition (assuming I can get rid of this 39MB partition). That way I can have Windows install, file storage, Ubuntu install, and swap, respectively. However, the partition manager in the Ubuntu install is really not any help.

Any suggestions for me?

Also, how would I go about making an extended partition? I'm not sure I need one, but the answer is not immediately obvious for that either.

Thanks,
Dan

---

### Post by be4truth on 2007-08-11
There is no need for a 5GB swap at all. I run a 2GB Ram machine with 2GB swap and never run into trouble. If you laptop has 512 or 1 GB just double this for the swap and that's it. 10GB for Ubuntu is tight. I started like this but run out of space 6 months later. If you want to burn a DVD you need 4.7GB temp space!
I guess the 39MB are form the laptop producer for either boot stuff or recovery stuff. If you are not desperately in need of this 39MB better don't touch it.
I usually have first primary partition for windows, then swap 2nd primary, the a logical with a many other as I need. There is where Ubuntu sits in one logical partition.

---

### Post by dbsoundman on 2007-08-12
That makes sense. I was thinking my proportions were off a bit. Any advice on how to create a logical partition? I have no idea how that works. Also, how can I move the content within the partitions around, such as putting the windows boot stuff by itself, things like that?

-Dan

---

### Post by be4truth on 2007-08-12
You can do a lot with Gparted Live CD (check their web page). This is one Open Source partition magic like thing. Be aware that playing with partitions is dangerous. You might lose everything if you make a mistake. A proper backup of all data is indispensable. IN principle you can shift content of partition and partitions themselves around but every action is tricky and may led to loss or damage of partitions or boot loader etc. 
The good thing about using a live Cd like Gparted is that operating systems are sleeping. So while moving a partition the operating can't interfere. You might have some surprises when it wakes up afterwards. 
I played ones on an old machine. I install windows and several Linux OS and shifted them around like mad. After every shift I booted them to check if they are still OK. That was fun because no data were on the box and I didn't need it the next morning!.
But to do the same on a "good" machine is less enjoyable.
Gparted is intuitive and let you make Logical partitions. Before you start with this read a bit what theses partitions are (wiki paedia).

Look here as well
[http://ubuntuforums.org/showthread.php?t=500020]("http://ubuntuforums.org/showthread.php?t=500020")

---

### Post by dbsoundman on 2007-08-12
All right, I think I understand a bit better now. So once I get the GParted thing going and get more logical (heh heh) partitions going, once I get back into windows will I be able to see the different partitions somehow such that I can move all my files into the linux /home partition to share between both OS's, and then leave just the windows install and program files on their partition?

Thanks,
Dan

---

### Post by be4truth on 2007-08-13
You have XP partitions with NTFS file format
You have an Ubuntu swap partition somewhere with the linux swap file format
You have somewhere at least one linux partition probably with ext3 file system

You might have data partitions either in NTFS or FAT32 or ext3. 
There is software available to read/write linux partitions from Windows [http://www.fs-driver.org/]("http://www.fs-driver.org/") 
I have installed this but don't use it much. I am still a bit worried about the Linux files
You can access NTFS from Ubuntu [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")
Search on this site for NTFS and FAT32 if you want to mount simple FAT32 partitions.
I store my data on FAT32 and Linux and had never any problems.
Come back if you need more help.

---

### Post by dbsoundman on 2007-08-15
So, currently my Windows partition is NTFS. Once I create my "data" partition to use between the two OS's, would FAT32 be better, or should I use NTFS? The Linux install part will be ext3, and of course swap will be swap, but I'm just not sure what to use for the storage area. Also, I'm assuming that I will be able to see this storage area as a separate harddrive once I boot Windows right? I plan on making the windows install its own partition, then create an extended partition with my storage area and Linux install, and then the swap partition. Will this work out all right?

-Dan

---

### Post by be4truth on 2007-08-15
Find attached a how to for partitioning. I am working on it but this is the first draft.

---

### Post by patricktn on 2007-08-22
Hi Be4truth,

I realized that you are using 82566DC Gigabit Network Connection. I'm using that too but after installation of ubuntu (my first time using ubuntu), it doesn't detect the presence of this network connection. May I know how you got ubuntu to detect / work with 82566DC Gigabit Network connection ?

Thanks,
Patrick.

---

### Post by be4truth on 2007-08-23
> **patricktn said:**
> Hi Be4truth,

I realized that you are using 82566DC Gigabit Network Connection. I'm using that too but after installation of ubuntu (my first time using ubuntu), it doesn't detect the presence of this network connection. May I know how you got ubuntu to detect / work with 82566DC Gigabit Network connection ?

Thanks,
Patrick.

Have a look at my screen shot:



Could you start a new thread for your problem? Under Networking?
Thx

---

### Post by ArtF10 on 2007-08-23
The DEFINITIVE GUIDE TO DUAL BOOTING:

[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Oh, and I find that G-Parted runs best off the Live-CD.

---

