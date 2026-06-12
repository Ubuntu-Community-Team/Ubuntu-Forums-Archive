---
title: "Linux does not find partition"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by Flame_Phoenix on 2010-10-31
To be honest, I am trying to install Linux Mint, but since this is based on Ubuntu, and I am comfortable with Ubuntu on my VM I decided to label it Ubuntu.

I have a 235 HDD and it is partitioned like this:
C: 150 GB (Windows)                       NTFS
D: 70 GB (Data)                           NTFS
G: 15 GB (for my not yet installed Linux) NTFS

I also followed this tutorial and now I have some sort of LiveCD inside my USB:
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

So, now I have a pen drive with an Ubuntu LiveCD and a 15GB ready for my Ubuntu! Should be easy right? WRONG!

This is what I do:
1 - connect pen to computer
2 - turn on computer
3 - pen start running and I load Linux like a LiveCD (yey!)
4 - Linux loads and I wait
5 - I click "Install linux"
6 - I configure the language, time zone and keyboard with no problems
7 - Disk partitioning ... it offers me 2 choices:
    7.1 - Erase entire disk and install Ubuntu (Hell no!)
    7.2 - Manually partitioning: but drive C:, D: and G: do not appear!!!

I want to install my Linux on driver G:, but I don't find a "Install Linux in this specific partition" option! 

I did a search on Google and I found someone with the same problem I have:
[http://www.linuxquestions.org/questions/linux-newbie-8/installing-ubuntu-on-existing-linux-partitions-partition-magic-439376/](http://www.linuxquestions.org/questions/linux-newbie-8/installing-ubuntu-on-existing-linux-partitions-partition-magic-439376/)

But this is the first time I install Linux and I don't understand that thread! It's like everyone is talking Chinese! 

I also used the search function of this forum and I found nothing :S

Can someone please help me? I am really lost around here and I would really like to have my Ubuntu installed on that G: partition!

---

### Post by jrev on 2010-10-31
Hi,
The problem is : do you want to keep your Windows system and add Ubuntu to your hard disk ?
Do you want to replace Windows by Ubuntu ?
in any case, there is no partition c or D or E in linux
If you start on a live-CD (which can be the install CD) you can have a look at your hard disk and format it in order to install Ubuntu.
This is the first thing to do so that you will know if your PC is Ubuntu compatible.
On a live-session you should be able to go on the net and have a good graphic screen.
The difficult thing when you start Linux is to forget about Windows and its bad manners.
If you want to know the name of your partitions on Ubuntu you have to type :
sudo fdisk-l in the console of the live-CD  or use  the graphic application "gparted"
from the same live-CD.
your C partition is /dev/sda1
your d partition is /dev/sda2 ans so on sda is your first HD sdb the second HD and so on

---

### Post by Flame_Phoenix on 2010-10-31
> The problem is : do you want to keep your Windows system and add Ubuntu to your hard disk ?
Yes! I want to make some sort of dual boot. I want to have both windows and Linux, and I want to choose between them when I boot my computer.

I know this is possible but I just make no idea on how to do it. Did I do something wrong?

Btw, I want a real Ubuntu installation, so I don't want to use Wuby :P

---

### Post by DualCore555 on 2010-10-31
Hey guys, I jave the same problem. I wanted to install my Ubuntu 10.10 on the new partioned drive (first one has the Windows 7), but the problem is, that when the partitioner starts during the installation, i cant see any drives. Everything is Unallocated, and the GParted says the same. Whats wrong? can please anyone help me? I can give you also the the output of sudo fdisk -ul. Please, help.

```
ubuntu@ubuntu:~$ sudo fdisk -ul

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b159386

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   312578047   156185600    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1267663b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

---

### Post by Flame_Phoenix on 2010-10-31
I may be wrong ... but isn't the topic of this thread a problem about LINUX? Linux is causing the problem by not reading the partitions correctly. 

Windows doesn't give me half the problems Linux does. Just saying.

Is it because our partitions are NTFS? Still, I am sure Linux can detect NTFS, he just can't write in NTFS format right?

---

### Post by jrev on 2010-10-31
Now we know what you want to do OK
1) Start the Windows defragmenter ***more than once*** in order to bring the data at the beginning of the Hard disk
2) reduce the Windows available space on the HD (maximum half the original size)via "gparted" on the live-CD
3) prepare the Hard disk partition by typing > sudo fdisk -l with the Live-CD (that can be the Ubuntu install CD)
4) make one partition linux (/) one partition /home and one for swap with ext4 file system
5) Read the detailed installation description 
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Fresh_Installation](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Fresh_Installation)


Come back if you have more questions !


:P  :P

---

### Post by jrev on 2010-10-31
> **Flame_Phoenix said:**
> I may be wrong ... but isn't the topic of this thread a problem about LINUX? Linux is causing the problem by not reading the partitions correctly. 

Windows doesn't give me half the problems Linux does. Just saying.

Is it because our partitions are NTFS? Still, I am sure Linux can detect NTFS, he just can't write in NTFS format right?

Linux is different from Windows. It's simpler if you start with Linux but the main problem in life is always : <How to get rid of our (bad) habits ?

---

### Post by Flame_Phoenix on 2010-10-31
> Now we know what you want to do OK
1) Start the Windows defragmenter more than once in order to bring the data at the beginning of the Hard disk
2) reduce the Windows available space on the HD (maximum half the original size)via "gparted" on the live-CD
3) prepare the Hard disk partition by typing
Quote:
sudo fdisk -l
with the Live-CD (that can be the Ubuntu install CD)
4) make one partition linux (/) one partition /home and one for swap with ext4 file system
5) Read the detailed installation description
[http://ubuntuguide.org/wiki/Ubuntu:M...h_Installation](http://ubuntuguide.org/wiki/Ubuntu:M...h_Installation)

1 - I used defrag on partition C: and D: before shrinking C: and creating partition G:. So this step would be useless now.
2 - I used the computer management tool (that comes with windows) to create the new partition G:. I also have a CD with GParted, but I didn't need to use it.
3 - I don't understand this step. Am I supposed to do this after starting the LiveCD ?
4 - Ok, I am now totally host here, I am not following.

I don't get it. Are you saying that now I have to merge partition G: with C: and then use GParted to split them again? What's the point?

---

### Post by DualCore555 on 2010-10-31
The problem is, that NOW i have ONE partition with Windows 7 installed. And I want to have also Linux Ubuntu 10.10 on the second partition, wich i want to create during the Ubuntu installation. BUT when the partitioner starts, it doesnt see my windows partition at all. It says, that my disk is empty and unallocated, but in fact it isnt. I dont want to lose my data on the windows partition, thats why im asking you guys, if anyone had or has the same problem and we could find a solution. 
When i start the GParted, it says the same as the partitioner during the installation.

---

### Post by jrev on 2010-10-31
> **flame_phoenix said:**
> 
3 - i don't understand this step. Am i supposed to do this after starting the livecd ?
[size="5"]yes[/size]


:p

---

### Post by Flame_Phoenix on 2010-10-31
> BUT when the partitioner starts, it doesnt see my windows partition at all. It says, that my disk is empty and unallocated, but in fact it isnt. 

I have this exact same problem. Don't know why, nothing seems to work :S

Wait a second:
> 
sudo fdisk -l 
Is this command supposed to magically find my C: partition, D: partition and G: partition so then I can choose the G: partition to install Linux?

---

### Post by DualCore555 on 2010-10-31
> **Flame_Phoenix said:**
> I have this exact same problem. Don't know why, nothing seems to work :S

Wait a second:

Is this command supposed to magically find my C: partition, D: partition and G: partition so then I can choose the G: partition to install Linux?
 No it isnt. It will just show you the partitions. But try, and the output post here please.

---

### Post by jrev on 2010-10-31
> **Flame_Phoenix said:**
> I have this exact same problem. Don't know why, nothing seems to work :S

Wait a second:

Is this command supposed to magically find my C: partition, D: partition and G: partition so then I can choose the G: partition to install Linux?
**report to my previous post **explaining the Ubuntu names of the partitions.
 
Before you start the installation of Ubuntu you start the live-CD then once on the Desktop you go :
menu **Applications/Accessories/Terminal **
In the console you type :> sudo fdisk -l in order to see the arrangement of you HD as Ubuntu sees it.
You should now see your Windows partitions (you can see it on Dual Core post #4 !)

---

### Post by Flame_Phoenix on 2010-10-31
After using "sudo fdisk -l" I see:

> 
124 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      419273      451359   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(419272, 58, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(451358, 103, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       56305      157201   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(56304, 96, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(157200, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      243180      492820   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(243179, 38, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(492819, 2, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      139665      140748     4161540    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(139664, 80, 33)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(140747, 31, 46)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



---

### Post by jrev on 2010-10-31
You typed the fdisk-l on the second Hard disk 
Your windows partitions are on the first Hard disk. So you probably have 2  hard disks 

I am using as Live-CD a Linux-Slitaz CD, a very light system that loads quicker than the Ubuntu install CD in order to checjk all PC's young or older. from this CD you can use "gparted 0.4.6" or the command line to type your "fdisk -l"  

Here is my hard disk as Ubuntu sees it :
[http://www.zimagez.com/zimage/capture-jeanjean0.php](http://www.zimagez.com/zimage/capture-jeanjean0.php)
You can see I have only one Hard disk = /dev/sda and 3 partitions with only one OS 
Windows is not there !

---

### Post by shultzjr on 2010-10-31
make sure you have the latest stable version of gparted, some older versions played h#ll with ntfs parts due to linux kernel timing problems.

c.

---

### Post by Flame_Phoenix on 2010-10-31
Ok, Here is the correct disk:

> 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x760b5e6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19294   154874880    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           19294       21253    15728640    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           21253       30402    73490432    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           19295       21253    15727616    7  HPFS/NTFS



---

### Post by jrev on 2010-10-31
> **Flame_Phoenix said:**
> Ok, Here is the correct disk:

So you can start the Ubuntu automatic installation using the whole second disk...
This would be easier and quicker for you !:P

---

### Post by Flame_Phoenix on 2010-10-31
My "second" disk is actually my pen. I do not want to install Linux there, for obvious reasons lol ...

Is there a way to fix the problem on my REAL disk ? :P

---

### Post by oldfred on 2010-10-31
Partition sda1 is the 100MB boot/recovery partition for windows that is usually hidden by windows. Partition sda2 is probably your main windows install. You then have the extended partition which is just a container for the logical partitions, sda5 & sda6. 

Windows will not create or see linux partitions. You use windows tools to edit windows partitions, but use gparted or command line tools in linux to edit linux partitions. If you have no data in the NTFS partitions you created, then in gparted from the liveCD, delete sda5 & sda6. You can then install Ubuntu into the free space or create partitions for the install (my preferred way). 

If you want to create partitions and for whatever amount of space you want for Ubuntu:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

If you want to hibernate you need swap the same size as your RAM memory, otherwise if you have 2GB or more of RAM, 2GB of swap is enough for almost everything as it will almost never be used.

If you want to install in the free space, Maverick seems to have changed some things:
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
Examples with screenshots of installs:
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by jrev on 2010-10-31
> **Flame_Phoenix said:**
> My "second" disk is actually my pen. I do not want to install Linux there, for obvious reasons lol ...

Is there a way to fix the problem on my REAL disk ? :P

Yes refer to my post #2

---

### Post by jrev on 2010-10-31
Thanks oldfred for these informations :P

---

### Post by DualCore555 on 2010-10-31
> **oldfred said:**
> Partition sda1 is the 100MB boot/recovery partition for windows that is usually hidden by windows. Partition sda2 is probably your main windows install. You then have the extended partition which is just a container for the logical partitions, sda5 & sda6. 

Windows will not create or see linux partitions. You use windows tools to edit windows partitions, but use gparted or command line tools in linux to edit linux partitions. If you have no data in the NTFS partitions you created, then in gparted from the liveCD, delete sda5 & sda6. You can then install Ubuntu into the free space or create partitions for the install (my preferred way). 

If you want to create partitions and for whatever amount of space you want for Ubuntu:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

If you want to hibernate you need swap the same size as your RAM memory, otherwise if you have 2GB or more of RAM, 2GB of swap is enough for almost everything as it will almost never be used.

If you want to install in the free space, Maverick seems to have changed some things:
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
Examples with screenshots of installs:
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)


This is exactly the thing, that i know. BUT my problem is, that i CANNOT choose "install alongside other operating systems". Ubuntu just says, that i dont have any system installed, which i actually have. GParted says the same. So, i cannot make the linux partition on my windows partition, without data lose. the only one thing i can do, is install the ubuntu on the whole disk. which i dont want to.

---

### Post by oldfred on 2010-10-31
DualCore555 You need to start your own thread as your issue is different and the same solutions for the OP will not work for you.

See this:

[http://ubuntuforums.org/showthread.php?t=1606596](http://ubuntuforums.org/showthread.php?t=1606596)

Remove old gpt info/convert :
[http://ubuntuforums.org/showthread.php?t=1560383](http://ubuntuforums.org/showthread.php?t=1560383)

---

### Post by Flame_Phoenix on 2010-11-01
Apart from the fact that Linux Mint does not have GParted (nor does any KDE system afaik, they use instead the KPartitioner) I still tried to follow the tutorials. I can't turn the swap off :S
> 
BUT my problem is, that i CANNOT choose "install alongside other operating systems". Ubuntu just says, that i dont have any system installed, which i actually have. GParted says the same. 
Same problem here. Only difference is that when I run GParted, it actually freezes .... which is why I decided to destroy that evil CD ...

---

### Post by jrev on 2010-11-01
you can always download "gparted" from synaptic, even on a live-CD

Did you try to download Slitaz and burn it to a CD ?
Slitaz includes gparted
did you check this :
[http://ftp.heanet.ie/pub/linuxmint.com/docs/user-guide/english_9.0.pdf](http://ftp.heanet.ie/pub/linuxmint.com/docs/user-guide/english_9.0.pdf)

---

### Post by Flame_Phoenix on 2010-11-01
So, you are saying that I should download GParted in my Live-CD of linux mint and then try to follow the steps ? 
That sounds a good idea ... for someone with a stable internet connection (I assume it is some sort of problem from my network driver). 

I will see what I can do, thanks for the tip, I will surely try doing that!

---

### Post by jrev on 2010-11-01
> **jrev said:**
> [SIZE="5"]Yes[/SIZE] refer to my post #2
bye

---

### Post by srs5694 on 2010-11-01
Some comments and suggestions:


[list]
[*]Although the symptoms are the same, Flame_Phoenix's and DualCore555's problems have different causes and different solutions.
[*]Because of the previous fact, I recommend that DualCore555 start another thread if s/he continues to have problems; in my experience, threads that attempt to address two fundamentally different problems become very confusing very quickly. (See below, though.)
[*]I recommend that Flame_Phoenix review [this Web page](http://www.rodsbooks.com/missing-parts/index.html) of mine, which covers one possible cause of the problem. If that doesn't help, post the output of "sudo fdisk -lu /dev/sda". Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility. Note that the "u" part of "-lu" is important; it changes the units from the uselessly imprecise (for this problem) cylinder units to sector units.
[*]DualCore555 should review [this post of mine](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) in a previous thread. It should solve the problem.
[*]Neither problem will be solved by filesystem manipulations such as defragmenting a disk.
[*]Flame_Phoenix's claim that "Linux is causing the problem by not reading the partitions correctly" may not be correct. Certainly it's not correct in DualCore555's case, since that problem is caused by corrupt partitioning data that Windows is tolerating but that Linux (or at least, the Ubuntu installer) is not tolerating. The same may be true of Flame_Phoenix's problem, too, although the precise cause isn't yet clear. (I know enough to rule out the type of damage to Flame_Phoenix's disk that's clearly present on DualCore555's disk, but it's not yet clear to me precisely what's causing problems for Flame_Phoenix.)
[*]As added information for the previous point, the Linux installer relies on a library called libparted to deal with partition identification and partitioning. This library is very fussy; it tends to show the disk as blank when there are any problems with the partition table. In some sense this is good, since these problems could come back and cause major data loss in the future, so it's best that they be discovered and addressed ASAP. Unfortunately, libparted and the programs based upon it do a poor job of communicating the nature of the problem to users.
[/list]

---

### Post by Flame_Phoenix on 2010-11-01
Jesus Christ. After a lot of fear and some guts, I decided to take the final heroic step and to click that "Install Now" button I was so afraid of.

I must thank you all for helping me fix this problem. I followed jrev suggestion and deleted my Linux partition entirely. After that it became easy.

Now I struggle against Linux Mint and KDE immense bugs, which is why I am reconsidering installing a stable version of Linux - the Ubuntu you all love so much (and now I understand why!)
But that's a tale for another time, now that I have learned the dual boot magic of Linux I need not to bother you people with my silly questions :P

Thanks to all of you!!

Is there a way I can pay my debt?
(PS: how do I mark this thing as solved?)

---

### Post by oldfred on 2010-11-01
Progress, we love to see that.

I have been trying to get a beer or at least a cup of coffee, but delivery seems to be an issue.:) No world tours planned soon.
 
We are more a pay it forward model. As you learn you can help someone else who know less. I found when I first started & Googled for help, that I was usually in the forum. Then I started looking at other questions and ran across one I had just solved for myself and responded. I have been hooked ever since.

Instructions on solved are in my signature.

---

### Post by Flame_Phoenix on 2010-11-01
Done, Thx ! :D

---

