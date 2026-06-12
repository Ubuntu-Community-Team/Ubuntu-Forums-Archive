---
title: "Partition sizes for multiple installs"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by smcrossman on 2012-01-19
[FONT="Verdana"][COLOR="Indigo"]I have a 64 bit 320GB hard drive.  I would like to do side by side installs of (reluctantly) Win 7 (Home Prem), Ubuntu 11.10 (with a few KDE apps but not the full KDE system), and Server 11.10.  I'm already in the process as upgrading of placing my /home on a separate partition.  After much trial and error on my netbook I think I have a basic size for Win 7....the recovery part should be abut 25-30 MiB, and the OS & files will be 50-70 GB because I'm going to be using it for some file intensive applications.

1) [COLOR="DeepSkyBlue"]a)What are the minimums for the root partitions for both Desktop and Server?[/COLOR]  [COLOR="DarkOrchid"]b)They can share the home file if it is separate partition, correct?[/COLOR] [COLOR="Magenta"]c)How big does the swap partition need to be and is one sufficient to cover both installs?[/COLOR]

I'm looking to try out Server and see if I can replace desktop with it for my home network.  Hopefully in the near future (well 6 months likely) the desktop will be replaced with a new laptop and I would like to be able to just install based on the outcome of this trial time and go without a lot of fiddling around.

2)Backups and reinstaling from them.
For backup I'm currently using KBackup since I'm having trouble finding anything that will backup to my Network Storage Drive although I've done some Nepomuk and then moved them to the network drive.[COLOR="Green"] a)Will I be able to pull either of those backups into the new setup if all the installed programs are NOT the same?[/COLOR]  I've already lost most of my files when my first desktop upgrade install corrupted and likewise on the netbook (before I managed to get backups working). So at this point it isn't a huge deal but will be on the future migration. Thanks for taking the time to look at this. If you need more inforamtion just ask.[/COLOR][/FONT]

---

### Post by cortman on 2012-01-19
> **smcrossman said:**
> I have a 64 bit 320GB hard drive.  I would like to do side by side installs of (reluctantly) Win 7 (Home Prem), Ubuntu 11.10 (with a few KDE apps but not the full KDE system), and Server 11.10.  I'm already in the process as upgrading of placing my /home on a separate partition.  After much trial and error on my netbook I think I have a basic size for Win 7....the recovery part should be abut 25-30 MiB, and the OS & files will be 50-70 GB because I'm going to be using it for some file intensive applications.

1) a)What are the minimums for the root partitions for both Desktop and Server?b)They can share the home file if it is separate partition, correct?c)How big does the swap partition need to be and is one sufficient to cover both installs?

I'm looking to try out Server and see if I can replace desktop with it for my home network.  Hopefully in the near future (well 6 months likely) the desktop will be replaced with a new laptop and I would like to be able to just install based on the outcome of this trial time and go without a lot of fiddling around.


1) a) I wouldn't go any smaller than 20 GB for the root partitions of both.

b) This is best not done. Although possible, it can create problems later on.

c) Swap partition should equal your RAM. If you want to hibernate one system while booting into another, you might consider 2x or 3x your RAM.

Since you're only using 50-70 GB for windows, that leaves you about 250 GB for Ubuntu. I'd say give each installation its own home partition (or just make /home part of the root partition) and give them plenty of room. You can expand/shrink your Ubuntu partitions quite easily later.

And... I'm not really qualified to offer much opinion on backups. I use Deja Dup for most things and a couple homemade scripts for the rest.

---

### Post by smcrossman on 2012-01-19
Thanks cortman!  I've decided separate home partition protects my documents (in addition to backing up) from corruptions when installing new software or when upgrading, etc.  I was hoping the 2 versions would share nicely so I could do whatever I needed in whichever one I was working in at the time.

I just checked my RAM  3.7GB which basically means I'm running on 4...No wonder I'm having memory and speed issues! LOL  At this point no sense upgrading if I'm going with a new one within the next 6 months though.  Wow! only 20GB for the root partition?  I think I only cut back to about 50 on the netbook. I guess If windows screams for more there before I get this one configured I have someplace to pull it from. (I refuse to keep any important Ubuntu documents, etc on the netbook right now because it's been behaving poorly). 

If noone offers info on the backups I might just put that into a new thread.  I'll see what turns up before I hit the sack tonight!

---

### Post by darkod on 2012-01-19
Unless you plan to have loads of big files, loads of data, accessible only in ubuntu, splitting it 70/250 is a waste. Give more space to win7 since it needs it anyway. Even better, create a ntfs partition for your data that both OSs will be able to access.

Assuming a shared data partition and a smallish /home, ubuntu desktop should be fine with 10-15GB for the /.
The server is even smaller, again it depends if you will be running any server functions and data (databases, etc) on it. I have a network storage based on ubuntu and the default 10.04.3 install with samba server and openssh is approx 1.7GB. If you plan something similar, 10GB is plenty. Everything above is overkill.

I agree sharing /home is a bad idea especially between desktop and server. For the server a separate /home might not be a good solution, it all depends what you will be running on it.

As a backup solution take a look at FS Archiver: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

It can create the backup on a network destination if you mount it first. The source is always backed up unmounted. What I like about it is that it can restore on partition with different size as long as the data fits. If tomorrow you want to restore on a smaller partition, it will work as long as it's bigger than the data size.

Clonezilla for example can restore on a partition with the same or larger size, not smaller. At least that's how I understood it.

---

### Post by cortman on 2012-01-19
> **smcrossman said:**
> Thanks cortman!  I've decided separate home partition protects my documents (in addition to backing up) from corruptions when installing new software or when upgrading, etc.  I was hoping the 2 versions would share nicely so I could do whatever I needed in whichever one I was working in at the time.

I just checked my RAM  3.7GB which basically means I'm running on 4...No wonder I'm having memory and speed issues! LOL  At this point no sense upgrading if I'm going with a new one within the next 6 months though.  Wow! only 20GB for the root partition?  I think I only cut back to about 50 on the netbook. I guess If windows screams for more there before I get this one configured I have someplace to pull it from. (I refuse to keep any important Ubuntu documents, etc on the netbook right now because it's been behaving poorly). 

If noone offers info on the backups I might just put that into a new thread.  I'll see what turns up before I hit the sack tonight!

Hm... 4 GB of RAM is still quite up-to-date. That's what I run myself. Ubuntu should run smoothly on those specs.
Re what darkod said... If you want to share files between Win7 and Ubuntu, by all means you want a separate "data" partition on the drive, and if you do that, 15-25 GB for each Ubuntu installation should be plenty.
I have a "data" partition on my 750 GB HD, where I keep all my personal files. It's equally accessible from Windows and Ubuntu and works quite well. BUT you want to create this partition with Windows, so that it (Windows) can "see" it. Ubuntu can see any and all Windows partitions, Windows itself keeps its nose too high in the air to be able to see any but Windows partitions.


> **darkod said:**
> Everything above is overkill.

If the space is there, why not use it?

---

### Post by darkod on 2012-01-19
> **cortman said:**
> 
If the space is there, why not use it?

Maybe it didn't sound right because I tried to keep it short. My point was why give loads of space you probably know you will never fill up, and on the other hand making your data partition rather small.
In most cases, you will find yourself with a data partition filling up sooner than you thought, and a / partition with a free space.
It's best to try to avoid resizing partitions later because that always carries a risk.

---

### Post by smcrossman on 2012-01-19
Thanks! Bummer they won't share the home file....but since I've never worked with a true "server" OS that is going to be all hit and miss while I get my feet under me so a separate home is probably a good idea anyway. 

A little confused with the data partition in most cases would actually be the /home partition in most basic cases anyway...right? Is there a reason to do a separate one (other than my NAS where I hope to keep the things I need to share among computers and remotely access, such as media, general files, etc)?  I hadn't thought about sharing a data partition with Windows....I mean that way I could access most documents, etc, with either OS since I used open office in Windows before I started using Ubuntu.  It would certainly save room since I wouldn't have to duplicate files for each system.

I'll check out the backup tool link. Sounds like it would work better and if the partition size doesn't have to match perfectly a new install should accept the files from the archive/backup.

So tomorrow I guess I start the windows install (as soon as I re-discover the workaround for the upgrade key on a non-windows hard drive).  Then reinstalling Ubuntu & then server (since I believe trying to install it the other way around server wants to downgrade to Ubuntu...IF I read that correctly today!)
Thanks for the input! I really like doing it myself...only with no training I'm usually in over my head. Knowing this before hand will save a LOT of headaches later because I don't like resizing partitions with data on them.  Only been doing it on the netbook lately because I know it is going to be completely wiped and fresh installs once I get the desktop up and running.  Most likely without windows at all this time.  Off to the Windows community support stuff....

---

### Post by cortman on 2012-01-20
> **darkod said:**
> Maybe it didn't sound right because I tried to keep it short. My point was why give loads of space you probably know you will never fill up, and on the other hand making your data partition rather small.
In most cases, you will find yourself with a data partition filling up sooner than you thought, and a / partition with a free space.
It's best to try to avoid resizing partitions later because that always carries a risk.

Ah, ok, I see what you mean. I'm just considering that it's good to keep room enough for applications too, even though Linux applications tend to be .5 or less the size of Windows, what with shared libraries and all.

> **smcrossman said:**
> 
A little confused with the data partition in most cases would actually be the /home partition in most basic cases anyway...right?

No, not at all. The /home folder, whether it be on a separate partition or not, is where Ubuntu stores all your user data, all your program data, and is the default location for your personal data. When we're talking about a "data" partition, we're just referring to a blank partition for keeping your personal items on. A "my stuff" partition. Keeping your stuff on a separate partition not only protects it (if your OS crashes, your data remains untouched) but also makes it accessible by any OS on that computer.

> **smcrossman said:**
> 
Is there a reason to do a separate one (other than my NAS where I hope to keep the things I need to share among computers and remotely access, such as media, general files, etc)?

In this case, you have less need of a separate data partition. If all your stuff is just on a NAS, you can get at from any OS on the PC anyway.

> **smcrossman said:**
> 
Thanks for the input! 

We're all more than happy to help! Good luck with the installation, and keep us posted!

---

### Post by smcrossman on 2012-01-20
> Quote:
Originally Posted by smcrossman  
A little confused with the data partition in most cases would actually be the /home partition in most basic cases anyway...right?
No, not at all. The /home folder, whether it be on a separate partition or not, is where Ubuntu stores all your user data, all your program data, and is the default location for your personal data. When we're talking about a "data" partition, we're just referring to a blank partition for keeping your personal items on. A "my stuff" partition. Keeping your stuff on a separate partition not only protects it (if your OS crashes, your data remains untouched) but also makes it accessible by any OS on that computer.

Hmmm...okay so if you do a straight full install of Ubuntu Desktop you end up with 3 partitions....the OS & home; and extended and swap. So would the extended be the data partition? I always wondered what it was exactly since it was much larger than the others. I just thought it was some kind of workspace or overflow space....really not techie huh?

I'm burning a new 11.10 64 bit since my last one was corrupted so when I installed last time I had to reinstall 11.04 and then upgrade.  I have my windows .iso and a cheat sheet on how to work around no original windows on the hard-drive if need be so I'll be starting on that in a bit. Lots of room organizing in that location so I can monitor as the process proceeds. Beauty of multiple pcs is that I can always use the extra to go looking for help. So yes, I'll keep you posted and I'll mark this thread as solved when the installs are done and working.

Thanks again!

---

### Post by nipunshakya on 2012-01-20
@OP: Hi. sorry I didn't go thoroughly through the previous comments of other gurus here. 

Basically, i have similar scenario as yours, 320gib hard disk. but instead of a triple boot, i have a dual boot. and my partition scheme is something like this:

a. 60 gib ntfs for windows 7
b. 200 gib ntfs for data sharing between windows and linux(thats better i guess)
1. 25 gb for /
2. 10 gb for /home
3. 3gb swap area

All 1,2 and 3 are  ext4 logical partitions under same extended partition while 'a' and 'b' are primary partitions.
If you intend to have a server edition of ubuntu, you can go with similar partition scheme, with /home shared for both ubuntu versions and a 4gib ram if you wish for hibernation and suspending your machine while working.


Regards,WinuxUser

---

### Post by cortman on 2012-01-20
> **WinuxUser said:**
> 
a. 60 gib ntfs for windows 7
b. 200 gib ntfs for data sharing between windows and linux(thats better i guess)
1. 25 gb for /
2. 10 gb for /home
3. 3gb swap area

All 1,2 and 3 are  ext4 logical partitions under same extended partition while 'a' and 'b' are primary partitions.


^^ Good example of a well partitioned HD. I have mine partitioned approximately as follows-

a) 100 GB for Windows
b) 40 GB for Ubuntu
c) 500 GB data sharing between Ubuntu and Windows (the "data" partition)
d) 40 GB for Fedora 16
e) 4 GB swap

If you let Ubuntu install on its own without telling it how to partition it will make two partitions; one for / and everything under it (i.e., /home, /etc, /usr, /boot, etc.) and one for swap. The "data" partition we're referring to is something you do on your own after the fact. Its purpose is to be a point for file storage that can be accessed by both Windows and Ubuntu.

> **WinuxUser said:**
> 
with /home shared for both ubuntu versions

I DO NOT recommend this.

---

### Post by nipunshakya on 2012-01-20
> **cortman said:**
> ^^ Good example of a well partitioned HD. I have mine partitioned approximately as follows-

a) 100 GB for Windows
b) 40 GB for Ubuntu
c) 500 GB data sharing between Ubuntu and Windows (the "data" partition)
d) 40 GB for Fedora 16
e) 4 GB swap

Glad to know that after a long struggle to get a perfect combination of ubuntu and windows 7 i found this scheme best for me, and even more glad to know that a guru has similar to mine..

Thank You.
Regards,Winuxuser

---

### Post by cortman on 2012-01-20
> **WinuxUser said:**
> Glad to know that after a long struggle to get a perfect combination of ubuntu and windows 7 i found this scheme best for me, and even more glad to know that a guru has similar to mine..

Thank You.
Regards,Winuxuser

Whoa, whoa! I am FAR from a guru! I'm still learning myself on a LOT of things. It took me a good bit of trial and error to get a decent partitioning scheme myself, but I'm very happy with it, and yours looks good too!

---

### Post by nipunshakya on 2012-01-20
^^^^^ :) :) :)

---

### Post by smcrossman on 2012-01-20
hmmm....this is what I have so far. Only 2 install done...currently installing packages I heavily rely on into Ubuntu and doing first round of updates/upgrades so I can use it if need be. I have 8 partitions and a block of Free between the windows and Ubuntu sections which I guess if I format it would become partition 4

1  105 MB NTFS System Restore
2  157 GB NTFS Windows (I know that I'll be storing a lot of video/audio so I went rather large here

Free 18GB

3 144GB  "Extended" note says its for "Logical"
5 10GB Swap
6 22 GB  Ext4 /
7 50 GB  Ext4 /home
8 20 GB
9 42 GB

8&9 are for Server currently unformatted & unassigned

Regardless....so far so good. time to CALL support re: my network storage drive already did chat for a couple of hours so I'm being elevated.  See if I can get that resolved in time to set it up after I get Server installed and basic set ups done in Desktop and Windows. What a day!

---

### Post by cortman on 2012-01-20
Looks good so far! Your partitions are sized a little oddly, but as you use your various OS's you'll find what works for you, and can resize accordingly. Be very careful with resizing though, and always be sure your data is backed up.
Good luck with your NAS. Any more questions, feel free to post!

---

### Post by nipunshakya on 2012-01-20
> **smcrossman said:**
> hmmm....this is what I have so far. Only 2 install done...currently installing packages I heavily rely on into Ubuntu and doing first round of updates/upgrades so I can use it if need be. I have 8 partitions and a block of Free between the windows and Ubuntu sections which I guess if I format it would become partition 4

1  105 MB NTFS System Restore
2  157 GB NTFS Windows (I know that I'll be storing a lot of video/audio so I went rather large here

Free 18GB

3 144GB  "Extended" note says its for "Logical"
5 10GB Swap
6 22 GB  Ext4 /
7 50 GB  Ext4 /home
8 20 GB
9 42 GB

8&9 are for Server currently unformatted & unassigned

Regardless....so far so good. time to CALL support re: my network storage drive already did chat for a couple of hours so I'm being elevated.  See if I can get that resolved in time to set it up after I get Server installed and basic set ups done in Desktop and Windows. What a day!

I think u did too much on swap area. 10gib was more than needed. And, there is no need to worry about extended saying logical, coz its that way. Just assume extended as a container for a number of logical partitions. 


Goodluck And happy Linuxing
Regards,WinuxUser

---

### Post by darkod on 2012-01-21
@WinuxUser
But you can have only one extended partition. You can't create a second one.

The layout looks good, but I have no idea why you left the 18GB unallocated space in front of the extended partition, why didn't you just continue where sda2 ends.

All logical partitions have to be next to each other, making a "group" and linux marks the extended partition according to that. Make sure you don't try to make logical partitions which are not next to each other as a one single group.

---

### Post by nipunshakya on 2012-01-21
> **darkod said:**
> @WinuxUser
But you can have only one extended partition. You can't create a second one.

Thanks Drako. Shall consider that as an unforgettable advice. I corrected my previous comment accordingly. Thanks again.:p

---

### Post by smcrossman on 2012-01-21
Actually I didnn't create the extended drive...regardless of what I partition or how it is just there.

Anyway the free space was because I was re-partitioning from pre-existing setup and thought I was going to try to save some data. I wanted it in case I needed it for windows but didn't want to commit it to windows because I HATE windows. I started with my linux partitions from the end of the disk to the middle which is totally backwards but I knew approx (which is why the sizes are so odd....I did approximates not exact numbers figuring more than less would be best) what I THOUGHT would suffice and then whatever free space was left over could be used by windows if needed in the future.  Since the server thing is a learning situation and may or may  not be included when I get a new machine I wasn't hung up on getting it just right this time. As long as I back up my info and all this should be good for a while now.

The installs went fine. Only I had a duh moment when it asked about installing the bootloader in server & told it yes.  Now I'm stuck with no menu and only access to server because I have a nVidia system which grub default is out of range. Know how to fix it in desktop, using graphical but not in command style.  So I have to go refresh my memory on that issue and the fixes I ignored before.  Not fun,but at least I KNOW what the issue is a year ago when I encountered this I was in a full blown panic...LOL.

Since the partitioning and installs are done basically successfully I'm going to mark the thread solved. I'd love to see further input if ya'll have thoughts or discoveries along this line for future reference!

Thanks for your help!

---

### Post by nipunshakya on 2012-01-21
Glad to know that....Happy linuxiing.

---

