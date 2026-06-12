---
title: "Installing Ubuntu Side by Side with Windows XP"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by touches on 2012-01-21
hello Ubuntu Forums

I decided to install Ubuntu 11.10 as a dual boot option alongside my existing Windows XP OS. Now since i am new to partitions and dual booting i have certain doubts which halts my Ubuntu installation. I have 4 drives in my windows XP:c,d,e and f

Windows XP is installed on e drive ,its total size is 39 GB and free space is 16.9 GB. Now when i booted the live Ubuntu cd for installation and checked the install side by side option i was presented with the partition option of 50gb for windows and another 48 GB for Ubuntu

my doubt is from where does Ubuntu take up the 48 GB since it by default tries to create a partition in the windows drive? is it from the other drives?? And if i want proceed with the installation as per the Ubuntu partitioning option will any of my windows data get erased??

I have an F drive where i have 80 GB of free space. can i install Ubuntu in that drive without formatting the drive in windows as i have data which i don't want to lose

Please any guidance in installing side by side with windows xp would be very grateful

---

### Post by darkod on 2012-01-21
The first thing when starting to use both windows and linux, is to forget the windows definition of "drive". The way windows uses it, it has two meanings and can create confusions.
If you only look in My Computer, you can't tell a difference between a partition and a disk. That's why it's better to look in Disk Management and give precise informations how many disks you have and their size, and the sizes of all the partitions on the disks.

If you already have the ubuntu cd, boot with it in live mode (Try Ubuntu option) and in terminal execute:
sudo fdisk -l (small L)

Post the results here and it will show all your partitions. If you can, also tell us on which partition is XP.

---

### Post by touches on 2012-01-22
@darkod

I am posting the sudo fdisk -l results. I don't understand the results though, and as for my windows i have a single disk of size 490 GB and it has 4 partitions C,D,E and F and in the 3rd partition i have my windows XP installed.

So now how do i proceed with Ubuntu installation and also help me in understanding the fdisk results please.

---

### Post by nipunshakya on 2012-01-22
Hi. First off all, warm welcome to the forum.
> **touches said:**
> hello Ubuntu Forums

I decided to install Ubuntu 11.10 as a dual boot option alongside my existing Windows XP OS. Now since i am new to partitions and dual booting i have certain doubts which halts my Ubuntu installation. I have 4 drives in my windows XP:c,d,e and f
are they all primary partitions?

> **touches said:**
> Windows XP is installed on e drive ,its total size is 39 GB and free space is 16.9 GB. Now when i booted the live Ubuntu cd for installation and checked the install side by side option i was presented with the partition option of 50gb for windows and another 48 GB for Ubuntu
Its best if you choose the label "something else" instead of "side by side" option. That way, you will be able to manually make partitions according to your wish. 

> **touches said:**
> my doubt is from where does Ubuntu take up the 48 GB since it by default tries to create a partition in the windows drive? is it from the other drives?? And if i want proceed with the installation as per the Ubuntu partitioning option will any of my windows data get erased?? Ubuntu will make partitions of its own if you go with side by side installation feature, and though i haven't tried that yet, i assume that ubuntu will pretty much mess your partitions of windows xp too. So i don't advice you going that way.

> **touches said:**
> I have an F drive where i have 80 GB of free space. can i install Ubuntu in that drive without formatting the drive in windows as i have data which i don't want to lose
Please any guidance in installing side by side with windows xp would be very grateful

**You selected right drive for installation as its free space so needs just a format as 'logical'** **ext2 or ext3 or ext4(as you want) and you are ready to go.**

1. The golden rule before partitioning is: back up all your data from other drives (in case if you format wrong partition, u might regret not to have a backup of them)that u need, all your pics, videos and personal stuffs. Then,
2. Boot to LiveCD.
3. When asked for installation method, select "**something else**".This will let you make partition as u want.
4. Format F drive, just make sure you select the right partition coz the partition manager will show you stuffs like /dev/sda and all....be careful here to recognise and format the f: correctly. and then format it as logical drive as ext2 or ext3 or ext4(any one ofcourse) as u want.
5. select the logical drive u just formatted and then make three partitions under it(thats the benefit of having a extended logical partition as it acts as a container of many other logical partitions to be created under it).Allocate space to them as:
a. an ext2 or ext3 or ext4 as / (around 20 gb) where your linux installs.
b. an ext2 or ext3 or ext4 as /home (around 57 gb) to store your files for linux.
c. a swap-area(around 3 gb) for letting your computer hibernate and suspend.

more help about dual boot is here:
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Goodluck.Feel free to ask any thing.
Regards,WinuxUser

---

### Post by touches on 2012-01-22
Thanks WinuxUser for the detailed steps and the warm welcome

> [SIZE=2]Hi. First off all, warm welcome to the forum.[/SIZE]
     Quote:
                                                                      [FONT=Arial][SIZE=2]Originally Posted by **touches**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11629648#post11629648")[/SIZE][/FONT]                 
                 [I][FONT=Arial][SIZE=2]hello Ubuntu Forums

I decided to install Ubuntu 11.10 as a dual boot option alongside my  existing Windows XP OS. Now since i am new to partitions and dual  booting i have certain doubts which halts my Ubuntu installation. I have  4 drives in my windows XP:c,d,e and f[/SIZE][/FONT] [/I]
                      
          
[SIZE=2]are they all primary partitions?[/SIZE]I have a single primary partition that is my C drive and 3 logical partitions.

Now for the F drive that has 80 GB of free space. If i have to install Ubuntu in that drive do i have to backup my windows data first? As i don't have the resources to backup 80 GB of data, is it possible to create a separate partition of 80 GB and installing Ubuntu in that. Is it possible to create such a partition in Ubuntu?

And how do i recognize the correct drive as per Ubuntu's parlance. I am purely confused with /dev/sda1's and so on and i don't want to mess up the wrong drive.

---

### Post by Quackers on 2012-01-22
Your hard drive currently appears to be filled with partitions. Even though some of those partitions may have unused space within them this is not space that Ubuntu can install into.
Ubuntu needs its own partition.
To install Ubuntu I would suggest that you shrink one of your logical partitions using Windows tools. How much you can shrink that partition by is largely up to Windows.
This will give you some free space on the disc in which you can then create a swap partition and an Ubuntu root partition, so that Ubuntu can install there.
Alternatively, once the new free space is created you can use the "side by side" option in the installer - making sure that the correct space is used.

---

### Post by nipunshakya on 2012-01-22
> **touches said:**
> 
I have a single primary partition that is my C drive and 3 logical partitions.

Well then thats it...you are ready to go buddy.

> **touches said:**
> 
Now for the F drive that has 80 GB of free space. If i have to install Ubuntu in that drive do i have to backup my windows data first? As i don't have the resources to backup 80 GB of data, is it possible to create a separate partition of 80 GB and installing Ubuntu in that. Is it possible to create such a partition in Ubuntu?

And how do i recognize the correct drive as per Ubuntu's parlance. I am purely confused with /dev/sda1's and so on and i don't want to mess up the wrong drive.

If you don't have resources to backup your data, well,u must well recognise your partitions in the ubuntu partition manager.
Yes it is possible to create single partition. However, the partition rule is that you cannot have more than 4 primary partitions.
It is possible for ubuntu's partition manager to create a partition for you.Just make sure you select the right one, i shall show u my partition scheme(see figure) and i'll explain. Hope u grab something out of it mate.
Total size of my HDD is 320gib and is its partition is described as:
1.dev/sda1 is my ntfs which is my primary where windows is.
2.dev/sda2 is the container called extended partition where the sub logical partitions reside like below:
     -dev/sda5 is / i.e. your linux installs here
     -dev/sda6 is /home where the music and all personal stuffs get into.
     -dev/sda7 is linux-swap
3,dev/sda3 is ntfs which is primary for data sharing between ubuntu and windows
4.dev/sda4 is also ntfs which is also primary for data between ubuntu and windows

Now go to my attached file. Ill explain what each column means.
As you see in picture, partition means the way my spaces are allocated in the harddisk.
the filesystem means the type of partition under which u formatted that space(ntfs,extended,ext4,ext4,linux-swap,ntfs,ntfs resp.)
The mount point means what linux is using that partition for. i.e. / for linux installation and /home for data
Label means what your partition is labeled(back in windows, i have labeled my last two ntfs partitions as Repository and Whatever, and hence the name.) But linux partitions(ext2/ext3/ext4 doesn't have labels)
Size is what u can understand well

Now, i suggest you boot to liveCD. Run gparted, and see your partition scheme first. Then u can compare your partition with mine and then see what u can make out of your partiton. U can post a picture of it here so i can help you out with your partitioning scheme too. 
Rest, refer to my previous reply.

Going with this step might be a bit scary to u at first, but trust me, u won't regret your partitions in future.Even i messed up myself for few times, and what i have now is what i enjoy the most.:P


Goodluck and happy linuxing:D
Regards,WinuxUser

---

### Post by touches on 2012-01-22
@WinuxUser

Thanks a lot mate for your patience and clear explanation .

I am posting my screen-shot from gparted taken from the Live CD.

In the pic i have my windows installed in dev/sda6 and dev/sda7 is my F drive.
Now how do i proceed with the partitioning scheme.

And thanks a lot again WinuxUser for your patience and guidance.

---

### Post by nipunshakya on 2012-01-22
okay mate...wait few minutes...i shall tell u my reviews...

---

### Post by nipunshakya on 2012-01-22
first tell me one thing ...isn't sda1 the place where your windows is currently installed?? 
I strongly say it because you cannot install windows in extended partition and windows always needs to assume it as its installed in primary partition. So lets make clear of this thing first...check it once....
Make this thing sure by booting to your windows and running Disk Management tool,compare the sizes of your partition by what your gparted tells,to that of what your Disk Management Utility tells you...see the size of your windows installation in both places and confirm it first...

---

### Post by nipunshakya on 2012-01-22
Now, be at your windows only. If you wish to install ubuntu in sda7, first off all move all your data from sda7 to sda5(it has enough room there)and make sda7 empty. Next, I would suggest you run Disk Management  again and then format the partition you just emptied now, and make it ntfs for time being.
[B]make sure u restart your pc to windows once again after you format the empty partition so that windows adapts nicely to your fresh empty partition.
[/B]next reboot again to livecd this time, and then this time u go for the installation as suggested above.Make sure to choose "something else" when u are asked how u would like to install ubuntu. Then at the partition manager, select the empty ntfs partition, and make 3 partitions out of it [ / (20gib is enough), /home(~126.35 i guess) and swap-area( 3gib is enough)]. Format all the / and /home as ext2 or ext3 or ext4..

Goodluck.
Regards,WinuxUser

---

### Post by darkod on 2012-01-22
You can also boot win7, open Disk Management and shrink sda7 for as much as you want to allocate to ubuntu. Restart win7 few times. Leave the space created by the shrink as unallocated.

Then start the ubuntu install and simply use the unallocated space to install into it.

---

### Post by touches on 2012-02-05
Sorry for the long time away..
I managed to install Ubuntu without a glitch alongside my Windows XP installation Now i have a dual boot OS. A friend of mine good at Linux stuff helped me out. Well i used GParted to create a new partition from my F drive which had a total of about 150GB with 60 GB free space and through GParted i created a new partition for about 28GB and installed Ubuntu in that partition, everything works fine now. I thank the forums guys for all the help and the detailed instructions provided.

Cheers

---

### Post by nipunshakya on 2012-02-05
Well, even though it took a week to figure it out, glad to know your machine is booting linux. With time, you will learn to adjust ubuntu according to your needs...till then, enjoy your ubuntu.

Cheers.
Happy Linuxing

---

### Post by bogan on 2012-02-05
Hi! **Touche**s,

If you have taken **WinuxUser**'s advice of two weeks ago, I am afraid this info may be too late, unless you have backed up everything; as he assumed the unused 'Free Space' in f: was 'really' Free Space, unallocated on the drive.

But then, if you had, I think you would have posted something before now.

You asked help to understand the fsusk -l info, so here is what I make of it:

[Round figures so they do not add up exactly].
> 
Partition     Sectors Bytes ..    Windows ...............                      Type
sda1..........                     30 = 150GB.....              c: ?? ...................                                             NTFS Primary Partition
sda2..........                     69 = 345GB.....             ?: ??....................                                            W95  Extended Partition
                       ...........total 99 = 495GB

sda5..........                    29 = 145GB.......               d: ??.........................                          NTFS Logical }
sda6............                      8 = . 40GB.......                   e: WinXP..................                                   NTFS Logical } Within sda2
sda7..........                     31 = 155GB.......               f: Data 80GB Free...       NTFS Logical }
 ....sub-total 68 = 340GBMy advice would be to use Windows to shrink the f: drive, sda7, after de-fragmenting it twice, to about 130GB, to give 20GB for Linux and 4GB as a swap file, and put the Home partition elsewhere, if you need it to be large.

The rest of **WinuxUser**'s advice would then apply. The other alternative depends on what the other partitions are used for and how much unused space there is, that could be used to take the data from f:

Best of luck,
**Edit:** I had not checked the Thread since starting this Post, so it is all a bit belated, but I am glad to see it all worked out well, & that my advice tallied with that given by **darkod**.
Chao!, **bogan**

---

### Post by touches on 2012-02-06
@WinuxUser
Thanks mate i hope i get to learn lots in Ubuntu just like you guys do...

@bogan
Your info is much appreciated. I tried De-fragmenting in Windows XP but it showed up as 'no need to De-fragment volume F:' and there was not much difference either. So i used Gparted from the Live CD and shrunk the F: partition to about 125GB and installed Ubuntu in the new partition. I'll post my screenshot of how the partitions are after the Ubuntu installation

---

### Post by n3oom on 2012-02-06
Help meeeeeeeeeee
I Changed the bootscreen for windows 7 using a software called bootscreen updater, so everthing goes ok then I restart my lap 2 see if the bootscreen really changed so I got 

_**[COLOR="Red"]bootmgr image is corrupt the system cannot boot [/COLOR]**_






Is there any way to fix that from ubuntu ???


Note : I don´t have windows 7 DVD, I know how to fix it using a flash usb but I don´t have it now .. i really need to work tonight with windows 7 .. so help me guys plz

---

### Post by nipunshakya on 2012-02-07
@touches: learning ubuntu requires time and alot of experimenting in your machine too....get along with terminal, learn its commands and then someday, u will go fine with ubuntu.... even im doing the same.. :D

Happy Linuxing

---

### Post by nipunshakya on 2012-02-07
> **n3oom said:**
> Help meeeeeeeeeee
I Changed the bootscreen for windows 7 using a software called bootscreen updater, so everthing goes ok then I restart my lap 2 see if the bootscreen really changed so I got 

_**[COLOR=Red]bootmgr image is corrupt the system cannot boot [/COLOR]**_






Is there any way to fix that from ubuntu ???


Note : I don´t have windows 7 DVD, I know how to fix it using a flash usb but I don´t have it now .. i really need to work tonight with windows 7 .. so help me guys plz

Run boot info script and post your output here......
Read the following:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It would have been nice of you had started a new thread...

Regards,WinuxUser

---

### Post by bogan on 2012-02-07
Hi! **touches,**

You Posted:> I'll post my screenshot of how the partitions are after the Ubuntu installationIt would be interesting if you also post what Windows Disk Management shows for the size and types of your partitions.

 What is a bit puzzling is the 150GB Primary partition, sda1, which I called C: ?? because Windows - as far as I know - needs a Primary partition to boot from, and can not do so from a logical partition like the 40GB sda5, which you identified as e: and Windows XP.

So what is that 150GB partition from your point of view?

Then there is the mystery of the missing sda3 & sda4, presumably hidden system or recovery partitions. 

Edit: I had not seen your GeParted Thumbnail when I Posted the above, which confirms what I thought and tried to describe.

Chao!, **bogan**.

---

### Post by vkadal on 2012-02-07
[QUOTE=touches;11629648]hello Ubuntu Forums

I decided to install Ubuntu 11.10 as a dual boot option alongside my existing Windows XP OS. Now since i am new to partitions and dual booting i have certain doubts which halts my Ubuntu installation. I have 4 drives in my windows XP:c,d,e and f

The simple solution is to install Ubuntu 11.01 without bothering much about disk space and other issues. You can choose all default options provided by Ubuntu 11.01. All you old data of XP will be safe and you can access them from Ubuntu also. Enjoy Ubuntu without asking to many questions! Ubuntu will take care of you.

---

### Post by bogan on 2012-02-07
[COLOR=Red]**Warning!**[/COLOR]

**vkadal **Posted: > The simple solution is to install Ubuntu 11.01 without bothering much about disk space and other issues. You can choose all default options provided by Ubuntu 11.01. All you old data of XP will be safe and you can access them from Ubuntu also.[ Presumably he meant 11.10.]

Unless you are installing to a clean, empty HDD, do not care what happens to any existing installation - Windows or whatever - have a standard set-up with lots of unallocated HDD disk space, or a large Windows partition with plenty of free space and fewer than four partitions, or are installing to an external drive **AND **have backed up **ALL** your valued data; then taking his advice could be highly dangerous.

The set-up described  by **touches** was far from standard, and he was wise to seek knowledge and advice.

 These Forums should be a source of safe and considered opinions and answers.

There are several Tutorials to be found in these Forums or elsewhere that give clear and helpful advice together with step by step instructions aimed at beginners.

**bogan**.

---

### Post by Mark Phelps on 2012-02-07
> **n3oom said:**
> ... I Changed the bootscreen for windows 7 using ... Is there any way to fix that from ubuntu ???

Since ALL this time has passed, with NO response, I hope you have learned that hijacking someone else's thread with an entirely DIFFERENT issue does not work well.

But basically, the answer to your question is -- NO.

If you had taken your question to the proper place -- Windows 7 forum (sevenforums.com) -- folks there might have been able to tell you how to fix your bootscreen problem from the command line.

---

### Post by touches on 2012-02-08
@bogan
Hi i am posting my windows and Ubuntu screen shots after installing Ubuntu and the partitions before installing Ubuntu

@vkdal

At first i was of the opinion that installing side by side option is quite safe with Ubuntu but  i read in some forums that its behavior can be unpredictable and it may mess up the windows installation, so i thought it best to seek knowledge from forums who have experience in partitions and installation, for the other stuff Ubuntu is great and i would leave it to its discretion to handle things!

Cheers

---

### Post by bogan on 2012-02-09
Hi!, **touches**,

You Posted:>  I am posting my windows and Ubuntu screen shots after installing Ubuntu and the partitions before installing UbuntuThanks for the Post with the Thumbnails. Looks like you are all set to blast off.

Interesting that GParted sees sda1, c: as the boot partition, whilst Windows insists it is sd6, e:

Chao!, **bogan**.

---

### Post by nipunshakya on 2012-02-09
> **touches said:**
> Hi i am posting my windows and Ubuntu screen shots after installing Ubuntu and the partitions before installing Ubuntu

Hi touches, first off all, good to see you post back. Glad to know that you made it with ubuntu. However, i have some reviews regarding your current partition scheme:

1. You don't need that extra linux-swap area. You are wasting extra space on it. Two partitions for linux-swap is much more than dedicated. Just one partition for swap is enough.
2. You can always create total 4 primary partitions. So you could have created 3 primary NTFS partitions(for windows and data sharing between windows 7 and linux) and one extended partition(for linux only and create logical partitions within it) so that linux would be separately inhabited in your HDD.

From your partitions, it is clear that you have made it, but, i'd suggest you make a /home partition out of the linux-swap area. The key icon on your partition means the filesystem is active and actions can't be taken to it. But your sda8 can be adjusted to /home 

Still, with your overall effort, im happy that you made it through.

Happy Linuxing
Regards,WinuxUser:D

---

### Post by nipunshakya on 2012-02-09
> **bogan said:**
> 
Interesting that GParted sees sda1, c: as the boot partition, whilst Windows insists it is sd6, e:

Mate, boot partition is just another partition containing windows operating system file. It doesn't have any boot files inside it. 
gparted sees the right thing and disk management does the right thing too...sees c: (in disk management) or the /sda1 (in gparted) as the system partition where the actual bootmgr for windows is located.
Might be due to some MotherBoard BIOS settings, it got to two different places, and bitlocker might be another reason too...He might have an older version of windows on his machine, and then installed windows 7 later on, (i assume) which caused newer Windows version to typically use a separate system partition.

---

### Post by bogan on 2012-02-10
Hi!,[B] WinuxUser,
[/B]
Thanks for the clarification; I had, without actual knowledge, come to the conclusion that what you describe must be the case.

But it is still very confusing for the non-expert.

Chao!,** bogan**.

---

### Post by nipunshakya on 2012-02-10
okie....lets wait for someone more expert then to clarify us both,..... :D

---

### Post by touches on 2012-02-10
@WinuxUser and Bogan
Guys first of all i dont have Windows 7!! i have Windows XP installed, if thats of any use to the Windows and GParted naming conventions, i may have mentioned about it in my previous posts or i may have missed it.

@WinuxUser 
Mate you must be really good if you can draw inferences from the partition scheme, i hardly got it and i was just happy that i managed to install Ubuntu, never thought about the extra space. I would like to do what you have said. So does that mean that for /home partition to have 4GB should i reinstall Ubuntu or do i have to do any such changes.

---

### Post by nipunshakya on 2012-02-10
@touches:
The following link will best answer your question of getting a separate /home without re-installation. 
Personally, i haven't tried to do this. But i think, in your case, what you first need to do is format /sda10. To do that, boot from livecd(select 'try ubuntu'), run gparted there, swap-off the /sda10 to make it inactive) and then go along with the tutorial.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Try it if you want....coz since u are new to ubuntu, u can always learn a new thing. :D

---

### Post by nipunshakya on 2012-02-10
> **touches said:**
> Guys first of all i dont have Windows 7!! i have Windows XP installed,

Hmm...so i guess my previous assumption was right.... neglecting the part where i mentioned he installed another version of windows later on...hehehe
> He might have an older version of windows on his machine, and then  installed windows 7 later on, (i assume) which caused newer Windows  version to typically use a separate system partition.

---

