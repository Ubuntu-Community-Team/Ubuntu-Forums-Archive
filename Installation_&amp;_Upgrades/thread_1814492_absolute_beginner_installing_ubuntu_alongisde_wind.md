---
title: "absolute beginner: installing ubuntu alongisde windows with shared access hard drive"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by aaj99 on 2011-07-29
hello people

i have just bought a laptop with windows7 preinstalled. i would like to install ubuntu alongside (windows for work, ubuntu for photos and music)

i have tried a wubi installation but it seems that the max hard disk space available for my data is 30gb. i therefore think i need to do a proper installation. ideally, i would like to be able to access all my files from both windows and ubuntu - is this possible? if not, i would put 100gb for windows and 400gb for ubuntu

i would really really appreciate some clear advice. i have no computer background, and am a bit nervous of entering the linux world, but feel i should do all i can to fight the windows/mac hegemony

ps once a partition is made, is there any way of changing it?

---

### Post by oldfred on 2011-07-29
Yes you can change partitions around after creating but there are rules and it may be extremely difficult to add space at the end of a drive to a partition near the beginning of the drive. So some planning is a good idea.

Most new win7 computers come with all four primary partitions used. You can only have four primary partitions, but can convert one primary to an extended an make as many logical partitions as you need. Windows needs to boot from a primary, Linux can boot from either a primary or logical. Both system will read a NTFS formated logical partition which is the best way to share lots of data. 

Lots of links - review and come back with more questions if needed. Backup is vital and having a Windows repairCd or Linux liveCD is important if repairs are needed.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by aaj99 on 2011-08-03
dear oldfred

thanks very much for the links - the most helpful i've seen so far.

i am still a bit confused, though:

i think the way to go is through the standard (guided/wizard) installation, as there is an option to allocate disk space between ubuntu and files
(see image: [http://www.psychocats.net/ubuntu/images/installingnattythumb07.png](http://www.psychocats.net/ubuntu/images/installingnattythumb07.png)). the 'files' partition is nfts - which i think means i can access it from both ubuntu and windows. 

is this definitely the case? e.g. if i put all my photos on the files partition would i get full access from both windows and ubuntu? (i plan to use ubuntu for everything except officey stuff, but i may end up only using it for downloading, so i need this flexibility)

the fact that you sent me so many links on partitioning makes me think there must be something i'm missing... or is it just the case that this 'files' partition is new to the 11.04 release..? (or perhaps everyone is so linux-literate that you are not naturally drawn to the wizard, as i am...) 

sorry if i seem a bit useless, it's just that i really really don't want to mess up my computer

thanks again

aaj

---

### Post by YesWeCan on 2011-08-03
> **aaj99 said:**
> hello people

i have just bought a laptop with windows7 preinstalled. i would like to install ubuntu alongside (windows for work, ubuntu for photos and music)

i have tried a wubi installation but it seems that the max hard disk space available for my data is 30gb. i therefore think i need to do a proper installation. ideally, i would like to be able to access all my files from both windows and ubuntu - is this possible? if not, i would put 100gb for windows and 400gb for ubuntu

i would really really appreciate some clear advice. i have no computer background, and am a bit nervous of entering the linux world, but feel i should do all i can to fight the windows/mac hegemony

ps once a partition is made, is there any way of changing it?
You should be nervous (a little) because it is possible to trash your Windows installation if you are not careful. So good idea to visit here and get advice.

Ubuntu and linux in general is not as forgiving as Windows. Linux commands tend to do what you tell them without seeking confirmation or warning you of potential bad side-effects. The Ubuntu installer is, unfortunately, like this.

Ubuntu can read and write Windows filesystems but Windows cannot read linux filesystems.

Your home directory in Ubuntu needs to be in a linux filesystem. So you cannot have a shared home folder as it were. But you can share a separate filesystem as long as Windows can read and write it.

Your hard disk can have up to 4 primary partitions. Ubuntu requires 1 (of type "extended"). So you need to make sure there is one free. Use Windows Disk manager to shrink/move/defrag existing partitions to make enough empty disk space for Ubuntu to consume. It is safer to use Windows tools to modify Windows partitions.

FYI installing Ubuntu causes your MBR (master boot record - a tiny code at the front of your disk) to be modified in a way that breaks the normal Windows boot process. This means you can no longer boot Windows unless your Ubuntu files are present. So if you were to delete Ubuntu you would not be able to boot Windows. Similarly, if Windows should happen to repair the MBR code then Ubuntu will no longer boot. In either case, you can use the Ubuntu live CD to repair the MBR code to whichever one you desire.

Back up any vital files before embarking on any of this.

Try out Ubuntu on the live CD and make sure your laptop hardware works ok.
:)

Also be aware that some warranties are void if you mess with the system in certain ways. If this is important to you, you ought to contact your retailer to check whether dual-booting with Ubuntu will affect your warranty. :!:

---

### Post by Sansari on 2011-08-03
Can it work like this:

Hard Drive 1:
Partition 1: Windows booting only, NTFS
Partition 2: Linux booting only, ext3/4
Partition 3: Linux swap only, ext3/4

Hard Drive 2:
Single Partition: All applications and files from both OS's saved here, NTFS

I'm not too familiar with the linux filesystem, but is it possible to have it install all programs and save all files to a separate NTFS partition? I'm not sure how you'd tell a package manager to install programs to a separate partition; that's my main problem.

Also, if I wanted just the linux boot & swap on HDD 1, and all linux files and applications on HDD 2 (so no windows involved) would it be as easy as putting / on HDD 1 and /home on HDD 2?

Oh and one more situation, could I do this:

Single Hard Drive:
Partition 1: Windows 7 boot, NTFS
Partition 2: Windows xp boot, NTFS
Partition 3: Logical
[INDENT]Sub 1: Linux boot, ext3/4
Sub 2: Linux swap, ext3/4
[/INDENT]Partition 4: Storage for all 3 OS's, NTFS

Would XP complain about this setup? 
Thanks for any help :P

---

### Post by Duncan Williams on 2011-08-03
there is a very simple way to do what you want.
It worked for me and I never ended up with any corruption.
I only use linux now but I used dual boot for months.

> boot from ubuntu live cd.
> install ubuntu
> it asks if you want to keep your windows instalation.
> select that option (install alongside current instalation)
You then have dual boot setup with windows on one partition and ubuntu on another.

After that you can access your windows partition from ubuntu (and all files on there)
You can access your linux partition from windows using:
[http://www.google.com/search?q=read%20linux%20from%20windows](http://www.google.com/search?q=read%20linux%20from%20windows)

**gparted** for adding/changing partitions 

Please correct me if I have missed something here, anyone.

---

### Post by oldfred on 2011-08-03
@Sansari
If you need more info start you own thread. Windows can only boot from one partition with the boot flag (active partition in windows). So grub will only find one set of boot files in the active partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

@aaj99
I always partition in advance and then use manual install. But I want control over partition sizes where all the automatic installs just arbitrarily split drive. I have been using a shared partition since 2006, then it was FAT32, but for the last 2-3 years it has been NTFS. I cannot recommend FAT anymore except for those devices that have to have it like a camera or Xbox.
My shared NTFS partition has my Firefox & Thunderbird profiles & all photos. That way I have the same email & bookmarks in both systems. I did install the windows (3.8) Picasa in wine, not the (3.0) Linux beta, but each copy has its own edited files which does not really help much.
With the full Picasa in .wine my wife has little to complain about windows working better.

---

### Post by aaj99 on 2011-08-07
brilliant guys, think we're nearly there...
oldfred, you sound like you have the set up i need...
(duncan, that way it sounds like i can access them but not use them till i've copied them)
can you just clarify what kind of partitioning i need to do...?

i have all 4 partitions done in windows, so i need to create an extension.. which partition do i do this in..?

then how much do i allocate to linux?
how big does the swap file need to be? (i want to use hibernate function)
the remainder will be my nfts 

then you say to do a manual installation.. what does this mean?

thanks again everyone (esp oldfred)

---

### Post by oldfred on 2011-08-07
I think I answered all your questions in post #2. Others often have different opinions and none are really wrong. It depends on how you plan to use system. I find my optimal install in a couple of years is not so good. But I like a new hard drive every 3 years or so, for reliability, so I  get to reorganize again.:)

If you are thinking of hibernating you need to make swap equal to RAM in GiB or a little bigger than GB so there is room for all of memory. But if dual booting you do have to be careful hibernating. If a hibernated system is using a file and you boot into the other system and do something to that same file you just corrupted the system. I find Ubuntu boots fast enough that I do not need to hibernate. Part of the reason I do not want to boot into my XP as it now is up to 4-5 minutes to boot where Ubuntu is 40-50 seconds.

Manual install or Something Else is where you select a partition, choose a format like ext4 and select what you use it for like / or /home or swap. Swap does not have a format and once one swap is created you do not have to create another as it finds the current one automatically.

---

### Post by Duncan Williams on 2011-08-08
[I](duncan, that way it sounds like i can access them but not use them till i've copied them)
can you just clarify what kind of partitioning i need to do...?[/I]

If you go the standard install way.
You will be asked re/ your linux partition size.
It will leave the rest for windows partition.
In other words it does the partitioning for you.
If you wish to establish 4 partitions up front and install to one of them.
You will have to tell the install manager.

---

