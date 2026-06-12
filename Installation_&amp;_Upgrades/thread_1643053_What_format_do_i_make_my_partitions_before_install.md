---
title: "What format do i make my partitions before installing Ubuntu"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by eggwardo on 2010-12-11
Hi,
I'm dual booting a windows 7 starter netbook w/ubuntu netbook.
The netbook came with 3 partitions already on it (backup 12 gb, 100mb system, and main windows 35gb (I've shrunk it w/gparted).
I've done a couple attempts at installing, they seem to go ok but when i reboot there isn't the option to choose OS.

So this leaves me with 190ish Gb of unallocated space. Which i plan on splitting into a logic partition.

Here's what i'm thinking the logic partition will look like:
_Name, Format, Size, Mount Point_       
Logic Partition, (???), 190Gb 
--Storage, (NTFS), 155Gb
--Linux Root, (???), 10Gb, /
--Linux Home, (???), 23Gb, /Home
--Linux Swap, (???), 2Gb   

Do i make these partitions with gparted before i start the install?  
And if so how do i format them?   
OR do i use the partition "manager" thing that's part of the installation?
Also, from my readings i'm understanding that i need this "home" partition but i don't know why.  Do i need it?

thanks in advance

---

### Post by Quackers on 2010-12-11
Welcome to UF.
Have you rebooted Windows since making the partition changes to make sure it went ok?
In general, it is safer to use Windows tools to resize Windows partitions.
You can make whatever partitions you want in the Ubuntu installer by selecting the manual option in the partitioning stage of installation (sometimes called "specify manually").

Please note that if you already have 3 primary partitions on the disc, you must not create another primary as this will create serious problems.

---

### Post by sanderd17 on 2010-12-11
Why you need home?

well, this is the default place where all your documents and user-specific settings will come. This pust be an ext3 or ext4 partition because NTFS can't handle user rights.

If you use a separate partition to place all your documents, you don't really need a separate /home since losing your settings isn't as bad as losing your documents.

The home is made a separate partition in many places because it makes a fresh install of the system much more simple, you can just say "there are my settings and documents" instead of copying every file.

About 25GB will be enough for ubuntu with settings and without documents.

The partition manager in the installation wizard is just a build-in simplified Gparted, the same code is used. But it has some extre features to select what partition you want to use for what purpose.

2GB swap is good

Do watch out that you don't have 3 primary partitions already, as Quackers said.

---

### Post by oldfred on 2010-12-11
Your extended partition, I assume sda4 is not formated. It is just a container for all the logical partitions. Swap also does not have a format. 

Your partition sizes look fine as I typically recommend 10-20GB for / and as ext4 or if you want ext3.  /home can be either ext4 or ext3.  Ubuntu's standard is now ext4.

I create partitions  in advance but you do not have to format in advance as you can do that as part of manual install. You should format the NTFS in advance as the installer does not do that. You do have to remember which partition you are using for what. I accidentally installed to the wrong one once. Labeling partitions help, but all screens do not show labels.

---

### Post by coffeecat on 2010-12-11
You might want to think about your decision to have both separate home and data partitions. As sanderd17 says, a home partition is useful for retaining all your personal settings when you re-install, but if you also have a separate data partition, that's a less efficient way of using hard drive space. However, when you want to share data with windows, probably the best way is with a separate shared NTFS partition the way you describe. I always have a separate data partition but I don't bother with separate home partitions. This means I have to set up my personal settings afresh each time I re-install - and believe me, I reinstall a lot - but I don't mind that. There's no right or wrong way - what's best for you is best for you.

You might find this link useful, which answers many of your questions:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck!

---

### Post by eggwardo on 2010-12-11
thanks all of you.  Got it.

Not sure if i was doing the partitioning right but i was definitely picking the wrong option for "Device for boot loader installation".  I was picking the partition that i was putting ubuntu on.  This time i picked the default option and all is good.

Just for future searchers help -
I ended up not using a /home partition.
I created the partitions with gparted before the installation
I did end up reformatting the root drive in the installer because of some popup that seemed like it wanted me to do that

thanks again everyone, i've got more work ahead of me so maybe you'll hear from me again

---

### Post by eggwardo on 2010-12-11
ok, got a problem,  maybe

when i look at my partitions in windows with "disk management"  it says the disk that i thought i put ubuntu on is 100% available.

is there a way i can find out where i put ubuntu?

eveything's working,  should i care?

thanks again

---

### Post by oldfred on 2010-12-11
windows does not see Linux partitions. You have to be careful using windows partition tools around Linux partitions.

I suggest using windows tools on windows partitions, & Linux tools on Linux partitions.
Gparted will show both very well.

---

