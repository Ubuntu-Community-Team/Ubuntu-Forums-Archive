---
title: "Setting up partitions"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Zanwar000 on 2006-12-10
I am planning on finally installing Ubuntu on my laptop tomorrow. I have read some partition planning websites and I still cannot decide. I only have a 80gb(in actuality 69.8) hard drive so I plan to keep 30.2 for my XP partition, 15 for a FAT32 partition, 1gb for swap and the rest for Ubuntu. What I want to know is should I merge the FAT32 partition and the Ubuntu partition because of any advantages ext3 might have over FAT32, I have heard that FS Driver will allow XP to utilize ext3?

Also how much space does the a full installation of Ubuntu take up? I planned on having just enough space on one partition for Ubuntu and a second partition for a /home partition. Will this be a good idea?

Thank you for any help.

---

### Post by aysiu on 2006-12-10
Was this one of the partition planning websites you read?
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Zanwar000 on 2006-12-10
Yes, first one too. But I have heard that there is a lot of fragmentation on FAT32 and it will have many disadvantages to FAT32 and NTFS. Should I stick with FAT32 or go with ext3?

---

### Post by aysiu on 2006-12-10
It really could go either way. The disadvantages of FAT32 are:
1. Fragmentation
2. Can't support files over 4 GB
3. Takes up partition space (i.e., you have to set aside yet another chunk, whereas with the FS Driver, you can have all your shared space on the Ubuntu partition)

I don't know if you have files over 4 GB, and since it is a dual boot, you could always defragment the drive from the Windows side. I guess the real question is how flexible do you want your partitions? And are you definitely not going to mess with configuration files using the FS Driver?

---

### Post by Zanwar000 on 2007-02-26
I feel bad about bringing this old thread back to life but I am still lost and I want to give Ubuntu another go. :oops:

I have a hard drive of about 69gb. I have 39gb for windows and the rest I will share and have for Ubuntu. I am thinking 15gb for Ubuntu and 15gb shared. How should I set up the partitions? This is my current plan.

1. Windows Partitions (NTFS): 39gb.
2. Shared Partition (Ext3): 15gb.
3. Swap (I have 1gb RAM): 1gb.

Now I have no idea what to do for the Linux partition. Do i need different logical partitions for stuff like /home and /usr? What are the advantages? Should I?;

4. /root (Ubuntu): 5gb.
5. Logical Partition:
    1. /home: 6gb
    2. /usr: 3gb.

I understand the /home is like My Documents but do I need both /home and /usr if I only plan to have one account that is password protected and the other that is only guest?
If I won't need /usr should I add this space to /home or /root? Where would I install files for Linux /home or /root?:confused: 

Thank you.

---

### Post by kevinf311 on 2007-02-26
Well, here is how I have my drive set up. It is a 120GB (115 really) drive, but the principle is the same.

[--XP_25GB_ntfs--][---------/home_60GB_ext3---------][--Ubuntu( /)_25GB_ext3--][swap_4GB]


I have FS-driver for the read/write in windows. My music, pictures, and other files are all in /home. Each respective OS partition has system files and installed programs. This split may work for you:

[--XP_39GB_ntfs--][------/home_17GB_ext3------][--Ubuntu( /)_12GB_ext3--][swap_1GB]

I have pretty much everything I need installed and have only used 10GB of my root partition, and I've installed... a lot. This set up has worked well for me especially since I had to reinstall Edgy after an interesting battle with some bad DIMM slots but was able to retain all the files in my /home partition.

---

### Post by webofunni on 2007-02-26
I had only one hardisk with 7 partitions 5 of them are windows ntfs partition and one is ext3 and other one is swap. The all partitions in ntfs is listed in ubuntu as removable media. Why its behave like that. Why does it takes those partition's as part of filesystem partitions

---

### Post by Lingy on 2007-02-26
I am newbie to linux/ubuntu. I have drapper installed and read the whole 89 basic manuel pdf.
Unforunatly I am having a problem with creating a partition. It seems that all the instructions out there tell you how to create a partion when in WindowsXP for ubuntu but not while in Ubuntu.

I tried to do it but here is the problem. I installed ubuntu on a computer with 40gig hard drive overwriting an old Windows Xp install. Everything works fine. When logged in to an administrive user (the original user created when installed) and I access QTparted in System Tools under Applications, the hard drive is not visable. It  says “no device found maybe you're not using root user”. Now when I login with root user QTparted is not listed in System Tools.

How can one partition the hard drive with ubuntu??
Thanks for your time

---

### Post by kevinf311 on 2007-02-26
I think that the reason that you cannot edit the partition is because it is mounted while you are logged into the system.

If you want to edit the partition (resize to allow for more partitions maybe?) you need to do so from the Live CD or another bootable partition editing disk. When you boot from one of those, everything is loaded into RAM and the hard drive is not mounted. From the live disk, you can then edit the partitions using whatever partition editing program you feel comfortable with.

Hope this helps.

---

### Post by kevinf311 on 2007-02-26
> **webofunni said:**
> I had only one hardisk with 7 partitions 5 of them are windows ntfs partition and one is ext3 and other one is swap. The all partitions in ntfs is listed in ubuntu as removable media. Why its behave like that. Why does it takes those partition's as part of filesystem partitions

I'm not sure why this is so. I am not able to see my ntfs partition at all, but I don't have any thing installed to handle ntfs. If you are using a specific program to read/write to ntfs perhaps there is something that explains how it handles other filesystems. What are you using to read/write to ntfs?

---

### Post by Lingy on 2007-02-27
> **kevinf311 said:**
> I think that the reason that you cannot edit the partition is because it is mounted while you are logged into the system.

If you want to edit the partition (resize to allow for more partitions maybe?) you need to do so from the Live CD or another bootable partition editing disk. When you boot from one of those, everything is loaded into RAM and the hard drive is not mounted. From the live disk, you can then edit the partitions using whatever partition editing program you feel comfortable with.

Hope this helps.

I was sorta of thinking that, thanks for clearing it up!
Any program you suggest using. I am going to put centOS on the hard drive also, want to try out different versions of Linux and how they work as a server.

Can I do it when installing CentOS? With out first using a partition program?

Thanks again for your time.

---

### Post by spyder0080 on 2007-02-27
> **kevinf311 said:**
> Well, here is how I have my drive set up. It is a 120GB (115 really) drive, but the principle is the same.

[--XP_25GB_ntfs--][---------/home_60GB_ext3---------][--Ubuntu( /)_25GB_ext3--][swap_4GB]


I have FS-driver for the read/write in windows. My music, pictures, and other files are all in /home. Each respective OS partition has system files and installed programs. This split may work for you:

[--XP_39GB_ntfs--][------/home_17GB_ext3------][--Ubuntu( /)_12GB_ext3--][swap_1GB]

I have pretty much everything I need installed and have only used 10GB of my root partition, and I've installed... a lot. This set up has worked well for me especially since I had to reinstall Edgy after an interesting battle with some bad DIMM slots but was able to retain all the files in my /home partition.

Hello all,

This question is directed more to kevinf311 but I'll be happy if anybody answers

I am also trying to configure my laptop with this type of setup. However, I want to clear up a few things before I do anything.
1. If I mount the windows partition during installation, then should I automatically be able   to read/write my windows files in Ubuntu using the /home partiton? (I plan on using 6.10). 
2. Approximately how much space (percentage wise) should I reserve for each partition? If I want to install new programs, then would they go in their respective partitions?
3. Is there any way to prevent non-admin users of my computer from accessing my /home partiton in windows? If I can't then it's no big deal, but I just want to know.

Thanks!

---

### Post by spyder0080 on 2007-02-27
I also forgot to ask,

Would the size of my partitions matter if I plan on using both windows and ubuntu to program?

Thanks!

---

### Post by kevinf311 on 2007-02-27
> **Lingy said:**
> I was sorta of thinking that, thanks for clearing it up!
Any program you suggest using. I am going to put centOS on the hard drive also, want to try out different versions of Linux and how they work as a server.

Can I do it when installing CentOS? With out first using a partition program?

Thanks again for your time.

If the CentOS installer has a partition manager included on it, then yes you can do this during installation. If it does not then you will need to edit the partitions yourself. I am most comfortable with the program gparted that comes on the Ubuntu Live CD. If you boot with the Live CD and run gparted (I think it can be found in one of the drop-down menus in the gnome DE on the Live CD) then you can resize your existing partition and create a new one for CentOS to be installed to.

After the program successfully creates your new partition (I suppose if you are going to be installing more than one OS at a time you can go ahead and create those partitions too, most drives can only have 5 primary partitions though) you can go ahead with the CentOS install and in that installation choose the new partition that you just made.

I haven't used CentOS so I am unfortunately unfamiliar with their installation process.

---

### Post by kevinf311 on 2007-02-27
> **spyder0080 said:**
> Hello all,
...
1. If I mount the windows partition during installation, then should I automatically be able   to read/write my windows files in Ubuntu using the /home partiton? (I plan on using 6.10). 
2. Approximately how much space (percentage wise) should I reserve for each partition? If I want to install new programs, then would they go in their respective partitions?
3. Is there any way to prevent non-admin users of my computer from accessing my /home partiton in windows? If I can't then it's no big deal, but I just want to know.

Thanks!

1. Are you referring to choosing a designation for your windows partition during installation (without reformatting)? If this is the case and you have a program installed that will read/write to ntfs on your Linux installation (like ntfs-3g) then you should be able to access your windows files. Here is the [HowTo]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read%2Fwrite") for ntfs-3g, it's kinda old, so you might want to check out the site to see if there is an updated method. Alternatively, if you are setting up the partitions like I have mine, you can use [FS-driver]("http://www.fs-driver.org/") in windows to read/write to ext2 partitions (which will work with ext3). This would mean you will have to move all of your files into the /home partition. It was easy for me because I was starting from scratch w/ backups.

2. After checking my space again, I've actually only used about 5GB in Linux. Installable programs/applications should go in the respective OS partition while settings, files, music, etc should go in /home. I wouldn't recommend less than 20GB for windows but you can go pretty small on the root Linux partition. If your files are all going in /home make it the largest, if you are going to be pulling from the existing windows partition then make it the largest. How big is your drive?

3. The only thing I can think of is making an Admin user and a non admin user in windows and then only allowing the Admin account to utilize the FS-Driver program. I'm not sure I remember how to do this.

---

### Post by spyder0080 on 2007-02-27
> **kevinf311 said:**
> 1. Are you referring to choosing a designation for your windows partition during installation (without reformatting)? If this is the case and you have a program installed that will read/write to ntfs on your Linux installation (like ntfs-3g) then you should be able to access your windows files. Here is the [HowTo]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read%2Fwrite") for ntfs-3g, it's kinda old, so you might want to check out the site to see if there is an updated method. Alternatively, if you are setting up the partitions like I have mine, you can use [FS-driver]("http://www.fs-driver.org/") in windows to read/write to ext2 partitions (which will work with ext3). This would mean you will have to move all of your files into the /home partition. It was easy for me because I was starting from scratch w/ backups.

2. After checking my space again, I've actually only used about 5GB in Linux. Installable programs/applications should go in the respective OS partition while settings, files, music, etc should go in /home. I wouldn't recommend less than 20GB for windows but you can go pretty small on the root Linux partition. If your files are all going in /home make it the largest, if you are going to be pulling from the existing windows partition then make it the largest. How big is your drive?

3. The only thing I can think of is making an Admin user and a non admin user in windows and then only allowing the Admin account to utilize the FS-Driver program. I'm not sure I remember how to do this.

Thanks for replying!

I plan on partitioning my hd exactly the way you are. The difference is that I have a smaller hd (approx 55 GB). I already have windows installed, but I haven't done anything with ubuntu yet.

I'm worried about the partition sizes because I plan on doing development on both Windows and Linux. I'm not sure how much space dev tools/IDE's/compilers take but I am thinking about putting my source code, etc on my /home space because that seems like the logical thing to do. I also don't want to worry about running out of space when I install new programs on either OS.

Thanks again for your help!

---

### Post by kevinf311 on 2007-02-27
Ok. Do you happen to know how much space XP has taken up? If you can backup and remove any unnecessary files from the windows partition and then defragment it. If there are too many fragments spread out over the partition gparted will have trouble resizing it.

Let's say you can get it so that windows takes up 30GB (with 5 or more GB free) then you can have 25GB left for Linux. 1GB will probably suffice for swap, then you have 24GB for root and home. For this split you can go 12/12 or 10GB for root and 14GB for home.


As I said I have about 5GB used on my root partition. I don't really know how much dev packages will take up. Do you need both the normal and dev packages for certain apps? Or are you mainly going to need software writing apps? If that is the case then you can probably skew the split more to free up space in /home. I probably wouldn't go lower than 8GB since you never know what you might want in the future (like an entire DE or WM).

---

### Post by spyder0080 on 2007-02-27
> **kevinf311 said:**
> Ok. Do you happen to know how much space XP has taken up? If you can backup and remove any unnecessary files from the windows partition and then defragment it. If there are too many fragments spread out over the partition gparted will have trouble resizing it.

Let's say you can get it so that windows takes up 30GB (with 5 or more GB free) then you can have 25GB left for Linux. 1GB will probably suffice for swap, then you have 24GB for root and home. For this split you can go 12/12 or 10GB for root and 14GB for home.


As I said I have about 5GB used on my root partition. I don't really know how much dev packages will take up. Do you need both the normal and dev packages for certain apps? Or are you mainly going to need software writing apps? If that is the case then you can probably skew the split more to free up space in /home. I probably wouldn't go lower than 8GB since you never know what you might want in the future (like an entire DE or WM).

I don't exactly know how much XP is taking up, but I'll go with your estimates. 
For right now, I just need c/c++ and java compilers and IDE's. I would need space for compilers for other languages though (if they aren't already available). I know all linux distro's come with gcc and g++. I don't know about Java; Even with everything, I guess it shouldn't take up too much space. 

If your estimates are accurate, I'll go with the 30 GB XP/10 GB root/14 GB home idea.

Thanks!

---

### Post by kevinf311 on 2007-02-27
No problem, hope everything works out for you!

---

