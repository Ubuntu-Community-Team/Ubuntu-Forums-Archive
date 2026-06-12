---
title: "Triple OS and the &quot;Missing Operating System&quot; warning"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by redheat on 2007-05-30
Hi all

 Currently I have two OS installed on my system on two separate hardrives:

 hardrive one which is a western digital 250 Gb hard drive with two partitions only:
    a. Parition D for windows vista business (50 Gb)
    b. Partition G for non operating system content. (200 Gb)

 harddrive two which is also a western digital 250 Gb baracuda which has three partitions:

   a. Parition C: for windows XP professional (60 GB)
   b. Partition F: Unallocated Space (20 Gb) this one is reserved for Ubuntu, version 7.04 by the way.
   c. Partition E for non-operating system content (170 Gb) 

 First of all, I had windows xp as the official operating system, and I set its harddrive to be the main harddrive to boot from (in the bios I choose this harddrives name as first boot). After that I installed windows vista business on the second harddrive but still maintained the first one as the main boot drive. Of course this leads us to the famous os choice screen: 
 "Choose which operating system: 
                                                            Older versions of windows 
                                                            Windows Vista Business                                                            " 
 
  I went ahead with the installation of  Ubuntu 7.0.4 on partition F ( the one with 20 GB of unallocated), sorry if  I call it F, just for convenience only since its not formatted at all only unallocated space. Anyhow, I followed the usual installation steps and when it came to the boot partition I let the live CD do it. I choose the option "Guided and make use of maximum contiguous free space" and after this the installation process continued as usual.
 
 After the installation finished, a windows popped-up asking me to remove the CD and restart. Did that restarted the machine, went into bios changed the first boot device from CD to harddisk, and continued and then Poof! can't login anywhere a message called "Missing Operating System" popped up in place of the usual "choose operating system."  I was hoping for this: The OS choose menu woud load with a third OS listed...

 Of course that's a dream. So all I"m asking for is this: how can I get ubunto to load?

regards
redheat..

 p.s.  Ubuntu is installed on the same hard drive as windows xp, but not on the same hard with windows vista.

---

### Post by dannyboy79 on 2007-05-30
ok, well I think you may have made a mistake regarding guided partitioning. I think you are still booting to the vista hard drive because grub should have appeared no matter what if you're booting to the Windows XP disk. Are you sure there wasn't a grub error number? OR you may have had a botched grub install which is suppose to occur during the Ubuntu install which has obviously messed up your master boot record.

This is what I need you to do. Please pop in a live cd and boot it up. then I need you to preform these steps within a terminal. terminal can be found within Programs, Accessories, click on Terminal and it should bring up a command line interface. 

```
sudo fdisk -l
```
this will return all you hard drives and their respective paritions. I think you may have overwritten your windows xp hard drive but I am not sure hence why I am asking to see this output. THen, I want you to do this. As as example of what you will see, I am pasting the output from one of my drives which shows up from fdisk -l command:
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  HTPF
/dev/hdc2              14        1281    10185210   83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

So what this shows me is that it's a 20gb hard drive which is attached to the first ide channel and it's a slave and it's got 4 partitions. Linux goes like this, ide channel 0 would be hda is the drive, then numbers are partitions. Unless it's a SATA drive, then it would be sda, also USB external drives are like this as well (sda). Then the slave drive on the first ide channel would be hdb. then the master drive on the second ide channel would be hdc and so and so forth. I know by looking at the output from my fdisk -l command that I am looking at the master drive on the second ide channel mostly referred to as ide1 because motherboards usually have a ide0 channel. So my parititons are as follow; hdc1 is /boot, hdc2 is /, hdc3 is swap obviously, and hdc4 is my /home.

 So let's just say that yours didn't get screwed up and you have 4 partitions as well because Ubuntu needs a swap partition, so it would've created hdc2 and hdc3 (this is only if you have an IDE drive, if it was a SATA drive it would be sda2 and sda3)
What the object here is is to mount a partition to a folder and see if your stuff is still there which we hope it is. THis is a general way to do it but will differ based on what the fdisk -l command returns.

```
sudo mkdir /media/win1
```
```
sudo mkdir /media/stor1
```

these 2 commands just created folders within the /media folder. Now we'll "mount" the partitions within these folders to see the content of the partition. Windows using drives to show you the stuff stored on the partitions, like C drive and D drive, well linux doesn't do that, it uses "mount" points (or folders) and then you just "mount" the partition that contains the data you want within that folder. So, do this to see if your winxp install is ok as well as your non-os stuff.

```
sudo mount /dev/hdb1 /media/win1
```
now don't forget to use the /dev/hdXY or /dev/sdXY per the fdisk -l command for the  drive that windows xp is installed on and the partitiont that windows xp should be on. I am guessing hdb1 because you stated that it's your 2nd drive and I am assuming that 1 ide channel has 2 drives and the other has 2 optical drives, cdrom and dvdrom are optical drives and they will also get /dev/ place holders but just don't have a number since there is no partitions.
Once you do that, you can go to the places pull down, then go to computer, then a File Manager called Nautilus will open, then just navigate to the /media/win1 folder and pray that you see a file called ntldr, boot.ini and a Program Files folder and what you normally see on your C drive when you're within windows. Then you can do that for the other non-os storage partition using this command
```
sudo mount /dev/hdb4 /media/stor1
```
again, don't forget to make sure that hte hdb4 is correct.
Now look at it thru Nautilus, is your stuff there?

I need you to carefully read thru all this post and answer each and every question I have asked so that I can help. If you post back and I have to ask it again than you're insulting me and I have just wasted over 15 minutes writing this all up for you. So, when you post back, make sure you ahve the output and the answers to my querstions and I can help you from there.

OR

any easy fix to get windows to boot again, would be to just boot to your windows xp cd, then chose the recovery option, then enter this at the command line. first we need to see what drives are mapped where, so you should be able to enter the map command, and it should return what's mounted with which letters. once you find out where your windows xp install is mounted to then issue this command

FIXMBR C:
or whatever drive your windows xp drive is at, you don't want to fixmbr your vista drive with a xp mbr so be careful because I heard they changed this in vista. doing this will at least allow you to boot into windows xp again and we can go from there.

---

### Post by redheat on 2007-05-30
> **dannyboy79 said:**
> If you post back and I have to ask it again than you're insulting me and I have just wasted over 15 minutes writing this all up for you...Shame on Me if I did that :)

 First of all, the word thank you isn't enough for your post dannyboy79, thank you to the umpteenth time, I don't know how much is that in exponent power but it sounds big..

 secondly, before I answer your questions, bear with me for a while to show how my system got mixed up in the first place.

 As I said in the original post I have two 250 Gb WD harddrives. Both of them are connected to two types of SATA ports on my new Gigabyte board. My new Gigabyte motherboard is GA-965P-DS3/S3 which is based on intel's 965P chipsel and it has Intel's Core 2 Due E6600 processor which runs at 2.40 Ghz. Okay here's the gimmick..The motherboard has six SATA ports:

 1. Four Ports controlled by an intel Chipset called ICH8 and they are painted in orange.
 2. Two ports controlled by a chipset made by Gigabyte controller called GSATAII painted in purple. The difference between both of them is that the GSATA ports support RAID and the other four don't. But that's irrelevant since I don't know what RAID is let alone use it. The problem goes about something called AHCI..

 AHCI is a new interface for SATA ports that is supposed to make them run fast and make use of a new technology implemented in hard drives called NCQ. This technology like so many other hardware devices require a driver that needs to be installed while you're still setting up your version of windows, and it differs from one windows version to another. Some windows version like Vista do have the drivers already installed while earlier version require floppy disk and press F6 during their blue screen install. Ok so what has this to do with the linux, not yet, but bear with me a little.

 As I said this new technology could be enabled for both types of SATA controllers, the intel, which is called ICH8 controller, and the GSATA controller through the BIOS. Oh and one more thing, the two SATA ports on the GSATA controller are always made in the form of Master/Slave array blowing any chance for installing the two harddrives on the same controller if you are to install a dual OS on different harddrives which is the type of installation I follow. So this is what I did:

--1--   I installed windows xp on partition C of harddrive 1 or device (sdb) as the partition manager in Ubuntu shows that harddrive, and the non-os stuff was installed on partition G of the same harddrive leaving out of the 250 GB only 20 Gb for the ubuntu OS in the form of unallocated space. This harddrive is connected on the purple or GSATA controller.

--2-- On the second harddrive or (sda), I have windows vista business installed on partition D and other non-os stuff installed on the remainder. This one is connected to the orange intel controller SATA ports.

  I installed windows xp, its xp professional by the way, first and then installed windows vista, and in the bios I set the first hard drive to boot from to be the windows xp harddrive or (sdb).

 Now we come to Ubuntu's installation. In the original post I said that when I restarted the machine after the initial installation it didn't work out, and that was true. So I rebooted into windows vista cd, removed the two partitions the guided ubuntu installation made, and then rebooted again into Ubuntu's live CD and made another fresh installation. But this time I did one more thing, do you know the advanced tab that appears below the pre-installation summary which shows the type of installation, which partition to install to like sda/hd1 and so forth. It turned if you click that advanced tab it will bring up the place where to put your boot loader, and as I read from one of the posts around here: [http://ubuntuforums.org/showthread.php?t=426503&highlight=missing+operating+system+usb](http://ubuntuforums.org/showthread.php?t=426503&highlight=missing+operating+system+usb)

 I found out that the advanced tab show hd0 which means the first drive in this case sda which has windows vista on it, and doesn't have the ubunto installation on it, so I changed that to hd 1 which means the second harddrive or sdb which has both the ubunto and windows xp partition on it. right after the guided installation finished installing the whole thing. I restarted and guess what?

  A LIST OF OPERATING SYSTEMS APPEARED: now as  I recall they were like this:

 Ubuntu with command prompts
Ubuntu+Memtest
Windows xp
windows vista 

 the problem is  clicked on each one of them and it gave me grub 1.5 or 1.2 I don't recall exactly, and it said error. No matter which OS I choose it gave me "something" missing..and then the grub loader error appeared so I guess with that I answered your first question:

> **dannyboy79 said:**
> ok, well I think you may have made a mistake regarding guided partitioning. I think you are still booting to the vista hard drive because grub should have appeared no matter what if you're booting to the Windows XP disk. Are you sure there wasn't a grub error number? OR you may have had a botched grub install which is suppose to occur during the Ubuntu install which has obviously messed up your master boot record

 Right after this I went again and rebooted into ubuntu using the live cd and checked all my directories, and found them all to be intact and nothing of them is lost or deleted and they as you described: 

> **dannyboy79 said:**
> 
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 1 13 104391 83 HTPF
/dev/hdc2 14 1281 10185210 83 Linux
/dev/hdc3 1282 1472 1534207+ 82 Linux swap / Solaris
/dev/hdc4 1473 2434 7727265 83 Linux

So what this shows me is that it's a 20gb hard drive which is attached to the first ide channel and it's a slave and it's got 4 partitions. Linux goes like this, ide channel 0 would be hda is the drive, then numbers are partitions. Unless it's a SATA drive, then it would be sda, also USB external drives are like this as well (sda). Then the slave drive on the first ide channel would be hdb. then the master drive on the second ide channel would be hdc and so and so forth. I know by looking at the output from my fdisk -l command that I am looking at the master drive on the second ide channel mostly referred to as ide1 because motherboards usually have a ide0 channel. So my parititons are as follow; hdc1 is /boot, hdc2 is /, hdc3 is swap obviously, and hdc4 is my /home.

 I mean they were all intact and I even browsed them using nautilus, no change whatsoever. And all the harddrives partitions were "mounted" the moment I pressed fresh devices in the partition manager Ubuntu's desktop space became filled with little harddrives icons bearing the name of all of my partitions on the two harddrives. Good news!! 

 Yet still, I was unable to log in back into any of my windows and each time I try to login back I end up with that retarded grub error. So I rebooted into my vista cd, deleted the partitions I created under ubuntu, and then rebooted again into my windows xp CD opened the recovery console and used that fixmbr command like you said and then rebooted again into my harddisk.....and TA DA ..it worked.. I was faced with the two os choice. I choose windows xp professional and this where I 'm writing back to you from. :popcorn::KS:D

 So when it comes the ubuntu installation it didn't work no matter how I do it, and it only took the command "fixmbr" to restore the windows xp MBR file to the way it was...

 I was thinking of using that new utility Wubi to install Ubuntu from within windows but I have that got feeling its not gonna be as "clean" and manageable as installing ubuntu from the main black screen... you can get it from here:

 [https://launchpad.net/wubi](https://launchpad.net/wubi)

 dannyboy79, thank you so much my friend for your help... I truely appreciate the time and effort you put into writing your reply..waiting for further info from you...

regards and many thanks.
redheat..

---

### Post by dannyboy79 on 2007-05-31
ok, here's my suggestions. Don't go with Wubi, I have no experience with it and  if you do go with it I wouldn't be able to help. I am sure others can help you though BUT I know when i first started using linux, when I had some1's ear that wanted to help, I was going to stick with them until I got my problem resolved. 

Well according to here: [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
there are many problems people are having getting the installer to see their cdrom while installing but it sounds to me like you got it installed but are having an issue with grub. BUT according to that thread, you **should be using all the Intel ICH8 sata ports **and since you don't use RAID, it should matter to you anyway (i am not entirely sure about this as you say that you got it installed on the drive that was hooked to the gsataII port so I don't know if this is a contributing factor or not?). ALso, I found this bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115312](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115312)
which is also preventing people from installing so I want to make sure that this is not the case with you correct? The installler appears as though it works and asks you to remove the cd before restarting correct?
IF SO,
this is what I suggest. The problem is occuring because you installed grub onto hd1's mbr and then chose to boot that disk from the bios BUT for some reason grub couldn't find where you put it's files, they are stage1.5 and stage 2 which completes the boot process and get's you into your os (these are located within /boot/grub/). It also sounds like that since you tried booting windows as well and those didn't work either, your entire menu.lst that grub is automagically creating for ya just isn't working, can't tell you why, I can only help you fix it. 
So this is what I will suggest and I have to tell you that it may give us problems after the install BUT I will walk you thru the procedure to fix it entirely and get you to be able to boot all 3 os's from grubs menu so hang in there.
First, I need to know which drive you'll be booting from in the bios, it's going to have to be the one where we install grub into the mbr.  Then we need to decide which hard drive grub thinks is hd0 and which one it thinks is hd1, I know that you think just because ubuntu told you that the Vista drive is sda that that should be hd0 but sometimes grub reads them differently from the bios than Ubuntu does so we need to verify this. Do this
When you boot into the live cd, I'd like you to do these commands from the terminal
cat /boot/grub/device.map
This should show you something like my output:
(hd0)   /dev/hdb
(hd1)   /dev/hdc
(hd2)   /dev/hdd
(hd3)   /dev/sda
(hd4)   /dev/sdb

So, I am hoping that the live cd has this device.map file somewhere, I haven't worked in a live cd in awhile so I am not sure if there will be one of these files and if there's not, than we can just find out after the install. So if you're going to be sticking with booting the windows xp drive from the bios, than yes, install grub onto hd1 IF that's what the live cd showed and even if it didn't we already know that at least grub is being loaded from the mbr of your win xp disk, it just can't find the rest of it's files.

Ok, so basically what I am saying is that first make sure that all disks are connected to the Intel SATA ports (i think you should do this just in case as you don't use raid, we can rule that problem out) and then boot the live cd and find out which drive is being mapped where within the device.map file that should be located within /boot/grub/. Once you find that out, we now know whether sda is hd0 and so on and so forth.
THen perform the install again and just do what you did before and chose to install grub onto which ever drive you'll be booting from the bios. Then give it a shot BUT I have a feeling it wil fail again because something about grub isn't working correctly and it's not creating your menu.lst correctly.

So this time, if you don't have another computer to boot into and post back, than just leave Ubuntu installed but only fixmbr so that you can boot into Winxp Pro again and post back and tell what happened. When you post back and if it doesn't work after the install again, this is what you should do from a live cd BEFORE you post back to me.
Boot into the live cd, then I want you to chroot into your ubuntu install by doing this
```
sudo mkdir /mnt/root
```
```
sudo mount -t ext3 /dev/sdb2 /mnt/root
```
(NOTE: use the sdXY drive and partition that is correct for whereever the main fiesty install is)
```
sudo mount -t proc none /mnt/root/proc
```
```
sudo mount -o bind /dev /mnt/root/dev
```
```
sudo chroot /mnt/root /bin/bash
```
then enter
```
sudo grub
```
this will take you into the grub command line
```
find /boot/grub/stage1
```
It will return something like (hd1,2), this is where your grub files are located. so do this:
```
root (hd1,2)
```
that's only if the find command finds it at (hd1,2)
```
setup (hd1)
```
that's only if the find command finds it at (hd0)
```
quit
```
will get you out of the grub cli.
Then also, please post the menu.lst file (this is the one that your normal fiestyy will use so we need to fix this one) that's located within /mnt/root/boot/grub/ if it fails so that I can tell you how to fix it.
Good luck!!!!!!

This is an update, I was reading another thread and found that your motherboard will have frequent freezes once you get it installed and working, It's due to the Marvel Ethernet Chip on the motherboard and here is the fix: [http://ubuntuforums.org/showthread.php?p=2370287#post2370287](http://ubuntuforums.org/showthread.php?p=2370287#post2370287)
it's post number 9 that you should follow.

---

### Post by redheat on 2007-06-02
Hi dannyboy79

 Ok to make a long story short, I bought a new harddrive a 320 GB WD caviar, partitioned it into the following scheme:

C:\ Windows XP Pro (sdb1)
E: \ Windows Vista Business (both partition are 80 GB each) (sdb2)
F: Supposedly ubuntu ( this is an extension partition of size 25 GB)..23 are for the Ext3 and the other 2 are swap and they are given the names sdb5 and sdb6 consecutively, and they both fall under the extended partition sdb4 that contains both of them. 
and finally a I have an empty partition of size 133 GB called sdb3 

 all of the above on the same harddrive..

 I installed windows xp, and then installed windows vista, and then went ahead and installed Ubuntu, and choose (hd1) as the main installation location for the boot loader. 

 As expected, the boot menu of GRUB came up with the usual four choices:

Ubuntu 2.6....etc Origianl
Ubuntu (recovery mode)
Ubuntu memtest i86...etc.
Other windows OS (probably windows xp)
Windows Vista (loader) 

 No matter which one I choose the answer was either:

no such partition, missing ntldr or no such device or grub 1.5 error 22.

 so I did as you told me, I fixed the MBR, the vista OS choice window appeared again, and then I rebooted again and went into ubuntu using the live CD.

 Now I typed this:

```
cat /boot/grub/device.map
```

 the reply came back with "no such file or directory"  

 so I followed the the next part of your message: 

```
sudo mkdir /mnt/root
```
```
sudo mount -t ext3 /dev/sdb5 /mnt/root
```
(NOTE) I put sdb5 since this is the original directory where I installed Feisty Frown.
```
sudo mount -t proc none /mnt/root/proc
```
```
sudo mount -o bind /dev /mnt/root/dev
```
```
sudo chroot /mnt/root /bin/bash
```
```
sudo grub
```
```
find /boot/grub/stage1
```
It returned (hd1,4), where my grub files turned out to be installed in stead of 1.5. so I did the following:
```
root (hd1,4)
```
```
quit
```

 Now, I went back and typed the following:
```
cat /mnt/root/boot/grub/device.map
```

 and the answer came out like this:

> 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc


 and for the menu.lst, I typed the following command:

```
cat /mnt/root/boot/grub/menu.lst
```

 and the answer came out like this:

(Watch out this is gonna be a long one, I omitted the tutorial part on how to use the grub menu default options)

> 

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d65c1b70-678d-4212-bf39-0ceb21ee50a5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d65c1b70-678d-4212-bf39-0ceb21ee50a5 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1



 Waiting for further instructions:

regards
redheat...

---

### Post by redheat on 2007-06-03
Dannyboy79

 I hope you're still reading this post, I've reformated the whole drive, and right now I have my new drive my partitioned into the following scheme: (the drive is 320 Gb)

  Partition C: 80 GB reserved for windows XP
  Partition E: Reserved for Windows Vista (also 80 GB)
  Partition F: reserved for Ubuntu (30 Gb)
  Partition G: reserved for non-os files almost 130 GB)

  I've installed Windows XP, and Windows Vista, and I'm waiting for further instructions on how    to install Ubuntu...

 I would truely appreciate any help at all...

regards
redheat..

---

### Post by confused57 on 2007-06-03
> **redheat said:**
> Dannyboy79

 I hope you're still reading this post, I've reformated the whole drive, and right now I have my new drive my partitioned into the following scheme: (the drive is 320 Gb)

  Partition C: 80 GB reserved for windows XP
  Partition E: Reserved for Windows Vista (also 80 GB)
  Partition F: reserved for Ubuntu (30 Gb)
  Partition G: reserved for non-os files almost 130 GB)

  I've installed Windows XP, and Windows Vista, and I'm waiting for further instructions on how    to install Ubuntu...

 I would truely appreciate any help at all...

regards
redheat..
Wait on dannyboy79, but I may be able to offer some insight as to why your system wouldn't boot...you selected to install grub's IPL to your (hd1) mbr, but when you boot first to this drive it, in effect, would be recognized as (hd0) by grub...you could have highlighted your Ubuntu entry in the grub boot menu, pressed "e" to edit, then change root from (hd1,x) to (hd0,x), then press "b" to boot.

As I mentioned, dannyboy79 can help you...I just wanted to put in my couple of cents worth.

Added:  Just saw your new thread, you explained your setup quite nicely...you could probably do a "manual" partitioning, select your / and swap as logical partitions...install grub to (hd1), if this is indeed your drive with the OSes.  From your experience with guided partitioning, you know that root is formatted ext3, set mountpoint as /, logical partition type...swap would be mountpoint & formatted as swap(~1Gb), logical partition...after installing, try the "e" method I've outlined...be interesting to see the replies in your other thread.

---

### Post by redheat on 2007-06-03
> **confused57 said:**
> Wait on dannyboy79, but I may be able to offer some insight as to why your system wouldn't boot...you selected to install grub's IPL to your (hd1) mbr, but when you boot first to this drive it, in effect, would be recognized as (hd0) by grub...you could have highlighted your Ubuntu entry in the grub boot menu, pressed "e" to edit, then change root from (hd1,x) to (hd0,x), then press "b" to boot.

As I mentioned, dannyboy79 can help you...I just wanted to put in my couple of cents worth.

 Confused, your two cents are worth two million to me :D

 I thought of that too, and I let it install to hd0, once, but of no use. Actually, the one time  Ielt it do that it gave me nothing, not even the Grub menu to choose from, but the second time around  I chose hd1 and it was of no use too. It showed me the grub menu, but if I chose any option it either gives me..no such parition, or missing ntldr in case of windows vista, or error 11 or error 22...

 Thanks confused...I'm putting a new post, where everyone get to share in their experiences and answers.

regards
redheat..

---

### Post by dannyboy79 on 2007-06-04
> **redheat said:**
> Confused, your two cents are worth two million to me :D

 I thought of that too, and I let it install to hd0, once, but of no use. Actually, the one time  Ielt it do that it gave me nothing, not even the Grub menu to choose from, but the second time around  I chose hd1 and it was of no use too. It showed me the grub menu, but if I chose any option it either gives me..no such parition, or missing ntldr in case of windows vista, or error 11 or error 22...

 Thanks confused...I'm putting a new post, where everyone get to share in their experiences and answers.

regards
redheat..
well your setup isn't exactly going to work, I hope you made an extended partition for ubuntu and the non-os stuff that's after ubuntu because ubuntu needs 2 partitions, a /  and a swap so that would now be 5 parititons and you're limited to 4 primaries and unlimited logical's which that;'s what get created within the extended area you create. I don't see that you answered of my questions nor commente don what I said in my huge long reply to you so as I said in the very beginning, I won't continue unless you have already done what I suggested and return with waht I asked. sorry if you feel this is un called for but it happens to me way to much where I have to repeatedly ask over and over for the same stuff from some1 and I am not going do it anymore.

 I just noticed that your decided to put Vista and WinXP on the same drive, it can be done with grub by hiding the partitions but I have never actually help someone do it BUT the grub manual is pretty easy to understand so we'll be able  to figure it out BUT as I said, you can't have 2 windows OS's on the same hard drive without hiding them from 1 another. check it out here: [http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)
and then read his grub entries for disk /dev/hdc which is almost half way down within the very first "CODE" box.

---

### Post by redheat on 2007-06-05
> **dannyboy79 said:**
> well your setup isn't exactly going to work, I hope you made an extended partition for ubuntu and the non-os stuff that's after ubuntu because ubuntu needs 2 partitions, a /  and a swap so that would now be 5 parititons and you're limited to 4 primaries and unlimited logical's which that;'s what get created within the extended area you create. I don't see that you answered of my questions nor commente don what I said in my huge long reply to you so as I said in the very beginning, I won't continue unless you have already done what I suggested and return with waht I asked. sorry if you feel this is un called for but it happens to me way to much where I have to repeatedly ask over and over for the same stuff from some1 and I am not going do it anymore.

 I just noticed that your decided to put Vista and WinXP on the same drive, it can be done with grub by hiding the partitions but I have never actually help someone do it BUT the grub manual is pretty easy to understand so we'll be able  to figure it out BUT as I said, you can't have 2 windows OS's on the same hard drive without hiding them from 1 another. check it out here: [http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)
and then read his grub entries for disk /dev/hdc which is almost half way down within the very first "CODE" box.

 Dannyboy79, first of all, it would be shame on my side if I did not thank for your help you spent writing replies to this post, but at the same time I feel obligated to answer your accusation to me for not answering " any"  of your comments or questions:

 1. In your first reply to my original first post, you, in detail that is, were explaing to me, thankfuly,  what hd0 and sda..etc, and then you moved on to how " mount"  and broswer my harddrives using nautilus, and yet thankfuly, I answered in post following it, saying that I'm capable of browsing my system using nautilus, and that all my drives were already mounted without having to create a directory for windows. Yet thank you again for that post.

2. On the post following it, you gave a series of commands on how to check where the grub is and how to set it up in order for the grub to see the rest of its files, and in the post following it, I answered with a quoatation from your post with a reply accompanied along with the results. Also I'm thanful and grateful for that.

 In my last post, which Confused57 replied to it graciously, I thought why not make things easier by reformatting my whole drive and partitioning it into three pirmary drive and leaving the unallocated space for ubuntu to make the best use out of it. 

 Yet in this reply you say, I did not answer any of your questions or comments though I did both verbally and with code quotes.

 yet again, I'm thanful, and I don't wanna bug you more with my posts or questions. and finally, you said that  I cannot create more than four primary partitions, but isn't the extended partition considered a parimary with different logical dries... because in all cases I cannot create two primaries for the "/" part and the swap, I mean, I have to create an extended parition if I want to make use of the 120 GB left.?! and that's exactly what gparted pointed my attention to..when I first came across this problem. The help file showed me that I can create and extended parition for the ubuntu filesystem and linux and the left space could be considrered as primary. 

 anyhow thank you thank you and one more time thank you for your help, and I'm sorry if I couldn't achieve or communicate clearly what you've requested of me..I thank you again for your help, and I've learned a lot from what you told me to do. Yet again, I'm a whole noob to this linux language..yet I cherish, in my own sheepish way, what I've achieved so far...

regards and many thanks
redheat.

---

### Post by dannyboy79 on 2007-06-07
> **redheat said:**
> Dannyboy79, first of all, it would be shame on my side if I did not thank for your help you spent writing replies to this post, but at the same time I feel obligated to answer your accusation to me for not answering " any"  of your comments or questions:

 1. In your first reply to my original first post, you, in detail that is, were explaing to me, thankfuly,  what hd0 and sda..etc, and then you moved on to how " mount"  and broswer my harddrives using nautilus, and yet thankfuly, I answered in post following it, saying that I'm capable of browsing my system using nautilus, and that all my drives were already mounted without having to create a directory for windows. Yet thank you again for that post.

2. On the post following it, you gave a series of commands on how to check where the grub is and how to set it up in order for the grub to see the rest of its files, and in the post following it, I answered with a quoatation from your post with a reply accompanied along with the results. Also I'm thanful and grateful for that.

 In my last post, which Confused57 replied to it graciously, I thought why not make things easier by reformatting my whole drive and partitioning it into three pirmary drive and leaving the unallocated space for ubuntu to make the best use out of it. 

 Yet in this reply you say, I did not answer any of your questions or comments though I did both verbally and with code quotes.

 yet again, I'm thanful, and I don't wanna bug you more with my posts or questions. and finally, you said that  I cannot create more than four primary partitions, but isn't the extended partition considered a parimary with different logical dries... because in all cases I cannot create two primaries for the "/" part and the swap, I mean, I have to create an extended parition if I want to make use of the 120 GB left.?! and that's exactly what gparted pointed my attention to..when I first came across this problem. The help file showed me that I can create and extended parition for the ubuntu filesystem and linux and the left space could be considrered as primary. 

 anyhow thank you thank you and one more time thank you for your help, and I'm sorry if I couldn't achieve or communicate clearly what you've requested of me..I thank you again for your help, and I've learned a lot from what you told me to do. Yet again, I'm a whole noob to this linux language..yet I cherish, in my own sheepish way, what I've achieved so far...

regards and many thanks
redheat.
My point was that everything I had written out was based on a certain hard drive configuration and what would go where and then you completely changed that by not using 2 drives anymore. There's nothing wrong with that but my instructions are not good for that. 

When you were doing the step about finding grub's files and installing grub to a certain drive, you didn't do the most important one, the setup (hd1), you only did the root (hd1,4) part of it. 

The other MAJOR problem is that you can't install grub's files to far out on the disk and it appears that you are since you're getting that error about invalid partition. Basically I am saying, that if you want my help again, I'll need to know more specifically about what you want to do. You made a comment that you started a new thread so people could see it? I don't really understand why, people won't be able to see that one any better than this one? Also, if and when you do that, you should really paste the link so people know where to go. 

Didn't you notice that when you did the Ubuntu install, it only put 1 entry for your Winbloz Vista install, that's because it's going to boot into NTLDR, not the OS, (i believe anyway) so when you pick Vista from grub, it'll boot to windows boot loader, then you can either pick XP or Vista, I am not sure if you want it that way, I wouldn't anyway. You have to use the hide and unhide options if you want grub to be able to boot both of them so that you don't have to use NTLDR or whatever Vista's new boot loader is. 

I would strongly sugggest creating a boot partition as the first 100 megabytes of the disk. then have WinXP, then have Vista, then have your NON-OS parititon, then leave the rest UNALLOCATED for ubuntu. Then when it asks where you want to install grub, you'll still chose to install it into the MBR, but it will point to the /boot directory, which will be mounted on Parititon 1 (the first 100mb of the disk), your parititon 2 will be WinXP, your 3rd will be Vista, then the 4primary will ahev to be an Extended partition, then the 5 will be your NON-OS stuff, then the 6 will be / and then 7 will be /swap.

The other reason I said you didn't answer my questions was because I was asking you about whether you  had issues with the live cd booting up and exactly what occured during the install and you didn't answer me. I believe there were other questions  or comments that I made which more or less required a comment or answer back from you but it's a moot point at this stage, I wouldn't have written that you didn't answer my questions or comments if you did. It's not worth arguing about, you say you answered all them, I say you didn't, no big deal, we'll agree to disagree. :-)

 Many people with the same or similar motherboard as you are having a hell of a time. I would be happy to help you if you still need it, just let me know where the link is.

---

### Post by redheat on 2007-06-07
> **dannyboy79 said:**
> My point was that everything I had written out was based on a certain hard drive configuration and what would go where and then you completely changed that by not using 2 drives anymore. There's nothing wrong with that but my instructions are not good for that. 

When you were doing the step about finding grub's files and installing grub to a certain drive, you didn't do the most important one, the setup (hd1), you only did the root (hd1,4) part of it. 

The other MAJOR problem is that you can't install grub's files to far out on the disk and it appears that you are since you're getting that error about invalid partition. Basically I am saying, that if you want my help again, I'll need to know more specifically about what you want to do. You made a comment that you started a new thread so people could see it? I don't really understand why, people won't be able to see that one any better than this one? Also, if and when you do that, you should really paste the link so people know where to go. 

Didn't you notice that when you did the Ubuntu install, it only put 1 entry for your Winbloz Vista install, that's because it's going to boot into NTLDR, not the OS, (i believe anyway) so when you pick Vista from grub, it'll boot to windows boot loader, then you can either pick XP or Vista, I am not sure if you want it that way, I wouldn't anyway. You have to use the hide and unhide options if you want grub to be able to boot both of them so that you don't have to use NTLDR or whatever Vista's new boot loader is. 

I would strongly sugggest creating a boot partition as the first 100 megabytes of the disk. then have WinXP, then have Vista, then have your NON-OS parititon, then leave the rest UNALLOCATED for ubuntu. Then when it asks where you want to install grub, you'll still chose to install it into the MBR, but it will point to the /boot directory, which will be mounted on Parititon 1 (the first 100mb of the disk), your parititon 2 will be WinXP, your 3rd will be Vista, then the 4primary will ahev to be an Extended partition, then the 5 will be your NON-OS stuff, then the 6 will be / and then 7 will be /swap.

The other reason I said you didn't answer my questions was because I was asking you about whether you  had issues with the live cd booting up and exactly what occured during the install and you didn't answer me. I believe there were other questions  or comments that I made which more or less required a comment or answer back from you but it's a moot point at this stage, I wouldn't have written that you didn't answer my questions or comments if you did. It's not worth arguing about, you say you answered all them, I say you didn't, no big deal, we'll agree to disagree. :-)

 Many people with the same or similar motherboard as you are having a hell of a time. I would be happy to help you if you still need it, just let me know where the link is.

 Dannyboy79, believe it or not I didnot right setup hd1 for the following reason, remember the last time you told me to use the find command to locate where the grub was installed and it turned out to be (hd1,4) and then you asked me to setup hd 1 and then you followed it with this command which got the whole thing messed up in my mind, you said after you asked to setup hd1, "if the find command returned hd0" and then you asked me to type quit. 

 The main reason I moved on to a single harddrive, is to avoid distributing the OS' over multiple harddrives, but you know what I should have done that from the beginning if you noticed ilya's comment on his blog [http://hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)  (you'll notice he took all the harddrives out and then proceeded to install the operating systems on it) which is a good idea by the way and I'll tell you why.

 because all of my harddrives are SATA,  I wanted to enjoy SATA  to the most so I turned AHCI on both controllers, this shouldn't be a problem, but it turned out that there was actually a problem. The harddrive installed on the ICH8 (intel's controller) would always be reported as (hd0) and the others installed on the GSATA controllers would always be reported as (hd1 and hd2). But the question should be why? why is the harddrives installed on ICH8 controller should be reported with precedence and those installed on the GSATA should come second. For example suppose I installed two SATA harddrives on intel's controllers and two on GSATA's two sata ports they would be reported like this:
(hd0=sda, hd1=sdb) the ones on intel's, and then (hd2=sdc, hd3=sdd) for the two installed on GSATA. 

 And to be more frank, there's a great deal of argument going on among the Motherboard community if ICH8 does in actuality support AHCI, though intel has released a statement saying it does, they call it ICH8 vanilla, maybe they're craving ice-cream :p , and all other types like ICH8R/H/HH/HO (ho what were they thinking) and M..etc do support it especially in later motherboard versions like GA-965p-QS4..and so forth do have drivers for that. So I wanted to install the system on harddrive that is connected to the only SATA port that does actually support AHCI, the GSATA ports in this case, and since I had three harddrives, and two GSATA ports, a harddrive had to be installed on the intel ports, and no matter what that one does seem always to be noticed as I explained before as (hd0), and quite frankly, and this is only my conjecture about the whole thing, ubuntu feels happy if you installed it on a hd0 drive nothing else beside that. 

 That's the whole story behind using a single drive with three operating systems connected to gsata. I mean guess what, though when I installed all the systems on this harddrive as hd0, since it was the only one connected at the time, after I reconnected all harddrives back, it became hd1..and that connected to intel's sata port became automatically as hd0...

 I know the configuration of booting from a loader rather from the OS doesn't fit with your highly technical sense of irony..then excuse me..I mean excuse me :D  that's the best a new noob in linux can do for now on..

 Oh one more thing,  if you thought berating me is gonna get you off the hook, then you're wrong mr. linux-my-middle-name dude..:) 

 I need you to help me with one thing:

1. I have an nvidia 8600GT video card that I'm trying to install drivers for it, but I could not find a single decent easy to follow guide out there, I found that italian dude's guide on how to install nvidia, and I even downloaded the driver for it which is 100.14.06, but it didn't open well, which cost me to reinstall my whole os again.. can you help me with this please?

 Thanks dannyboy79 for replying

regards
redheat

---

### Post by dannyboy79 on 2007-06-07
> **redheat said:**
>  Dannyboy79, believe it or not I didnot right setup hd1 for the following reason, remember the last time you told me to use the find command to locate where the grub was installed and it turned out to be (hd1,4) and then you asked me to setup hd 1 and then you followed it with this command which got the whole thing messed up in my mind, you said after you asked to setup hd1, "if the find command returned hd0" and then you asked me to type quit.  
I have no idea what you're saying here as it's kind of hard to follow? My instructions would have worked for athe hard drive setup that you had initially. The goal was to find what the device.map mapped the drives to, and then installl grub into the disk that you were booting from the bios. It wasn't hard, you gave up to early.
> **redheat said:**
> 
 The main reason I moved on to a single harddrive, is to avoid distributing the OS' over multiple harddrives, but you know what I should have done that from the beginning if you noticed ilya's comment on his blog [http://hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)  (you'll notice he took all the harddrives out and then proceeded to install the operating systems on it) which is a good idea by the way and I'll tell you why. 
as I said, you gave up to early, many many people have multi-hard drive installs with many many os's, more than 3. I linked you to a guy that boots over 100+ os's from 4 hard drives and hundreds of partiitions. Oh well, you wanted to do it a different and that's fine, it's your system but that's why my instructions didn't work for you.
> **redheat said:**
> 
 because all of my harddrives are SATA,  I wanted to enjoy SATA  to the most so I turned AHCI on both controllers, this shouldn't be a problem, but it turned out that there was actually a problem. The harddrive installed on the ICH8 (intel's controller) would always be reported as (hd0) and the others installed on the GSATA controllers would always be reported as (hd1 and hd2). But the question should be why? why is the harddrives installed on ICH8 controller should be reported with precedence and those installed on the GSATA should come second. For example suppose I installed two SATA harddrives on intel's controllers and two on GSATA's two sata ports they would be reported like this:
(hd0=sda, hd1=sdb) the ones on intel's, and then (hd2=sdc, hd3=sdd) for the two installed on GSATA. 

 And to be more frank, there's a great deal of argument going on among the Motherboard community if ICH8 does in actuality support AHCI, though intel has released a statement saying it does, they call it ICH8 vanilla, maybe they're craving ice-cream :p , and all other types like ICH8R/H/HH/HO (ho what were they thinking) and M..etc do support it especially in later motherboard versions like GA-965p-QS4..and so forth do have drivers for that. So I wanted to install the system on harddrive that is connected to the only SATA port that does actually support AHCI, the GSATA ports in this case, and since I had three harddrives, and two GSATA ports, a harddrive had to be installed on the intel ports, and no matter what that one does seem always to be noticed as I explained before as (hd0), and quite frankly, and this is only my conjecture about the whole thing, ubuntu feels happy if you installed it on a hd0 drive nothing else beside that. 

 That's the whole story behind using a single drive with three operating systems connected to gsata. I mean guess what, though when I installed all the systems on this harddrive as hd0, since it was the only one connected at the time, after I reconnected all harddrives back, it became hd1..and that connected to intel's sata port became automatically as hd0.. .
Agreed
> **redheat said:**
> 
 I know the configuration of booting from a loader rather from the OS doesn't fit with your highly technical sense of irony..then excuse me..I mean excuse me :D  that's the best a new noob in linux can do for now on...
As I said, it's your computer, you can do it however you like.

> **redheat said:**
> 
 Oh one more thing,  if you thought berating me is gonna get you off the hook, then you're wrong mr. linux-my-middle-name dude..:) 

 I need you to help me with one thing:

1. I have an nvidia 8600GT video card that I'm trying to install drivers for it, but I could not find a single decent easy to follow guide out there, I found that italian dude's guide on how to install nvidia, and I even downloaded the driver for it which is 100.14.06, but it didn't open well, which cost me to reinstall my whole os again.. can you help me with this please?

 Thanks dannyboy79 for replying

regards
redheat 
Ok, you need to use the latest unstable Envy and do the manual install of the latest nvidia driver BUT you'll always get the API mismatch error. The only way around it is a hack which some1 else instructed me how to do it, it's here: [http://ubuntuforums.org/showthread.php?t=432056&page=5](http://ubuntuforums.org/showthread.php?t=432056&page=5)
just read thread number 50 and you should be set. Good luck!

PS (Linux isn't my middle name, I have only been on it for less than 18 months (ubuntu only). I merely view many many threads and read many forums and mess around with stuff and am not afraid to break it. If it breaks, I don't reinstall, I figure out how to fix it. That's what's gotten me a pretty descent knowledge base of the linux basics)

---

