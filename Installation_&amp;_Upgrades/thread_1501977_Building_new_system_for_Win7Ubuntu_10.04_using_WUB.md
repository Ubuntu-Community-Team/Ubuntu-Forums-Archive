---
title: "Building new system for Win7/Ubuntu 10.04 using WUBI"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by M3rc Nate on 2010-06-04
So this is my first post on a Ubuntu forum. So far my experience with Ubuntu has been using it in Virtual-Box and as a Live CD and Live-USB. I currently have laying around a CPU/GPU/PSU so i bought the rest missing to build a new computer. I got two hard drives (640gig for Win 7 & 80 gig for Ubuntu). I have been told on [H]ardForum . com to use WUBI. That its not necessarily great for long term usage,  but its best to use WUBI, get the hang of Ubuntu and dual booting and all that...and then eventually to try a more permanent solution. 

For now i am curious is there anything i should know before I start? I bought Win7 64bit so i want to use Ubuntu 64 bit as well correct? 
Are using WUBI and going into the Boot-Menu and starting using the 80gig HDD with Ubuntu on it, two different options? If so which is better in your opinion? 

Btw to install WUBI , do i install windows, put in the CD and click install WUBI which auto pops up, and follow directions and just make sure to have it install Ubuntu 10.04 64bit on the 80gig hard drive?

One last thing, i have seen screen caps of a menu (that looks like a boot menu before you enter your OS) that has options like "use memtest to test your memory" and "Check Ubuntu CD for errors" ....how do i get to that? I would really like to be able to do both of those things. 

Thanks guys, cant wait take off my floaty wings in the shallow end and learn how to swim in the deep end of Linux/Ubuntu :D

---

### Post by Revolutionary101 on 2010-06-04
To install Ubuntu via Wubi, just install Windows and then put in your Ubuntu CD. Once the window for Wubi pops up it is pretty self-explanatory.

Although, I doubt that Wubi will work if you plan on installing Windows and Ubuntu on two separate drives. Wubi installs Ubuntu kinda like a program for Windows. In order to use Ubuntu with Wubi, it would have to be on the same HDD as Windows 7.

---

### Post by oldfred on 2010-06-05
Wubi is inside the windows NTFS partition and uses the windows boot loader. It is for those windows folks who want a longer test than the liveCD and it allows changes to be saved that the liveCD does not allow.

But if you want to dedicate a separate drive, a full install is the better way to go. Most of us here have not used wubi so you will get better support.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

 With two drives it is important to install the grub bootloader to the second drive. You then set BIOS to boot the second drive. Grub will find the windows and let you boot either Ubuntu or windows. And if you every have trouble the windows boot loader is still in the first drive and you can change to that. To be sure grub installs to the second drive on the last screen you have to use the advanced button and select sdb. see graphic:
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by M3rc Nate on 2010-06-05
> **oldfred said:**
> Wubi is inside the windows NTFS partition and uses the windows boot loader. It is for those windows folks who want a longer test than the liveCD and it allows changes to be saved that the liveCD does not allow.

But if you want to dedicate a separate drive, a full install is the better way to go. Most of us here have not used wubi so you will get better support.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

 With two drives it is important to install the grub bootloader to the second drive. You then set BIOS to boot the second drive. Grub will find the windows and let you boot either Ubuntu or windows. And if you every have trouble the windows boot loader is still in the first drive and you can change to that. To be sure grub installs to the second drive on the last screen you have to use the advanced button and select sdb. see graphic:
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Thanks, sounds like installing it to the second hard drive (instead of WUBI) is the way to go. I have heard of GRUB and know a bit about it, that its helpful and lets you choose which to boot into, but that theres some controversy as to how it can get corrupted. Thats just what iv heard, im not saying i am not gonna do it. 
  
I will read through the Dual booting link(s) you gave me, if its clear cut then i will reply in a week with my results, if i have some questions after i read through it, expect to see a new post on this thread. :)   Thanks Old Fred

---

### Post by oldfred on 2010-06-05
The two main issues with grub2 are a user not understanding the difference between a drive (sda, sdb) and a partition (sda1,sda2 etc) and installing grub to every partition corrupting windows. And windows software that writes into the MBR with serial numbers that overwrite grub2 since it is slightly larger than the windows boot loader. The windows software is not following the standard that the MBR or master boot record is reserved for booting. There seem to be a few issues unique to different hardware configurations but most just require and extra setting.

If you are installing grub to a separate drive's MBR you will have neither of the above issues.

---

### Post by M3rc Nate on 2010-06-05
> **oldfred said:**
> The two main issues with grub2 are a user not understanding the difference between a drive (sda, sdb) and a partition (sda1,sda2 etc) and installing grub to every partition corrupting windows. And windows software that writes into the MBR with serial numbers that overwrite grub2 since it is slightly larger than the windows boot loader. The windows software is not following the standard that the MBR or master boot record is reserved for booting. There seem to be a few issues unique to different hardware configurations but most just require and extra setting.

If you are installing grub to a separate drive's MBR you will have neither of the above issues.

Thank you, when reading through that i was planning to ask that but you then answered it in your last sentence. My GRUB will be in the second hard drive where Ubuntu is..so windows should never touch it or see it. 

I do have a question, could i technically, install Ubuntu on the second drive, not install the GRUB, and when i wanted to use Ubuntu OS, when turning on the computer, open the boot menu, choose my 2nd drive and it would boot me into Ubuntu?
I dont want to do that considering GRUB is more convenient but i am just curious.

---

### Post by oldfred on 2010-06-05
You have to have some boot loader in the MBR of a drive.

Computers boot from BIOS load which turns it over to the MBR of the primary master, now with SATA you can use software in BIOS to select primary master or boot disk. Before with IDE drives you set jumpers on the hard drive.

The MBR then either like windows jumps to the PBR partition boot record or boot sector of the partition, or like grub to other files used for booting.

---

### Post by M3rc Nate on 2010-06-05
> **oldfred said:**
> You have to have some boot loader in the MBR of a drive.

Computers boot from BIOS load which turns it over to the MBR of the primary master, now with SATA you can use software in BIOS to select primary master or boot disk. Before with IDE drives you set jumpers on the hard drive.

The MBR then either like windows jumps to the PBR partition boot record or boot sector of the partition, or like grub to other files used for booting.

Ok that makes sense. So basically just cause you have ubuntu on the second drive (without GRUB) doesnt mean you can _Boot_ into that OS, you have to have something in the MBR that loads up the OS. Yeah i think "IDE Drives" were before my time, all Iv ever known is SATA.

---

### Post by M3rc Nate on 2010-06-12
On the Prepare Disk Space, with my 80 gig empty (except a bootloader from my old computers windows 7 on it), it shows the bar as fully green...that blue represents 104.9MB of Windows 7 (loader) (/dev/sdb1) on it, and that green represents /dev/sdb2 79.9Gb
 
Its not showing a empty bar that is blank because of my bootloader that is still on the 80 right? And i just choose "Erase and use the entire disk" and it will be fully whipped and i wont have any isuses?

---

### Post by oldfred on 2010-06-12
there have been one or two that have had the windows 7 boot/recovery partition on a different drive. You are not booting thru  the 80GB. If it is just an old install and you have no data or backed up all data you can just install to the entire drive. 

When you have a entire drive I prefer to keep user data separate from system files (I give same advice for windows). So you can create a 10 to 20-GB / (root) partition a 2GB or size of RAM if you want to hibernate and make the rest /home where all your data and user settings will go.

---

### Post by M3rc Nate on 2010-06-12
> **oldfred said:**
> there have been one or two that have had the windows 7 boot/recovery partition on a different drive. You are not booting thru the 80GB. If it is just an old install and you have no data or backed up all data you can just install to the entire drive. 
 
When you have a entire drive I prefer to keep user data separate from system files (I give same advice for windows). So you can create a 10 to 20-GB / (root) partition a 2GB or size of RAM if you want to hibernate and make the rest /home where all your data and user settings will go.
 
I will be booting through the 80 gig drive though. I want to have ubuntu and the boot info on the 2nd drive (aka 80gig). Theres nothing on the 80, it was from a old install but the install was a accident, the MBR wasnt supposed to be on the 80 when on the old PC, but for some reason it did. 
So create a 10-20 gig partition , a 2GB partition for hibernate and third partition for all my data and user settings? 
Im slow and careful cause i have lots of experience with partitions and stuff on windows, but none on ubuntu, complete noob on ubuntu.
 
That means i want to choose "Seperate partitions manually" right?
 
EDIT: just deleted everything off the 80 gig on the Seperate partitions manually page, so its completely empty now
 
There are a few more options when partitioning that you didnt mention. 
 
For 10-20 gig   and 2 gig and the left over for user data:
 
Do i want Primary or logical?
Location for partition: beginning or end?
Use as:  Multiple options, only one i recognize is FAT32...which do i use?
Mount point: what do i make the mount point of the 10-20 and the 2 gig? and the left over?

---

### Post by M3rc Nate on 2010-06-12
Cant progress any further at all until i get some help :) just so you guys know.

---

### Post by confused57 on 2010-06-12
If I were setting it up for myself I'd do:

1. 10-20 GB  Mountpoint /  primary   beginning    ext4(or ext3)
2. all but 2 GB  Mountpoint  /home   logical  beginning    ext3(or ext4)
3. 2 GB  Mountpoint  swap  logical  

I prefer to have swap at the end of the disk, I've just always done it this way.  You could probably do the 2 GB as step#2, but select end of the drive, & use the rest for /home.

You may however want to wait on oldfred's suggestions.

/  =  root partition
/home   =   home partition

---

### Post by M3rc Nate on 2010-06-13
Man this was a lot easier be4 all this partition stuff lol.

---

### Post by confused57 on 2010-06-13
> **M3rc Nate said:**
> Man this was a lot easier be4 all this partition stuff lol.

I personally wasn't even aware of what a partition was before I started using Ubuntu.  Since then, I've had over 11 distros on one computer at one time, but now usually restrict it to 2 or 3.

If you're a little uncertain about partitioning, use Herman's guide for dual boot on 2 drives that oldfred gave you in an earlier post:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Once you become familiar with Ubuntu & you're more confident with partitioning, then you might want to try reinstalling with a separate /home, etc.  Be sure to read Herman's guide carefully, especially the part about clicking on the advanced button near the end of the install to select where to install grub.

---

### Post by M3rc Nate on 2010-06-13
> **confused57 said:**
> I personally wasn't even aware of what a partition was before I started using Ubuntu. Since then, I've had over 11 distros on one computer at one time, but now usually restrict it to 2 or 3.
 
If you're a little uncertain about partitioning, use Herman's guide for dual boot on 2 drives that oldfred gave you in an earlier post:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
 
Once you become familiar with Ubuntu & you're more confident with partitioning, then you might want to try reinstalling with a separate /home, etc. Be sure to read Herman's guide carefully, especially the part about clicking on the advanced button near the end of the install to select where to install grub.
 
Sweet thanks, yeah i was planning on just doing it by the book (aka by the guide) but then someone commented on doing partitions. Which got confusing cause making partitions on ubuntu is a lot more complicated than windows. And if my system was only ubuntu then id be ok with fooling around, but i got windows on a partition (granted its a newly fresh install) but its OEM so idk if i could make the key work again. 
So thanks, tomorrow i will install ubuntu using the guide (no partitions) and if i got any Qs, ill post um here :)
 
S

---

### Post by oldfred on 2010-06-13
I thought confused57's instructions were very clear (better than mine). 

But if partitions are too confusing the default install works well. 

I did only have root & swap for my first three years. But I did have winXP and an extra shared FAT (now NTFS) partition so I could have the same data easily available in both systems. New hard drive, more experience with Ubuntu and a desire to experiment with multiple operating systems, I now have many partitions, but it takes some planning up front.

---

### Post by M3rc Nate on 2010-06-13
> **confused57 said:**
> If I were setting it up for myself I'd do:
 
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical 
 
I prefer to have swap at the end of the disk, I've just always done it this way. You could probably do the 2 GB as step#2, but select end of the drive, & use the rest for /home.
 
You may however want to wait on oldfred's suggestions.
 
/ = root partition
/home = home partition
 
 
Ok so i am at the partition part. 10-20GB mountpoint, primary, beginning ext4...ok i got that and thats good, but what what do i put in the "Mount Point" area? the part that has (/, /boot, /home, /tmp etc) ?
And same with the other 2 partitions, what do i put as their "Mount Points"? 
 
Btw for the 10-20GB, How much would you use from a 80GB drive for the OS? 10gb's for it or 20gb's?

---

### Post by oldfred on 2010-06-13
Partitions have to be primary and you only can have 4 primary. But years ago they realized that was  a problem so now one primary can be and extended that can hold virtually as many logical partitions as you want. You normally create the primaries first, if every thinking about another windows leave a primary, many new systems use all or most of the primaries.

ext3 and ext4 are formats for linux like FAT, FAT32 or NTFS are for windows. ext3 was the standard until recently and ext4 is a new standard. When ext4 first came out it had issues and many see old posts or blogs that say not to use ext4. Issue have been resolved so you can use either.

When you manually partition you set up the partitions - primary or logical inside the extended. When you then use manual install you have to tell Ubuntu which partition is / (root) and what its format will be, etc.

---

### Post by M3rc Nate on 2010-06-13
> **oldfred said:**
> Partitions have to be primary and you only can have 4 primary. But years ago they realized that was a problem so now one primary can be and extended that can hold virtually as many logical partitions as you want. You normally create the primaries first, if every thinking about another windows leave a primary, many new systems use all or most of the primaries.
 
ext3 and ext4 are formats for linux like FAT, FAT32 or NTFS are for windows. ext3 was the standard until recently and ext4 is a new standard. When ext4 first came out it had issues and many see old posts or blogs that say not to use ext4. Issue have been resolved so you can use either.
 
When you manually partition you set up the partitions - primary or logical inside the extended. When you then use manual install you have to tell Ubuntu which partition is / (root) and what its format will be, etc.
 
 
Ok that all makes sense. The only thing i need help with now is :
 
for the first parition (10-20gig) what do i put in the "Mount Point" area? the part that has (/, /boot, /home, /tmp etc) ?
And same with the other 2 partitions, what do i put as their "Mount Points"? 
 
Btw for the 10-20GB, How much would you use from a 80GB drive for the OS? 10gb's for it or 20gb's?
 
 
For example, i am at the create a partition window, and i have so far
Primary choosen, 15,000MB size, Beginning chosen, Ext4 choosen, but idk what to choose as mount point.  Same for the other 2 paritions, what will their mount points be?

---

### Post by oldfred on 2010-06-13
mount point for root is /. You also choose /home. All the other available mount points are if you have a server or other very advanced system and need those separate. Desktop users only need root, swap & optionally  /home.

---

### Post by M3rc Nate on 2010-06-13
> **oldfred said:**
> mount point for root is /. You also choose /home. All the other available mount points are if you have a server or other very advanced system and need those separate. Desktop users only need root, swap & optionally /home.
 
 
 
 
So for 10-20gb i choose "Primary, 15gb, beginning, ext4, and "/"
 
For 2gb i choose logical, 2gb, swap
 
The rest (63gb), logical, ext4, /home
 
That look correct?

---

### Post by oldfred on 2010-06-13
I found whatever I choose as partition sizes and setup a few months later I wished I had more somewhere. Foruneately I buy a new hard drive every 3 or so years so I do end up with room to grow.

I had partitions set up and put my Lucid iso on a USB flash drive. It took all of 9 minutes to install. It took longer to download all the updates.:p

---

### Post by M3rc Nate on 2010-06-13
> **oldfred said:**
> I found whatever I choose as partition sizes and setup a few months later I wished I had more somewhere. Foruneately I buy a new hard drive every 3 or so years so I do end up with room to grow.
 
I had partitions set up and put my Lucid iso on a USB flash drive. It took all of 9 minutes to install. It took longer to download all the updates.:p
 
 
Haha well, im sure your a full time linux user, i plan to use linux, get familar, have fun, but i will be using windows 90% of the time. But my question regarding my partitions wasnt really about size, i was making sure those parameters i choose were correct. Do i have them setup right? the mount points and the type of partitions and everything? They are the correct choices? Just double checking

---

### Post by oldfred on 2010-06-13
Those should be fine.

---

### Post by M3rc Nate on 2010-06-13
> **oldfred said:**
> Those should be fine.
 
 
Its installing, i made sure i put the boot loader on sbd :) So now once done i restart computer, and in bios put my 80 gig (ubuntu) as my first boot drive, and il get to choose between windows and ubuntu at startup?
 
UPDATE: It is installed, i restarted, and booted into windows. One weird thing, and this has always been this way since i hooked up the 80gig. It isnt seen in my bios as a "boot from" hard drive....why do you think that? All i see when i open up my boot priority is my 640, my CD drive, "removable" and "disabled"....
 
In my bios under "Main" tab, where it shows everything SATA related, it shows my 640 is in SATA 1 and my 80 is in SATA 2...
 
UPDATE2: Nvm, i went under Boot device priority and found "Hard disk drives" and its listed under there...lol
 
OH YEAH BABY! lol, booted with 80 gig and window popped up showing options for my boots (win 7, ubuntu)   SWEET..just booted into ubuntu

---

### Post by M3rc Nate on 2010-06-13
Thanks guys, consider this thread solved if the question was how do you dual boot a PC with 2 hard drives and you want some partitions lol. :)

---

### Post by oldfred on 2010-06-13
Glad you got it working.

---

### Post by M3rc Nate on 2010-06-14
> **oldfred said:**
> Glad you got it working.

So just a quick question... is there anything to be cautious of that can mess with my GRUB? Like when a Ubuntu update comes out or a new version or w/e..or should everything be dandy?

---

### Post by oldfred on 2010-06-14
Updates should not change anything although with Karmic and removeable drives some had an update install to the wrong drive, supposedly fixed in Lucid. New installs are of course a different animal.

I copied this comment from someone:

Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

