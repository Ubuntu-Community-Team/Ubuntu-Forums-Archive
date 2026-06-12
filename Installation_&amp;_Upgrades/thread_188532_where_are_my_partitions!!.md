---
title: "where are my partitions!!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by adityavb on 2006-06-04
I booted the intallation+live cd
It came up with proper Gnome desktop ...
I started the installation program
But it did not detect any partitions on my first HDD
here is my fdisk output ....

> 255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         638     5124703+   b  W95 FAT32
/dev/hda2             639        1275     5116702+  83  Linux
/dev/hda3            1276        4865    28836675    f  W95 Ext'd (LBA)
/dev/hda4            1914        3591    13478503+   b  W95 FAT32
/dev/hda5            1276        1318      345334+  82  Linux swap / Solaris
/dev/hda6            1319        1913     4779306    c  W95 FAT32 (LBA)
/dev/hda7            3592        4865    10233373+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1305    10482381   83  Linux
/dev/hdb2            1306        9733    67697910    f  W95 Ext'd (LBA)
/dev/hdb5            1306        3916    20972826    b  W95 FAT32
/dev/hdb6            3917        6527    20972826    b  W95 FAT32
/dev/hdb7            6528        9688    25390701    b  W95 FAT32
/dev/hdb8            9689        9733      361431   82  Linux swap / Solaris


I want to keep /hda2 as my root partition
/hda1 has Xp installed..
/hdb1 has fedora 5 on it and the GRUB is on the MBR of /hda

The installer detects all the partitions on /hdb but it says my whole /hda is "unallocated":confused: 

I was still able to select /dev/hda2   for "/"  i.e root 
but the installer said "No root file system" :mad: :mad: 

Please help.....****

---

### Post by majed on 2006-06-04
i don't know why, but i would trust more an alternate CD with the good old text based installer..

---

### Post by adityavb on 2006-06-04
well I thought of that ...but is there nothing that can be done from this CD??:confused: ](*,) :-k

---

### Post by ubuntu_demon on 2006-06-04
WARNING / take a look here prior to upgrading and installing! :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

try the alternate install cd or try this :
[http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2)

---

### Post by rcarring on 2006-06-04
The Live CD is designed primarily for simple install to whole hard disk or possibly a resize of the C drive.

For users with more complex partitioning schemes, refer to the guides posted above, and I would suggest use of the alternate install cd.

---

### Post by adityavb on 2006-06-04
Well I tried to use Gnome Partition Manager from the Live CD , but that too failed to detect my existing partitions on "hda" . When I still tried to create new partitions on it, it said that there is no disklabel , and a new disklabel will have to be written , and it will erase the whole of my HDD .(ie hda) . So I aborted it. 

Man this is a serious bug I think and the developers should have fixed this , as I read somewhere that this bug was present in pre-release versions too.

After reading so many positive reviews of Ubuntu , I really wnat to try it ..guess I ll have to wait a  bit more...till I finish downloading the alternate CD. Lets see how that goes.

---

### Post by rcarring on 2006-06-04
It looks like your Fedora install has placed Swap in the extended partition of a disk formerly formatted into several drives with fat32.

It also looks like the XP install drive has similarly got Linux swap in the extended partition.

You would use the alternate cd and manually edit the partitions.

I assume that you have some kind of bootloader installed to dual boot presently between XP and FC?

---

### Post by Mirrorball on 2006-06-04
Here I am, using the live CD, and I can't install Dapper because my partition table wasn't detected. :( It's weird, running ls /dev/hda* lists all my partitions. Also:

```

ubuntu@ubuntu:~$ fdisk /dev/hda

Unable to open /dev/hda

```

---

### Post by Mirrorball on 2006-06-04
I can't install Dapper, because my partition table isn't detected by the text mode installer either. What do I do? It's just an ordinary ATA hdd.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=Mirrorball]I can't install Dapper, because my partition table isn't detected by the text mode installer either. What do I do? It's just an ordinary ATA hdd.[/QUOTE]
Start gparted from the livecd. It may have gotten a different name (for example /dev/hde).

---

### Post by adityavb on 2006-06-05
Well people I tried with the alternate CD too , its the same problem. 

Yes I have installed  GRUB on the MBR of /dev/hda to boot into fedora and XP. 

The biggest joke is that ,on  the  partition which I want to use ie. hda2 , there is ARK linux installed which I dont use. Previous to ARK , Ubuntu Breezy was installed on the same partition and running fine . I dont understand what the problem is with that drive of mine!

I even mounted /dev/hda2 from the live CD and was able to see its contents!

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=adityavb]Well people I tried with the alternate CD too , its the same problem. 

Yes I have installed  GRUB on the MBR of /dev/hda to boot into fedora and XP. 

The biggest joke is that ,on  the  partition which I want to use ie. hda2 , there is ARK linux installed which I dont use. Previous to ARK , Ubuntu Breezy was installed on the same partition and running fine . I dont understand what the problem is with that drive of mine!

I even mounted /dev/hda2 from the live CD and was able to see its contents![/QUOTE]
Maybe this helps. I don't know :
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)

---

### Post by Mirrorball on 2006-06-05
[quote=ubuntu_demon]Start gparted from the livecd. It may have gotten a different name (for example /dev/hde).[/quote] No, because it says that my drive has 189 GB of unallocated space. But it doesn't display its partition table, which I created on Gentoo, and it only has Linux partitions in it. Both gparted and the text mode installer in the alternative CD act as if my hdd were empty.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=Mirrorball]No, because it says that my drive has 189 GB of unallocated space. But it doesn't display its partition table, which I created on Gentoo, and it only has Linux partitions in it.[/QUOTE]

You ran fdisk from the desktop cd but you forgot to use sudo. It's :
$sudo fdisk *devicename*

Are you sure the Dapper desktop cd detected your harddrive as /dev/hda ?  In breezy my harddrive was /dev/hda. In dapper it has become /dev/hde Although when updating grub it gets changed to /dev/hda. This is a common problem. Here's some information regarding that issue :
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)

Did you make a backup of the partition table ?(I never do but IMHO it's a wise thing to do)

---

### Post by Mirrorball on 2006-06-05
When I saw that my partition table wasn't being displayed, I canceled the installation. I went back to Gentoo, everything was OK. Ubuntu didn't mess up anything.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=Mirrorball]When I saw that my partition table wasn't being displayed, I canceled the installation. I went back to Gentoo, everything was OK. Ubuntu didn't mess up anything.[/QUOTE]
I've editted my above post :)

---

### Post by Mirrorball on 2006-06-05
I only have one hdd and the installer detected it. It showed it as /dev/hda, 200GB, empty partition table. All the space was marked as unallocated.

---

### Post by Mirrorball on 2006-06-05
Baffling, isn't it? I just tried the CD on a few computers at work and the CD detected their partition tables perfectly. It doesn't like my home computer though, which is the only computer that I want to install Dapper on.

---

### Post by Mirrorball on 2006-06-05
Doesnt anyone have a solution to my problem? Or at least doesnt anyone have the same problem?

---

### Post by Mirrorball on 2006-06-06
Here is a screenshot of gparted. My disk is indeed /dev/hda.

[IMG]http://img.photobucket.com/albums/v479/mirrorball/snif.png[/IMG]

Disk Manager, though, displays all partitions. I even mounted one of them.

---

### Post by SizzleBeast on 2006-06-06
Exactly the same for me, although, i have six different partitions. (2 for windows, with an EXT 3 for ubuntu, with a extended windows and 2 logical linux from under that). Could that have caused a problem with gparted?

Btw, sorry, i dont mean to seem to be hijacking the thread, just a possible part of the problem.

One other note: I had decided to reformat the partitions in the live installer because they were not recognized by ubuntu (i partition them in windows), but then, when i go to try and click on install, the icon dissapears from the desktop. I've went through the menus, and i get and error (i can't remember it off the top of my head). It seems to me as if ubuntu is dependent on the drive that i have partitioned, before it is installed.

---

### Post by adityavb on 2006-06-06
Well Mr. Mirrorball ... I had the same situation as you have shown in your screenshot. 

I finally got it solved. If you carefully see the fdisk output I posted in my first post , there is an overlapping or cylinders in two partitions . Due to this error all the partition managers in Linux were showing the drive as empty. Even in XP , Partition Magic 8 showed the dive as empty just like Gparted , and the windows control panel app showed my 40GB hdd as 59GB HDD . There lay the error . So I deleted all the partitions except /dev/hda1 on my first HDD , and then used Partition Magic Doctor to recover those drives and also thus corrected the wrong cylinder numbers. 

After this the Ubuntu dapper install went just perfect  from the alternate CD. 

A little more investigation revealed  that the XP Installer had scrwed my partition table when my brother had reinstalled XP after a serious virus/spyware infection. 

So people beware of this bug in XP Installer. I have to keep a copy of XP so that my local internet provider can debug it when the connection goes down, he cant use Linux at all.

---

### Post by Mirrorball on 2006-06-06
[quote=adityavb]Well Mr. Mirrorball ... I had the same situation as you have shown in your screenshot.[/quote]

Miss Mirrorball. :p

[quote=adityavb]A little more investigation revealed  that the XP Installer had scrwed my partition table when my brother had reinstalled XP after a serious virus/spyware infection.[/quote]

I had installed XP recently to play a stupid game I got tired of in two weeks, and that was what probably screwed by hdd, according to your post. Thanks for the info, I'm going to try and fix it using your instructions. I hope it works.

---

### Post by Mirrorball on 2006-06-06
[QUOTE=adityavb]Well Mr. Mirrorball ... I had the same situation as you have shown in your screenshot. 

I finally got it solved. If you carefully see the fdisk output I posted in my first post , there is an overlapping or cylinders in two partitions . Due to this error all the partition managers in Linux were showing the drive as empty. Even in XP , Partition Magic 8 showed the dive as empty just like Gparted , and the windows control panel app showed my 40GB hdd as 59GB HDD . There lay the error . So I deleted all the partitions except /dev/hda1 on my first HDD , and then used Partition Magic Doctor to recover those drives and also thus corrected the wrong cylinder numbers. 

After this the Ubuntu dapper install went just perfect  from the alternate CD. 

A little more investigation revealed  that the XP Installer had scrwed my partition table when my brother had reinstalled XP after a serious virus/spyware infection. 

So people beware of this bug in XP Installer. I have to keep a copy of XP so that my local internet provider can debug it when the connection goes down, he cant use Linux at all.[/QUOTE]
Could you please show me the overlapping in your fdisk output? I looked at it again and again and I couldn't find the wrong partitions.

---

### Post by Mirrorball on 2006-06-06
I backed up my Gentoo installation and deleted all the partitions except /home. Now I'm installing Ubuntu! It worked! It's at 54% now. ;)

---

### Post by adityavb on 2006-06-06
[QUOTE=Mirrorball]Could you please show me the overlapping in your fdisk output? I looked at it again and again and I couldn't find the wrong partitions.[/QUOTE]

this is the fdisk ouptput for my first HDD I posted in my first post....

> 255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 638 5124703+ b W95 FAT32
/dev/hda2 639 1275 5116702+ 83 Linux
**/dev/hda3 1276 4865 28836675 f W95 Ext'd (LBA)**
**/dev/hda4 1914 3591 13478503+ b W95 FAT32**
/dev/hda5 1276 1318 345334+ 82 Linux swap / Solaris
/dev/hda6 1319 1913 4779306 c W95 FAT32 (LBA)
/dev/hda7 3592 4865 10233373+ b W95 FAT32



If you can see the entry for my extended partition , it says cylinder 1276 to cylinder 4865 .

so , a partition from 1914 to 3591 (ie hda4 shown above) should be  a logical partition inside this extended partition. But the partition hda4 above , from 1914 to 3591 is listed as a primary partition . 

So cylinders 1914 to 3591 were being counted twice causing the windoze partition manager to report my 40GB HDD as 59GB hdd. , and Gparted to not detect any partitions at all. Screw M$ and Winblows.

---

### Post by Mirrorball on 2006-06-06
Now I see it, thanks. I'm angry at M$ too, although I didn't lose much by deleting those partitions. Fortunately I had the space to back up my Gentoo installation in my /home partition. Posting from Dapper. :)

---

### Post by rcarring on 2006-06-07
Um, it looks more like a corrupt file allocation table, remember the extended partition is just a primary partition that can be divided into logical drives.

But note if a drive partition is of a type that cannot be seen (try it some time with an original 95 fdisk where you have fat32 partitions and fat16 partition in logical it will see the fat16 drive as C:\) then this may cause the drives to be moved about.

---

### Post by deaftoned on 2006-07-31
> **adityavb said:**
> Well Mr. Mirrorball ... I had the same situation as you have shown in your screenshot. 

I finally got it solved. If you carefully see the fdisk output I posted in my first post , there is an overlapping or cylinders in two partitions . Due to this error all the partition managers in Linux were showing the drive as empty. Even in XP , Partition Magic 8 showed the dive as empty just like Gparted , and the windows control panel app showed my 40GB hdd as 59GB HDD . There lay the error . So I deleted all the partitions except /dev/hda1 on my first HDD , and then used Partition Magic Doctor to recover those drives and also thus corrected the wrong cylinder numbers. 

After this the Ubuntu dapper install went just perfect  from the alternate CD. 

A little more investigation revealed  that the XP Installer had scrwed my partition table when my brother had reinstalled XP after a serious virus/spyware infection. 

So people beware of this bug in XP Installer. I have to keep a copy of XP so that my local internet provider can debug it when the connection goes down, he cant use Linux at all.


man, been having the exact problem, but what is partition magic doctor? i have partition magice but it is even giving me this init error 117 message. it is not even starting. i have to fix this it is killing me. help?

---

### Post by adityavb on 2006-07-31
this small utility fixes any errors such as mine in the partition table....use it to rectify your partiton table..then install Ubuntu.

---

### Post by hayati on 2006-08-25
thank a lot this may help very much.

---

### Post by monti on 2007-04-06
I have a similar problem, gparted and the ubuntu installer doesn't detect my partitions.  All other partition application I have tried (windows and linux) shows the partitions like it should.

What to do?  I created a new thread before I saw this one, look there for more info: [http://ubuntuforums.org/showthread.php?t=402872](http://ubuntuforums.org/showthread.php?t=402872)

---

### Post by monti on 2007-04-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gparted/+bug/48412](https://launchpad.net/ubuntu/+source/gparted/+bug/48412) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **monti said:**
> I have a similar problem, gparted and the ubuntu installer doesn't detect my partitions.  All other partition application I have tried (windows and linux) shows the partitions like it should.

What to do?  I created a new thread before I saw this one, look there for more info: [http://ubuntuforums.org/showthread.php?t=402872](http://ubuntuforums.org/showthread.php?t=402872)

This issue really seems to be a libparted issue:

[http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/50](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/50)

---

### Post by sunset blvd. on 2007-04-19
I may have found a solution (I had a similar problem). I explained in this post: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121)

I hope this helps.

---

