---
title: "[SOLVED] Newbie install of Kubuntu dual boot"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by just_bruce on 2007-07-23
I just downloaded kubuntu feisty fawn version and it boots and runs just fine off the live cd.  
The machine is an IBM T60 Laptop with WinXP Pro. It has my son's data on it, which I am just copying off to DVD now.  I downloaded the gparted livecd and looked at the partitions.
On the 93MB formatted hard drive there are only two partitions. 
A big one, formatted ntfs, starts at the beginning and goes almost to the end. At the end of the drive is a small partition called SERVICE001 which seems to have in it some recovery software from IBM.  (You can see it with a Knoppix livecd boot!) The big windows partition is only about half full, 44.5 used and around 45 unused.  
From reading here, I think I need to 
1. shrink the big windows partition to about 50-60GB, using gparted. 
2. let Kubuntu feisty install into the 30GB empty space, using the install icon on the desktop, without my creating any new partitions first.
It seems like the Kubuntu install should create any partitions it needs in the vacant real estate. It will also if i understand right install the grub boot loader so that Kubuntu will be booted first, but Windows can also be booted.  It will rewrite the MBR so that grub is the boot loader.

Questions:
1. Will this work, or will the little service partition at the end foul it up?
1a. Can i try booting WinXP after shrinking the partition just to check/ Or will that foul things up?
2. Should I choose the "largest free partition" option in the install screen? I don't want to foul up so the machine won't boot WinXP.
3. How do I boot windows later when necessary (I hope seldom, but my son may not agree)? Will grub present it as an option? Or do I need to type in some weird codes to grub?
Thanks a lot for the advice-- I'm sure it will go smoothly but I want to leave myself an escape route at every stage!

---

### Post by Pumalite on 2007-07-23
Seems you are ready to go. The last partition is probably XP Rescue. You need to think if you want to keep it. You could get anXP CD. Defrag XP several times, erase all temp files. You are backing up your data. Good. Use Gparted> Srink XP partition and install. Make sure you make a partition of the srunk space. Don't leave it 'unallocated'. Then you better manually (  Manual ) create a 500MB Swap partition, 12 GB '/' partition, the rest, /home. And install.

---

### Post by just_bruce on 2007-07-23
> **Pumalite said:**
> Use Gparted> Srink XP partition and install. Make sure you make a partition of the srunk space. Don't leave it 'unallocated'. Then you better manually (  Manual ) create a 500MB Swap partition, 12 GB '/' partition, the rest, /home. And install.

So I use gparted to
1. Shrink the XP partition
2. Create a 500 mb partition for '/swap'
3. create a 12gb partition for '/'
4. Create a partition in the rest for '/home '?

Does gparted let me name the partitions like that or do I let install name them?
In that case I would simply create the 3 new partitions in the void between the shrunk XP partition and the SERVICE001 partition at the top of the disk, and then in install point the installer to the right partition when it asks me where to put them?

Sorry for all the questions, but I am a bit afraid to start the installer without knowing what it will do in advance. Wish I could watch someone do it first.

And can I restart windows after shrink but before creating new partitions? and also, can I use the gparted in kubuntu, or should I boot in the one from the live cd gparted?
any suggestions?
:confused:

---

### Post by Pumalite on 2007-07-23
I meant the Gparted, stand alone, bootable CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Pumalite on 2007-07-23
This is a good read:

[http://ubuntuforums.org/showthread.php?t=480484](http://ubuntuforums.org/showthread.php?t=480484)

---

### Post by just_bruce on 2007-07-23
That sounds pretty good. the thread 480484 on the dual boot is nice-- shows you the screen images, so I know what to expect. I don't want to try it tonite-- just ran 3 mi and might make a mistake from being tired.  Maybe tomorrow or the next day (have to work tomorrow).  I can boot the gparted live cd and put in the partitions, then boot the kubuntu live cd and select install.  all the partitions will be there-- if i use manual i can just put them in properly.
Thanks a lot!!  I love ubuntu/kubuntu, messed with fedora but this is much better.

---

### Post by just_bruce on 2007-07-27
I completed the install on my T60 laptop's hard drive.  I just thought I'd document the steps and the questions I asked myself and answered in the hope they might help someone else.
First I booted the Gparted live cd and repartitioned.  I shrank the windows partition from 89gb to 50+-gb. I then put a partition of type extended in the unallocated space between the NTFS windows partition and the SERVICE001 partition at the upper end (it is about 4gb).  
I then inserted 3 logical partitions in the large extended partition. the one for root ('/') was 12gb; the one for swap was 3gb (there are 2gb of memory on this machine, and i saw that 1.5 to 2x memory is good for swap) and te rest was for /home.  you don't name the partitions here, you do that in the installer. but you make them the right size and target them for these uses.  formats: the home and root (/) partitions are formatted ext3; but for the swap, you must choose linux-swap type. i made this mistake, and had to go in and redo.
After i thought i had setup partitions correctly, I discovered that there was 4mb unallocated partition at the end.  It took me a while to figure out that that is because the sector/cylinder/block count did not come out exactly when I put in the size of the partitions. If i had been a bit (a lot!) more careful and calculated out exactly the sizes i might have been able to eliminate that.  
When I thought i had it wrong, i went in and deleted the new partitions and tried again. I got the same result-- but i also learned that after resizing the windows partition you can reboot the machine to windows!!  When you do this, you first get a small dos screen running chkdsk for a few minutes-- It believes the disk is messed with, and checks it.  This will finish with no errors, and then it will ask you to boot again.  I did it, and windows came right up.

So with the partitions correct, I booted my kubuntu 7.04 livecd and clicked the install icon.  After the simple questions it goes into a dialog about partitioning.  It is at this point you discover that you can't make a swap partition unless you have created yours with gparted as a linux-swap type.  For the others you simply associate /home or '/' with the right one.
I had to go back thru the gparted boot and partition creation to get the partition for swap as a linux-swap type, and then boot the kubuntu livecd and install again.  Note that stopping the install during the partitioning without committing does not modify the disk and you can go back to the partitioning if you did not get it right! that's comforting.

You then let it run (after setting up the user and password).  It takes a while and installs everything. After you get the success screen, you reboot.

Wonder of wonders! You get the grub boot prompt which asks if you want to boot linux (the first option) or windows xp professional (down about 4 options).  Both of them work!!

With this procedure you still have the service partition in case you need to restore windows at some point.

Hope some newbie with an IBM laptop can use this info--  and many thanks to Pumalite for the good advice about the process.

---

