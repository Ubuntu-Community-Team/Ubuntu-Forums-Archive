---
title: "Installing WIndows after Ubuntu"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Nico0020 on 2008-08-21
I've been using Ubuntu since Dapper and Love it.  Long story short something has happened to my windows partition and after a few weeks of trying to fix it I gave up.  I have been wanting to redo my partitions for awhile anyways so this gives me an excuse.  

I have been researching trying to figure out if it is possible for me to install ubuntu first?  Every situation I have read is the other way around (which makes the most sense of course)  It would be much easier to manage my windows partition by setting up the space for it then installing it in that last.  Thanks!

---

### Post by willix on 2008-08-21
I'm trying to do the same and must get it working for this weekend so any quick help will be greatly appreciated.

I booted up with a windows installation cd, and all went more or less ok until when windows needed to restart. It screwed up my boot loader and gave me a 'invalid partition table' error and stoped.

I has to reinstalld the grub first stage loader from an ubuntu live cd in order to get back into my ubuntu system.

When browsing the NTFS partition, I only see a WINDOWS directory (no Program Files or Documents and Settings) so obvisously the install did not finished.

Anyone have a clue to what needs to be done?

PS When I installed Ubuntu for the first time (some time ago using edgy), I swiped everything out of the beast and created a fresh partition table. Does ubuntu and windows have a different mecanisme of creating a partition table?

---

### Post by willix on 2008-08-21
A little more info
I tried running PartitionMagic and this is what it has to say

> 
PowerQuest PartitionMagic has found an extended partition on disk 1 that crosses th 1024 cyinder boundary and is not marked as an Extended partition.

This condition can cause data corruption on this disk.


and it offers me to fix the problem and reboot to reinitialize the file system drivers.

I'm a little worried to answer yes as I havn't made a bakup yet :( Could someone tell me if this can potentialy screw up my partition table in such a way that I can't reboot into ubuntu?


this is the outpu of sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeede9d79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+   6  FAT16
/dev/sda2               5         514     4096575   82  Linux swap / Solaris
/dev/sda3             515        3064    20482875   83  Linux
/dev/sda4   *        3065        9729    53536612+   5  Extended
/dev/sda5            3065        4976    15358139+  83  Linux
/dev/sda6            4977        6843    14996646    7  HPFS/NTFS
/dev/sda7            6844        9729    23181763+  83  Linux

---

### Post by willix on 2008-08-21
After rereading my last post I noticed I had two bootable partitions (the little *).

I removed the boot flag on /dev/sda1 and relaunch the windows installed process but it failed again and when I look at the output of fdisk, it has two bootable partitions again.

Don't know what to do next...

---

### Post by guywithcable on 2008-08-21
What is the FAT16 partition for?

---

### Post by guywithcable on 2008-08-21
It looks like you're trying to boot Windows from an extended partition, which I don't believe is possible.

---

### Post by guywithcable on 2008-08-21
> **Nico0020 said:**
> I've been using Ubuntu since Dapper and Love it.  Long story short something has happened to my windows partition and after a few weeks of trying to fix it I gave up.  I have been wanting to redo my partitions for awhile anyways so this gives me an excuse.  

I have been researching trying to figure out if it is possible for me to install ubuntu first?  Every situation I have read is the other way around (which makes the most sense of course)  It would be much easier to manage my windows partition by setting up the space for it then installing it in that last.  Thanks!

It is possible to install Ubuntu first, but Windows installation will erase Grub, and the Window boot loader doesn't understand anything other than Windows, so you'll need to reinstall Grub after you install Windows.

---

### Post by sandysandy on 2008-08-21
> **Nico0020 said:**
> I've been using Ubuntu since Dapper and Love it.  Long story short something has happened to my windows partition and after a few weeks of trying to fix it I gave up.  I have been wanting to redo my partitions for awhile anyways so this gives me an excuse.  

I have been researching trying to figure out if it is possible for me to install ubuntu first?  Every situation I have read is the other way around (which makes the most sense of course)  It would be much easier to manage my windows partition by setting up the space for it then installing it in that last.  Thanks!

have a look at this tutorial on installing XP after Ubuntu.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

also post snapshots of ur partitions from gparted.

regards

---

### Post by DavidTangye on 2008-08-21
Correct me if I am wrong someone, but I believe this is the safest easiest way to install windows then linux:

[LIST=1]
[*]Boot the linux installer in expert mode first (eg from the Ubuntu Alt CD or netboot etc), go just as far as the part about setting up partitions and do so. Set them manually to whatever you want eg partition 1 for windows, other primary and/or extended partitions for linux root, and swap. Then stop the install and reboot. So far you just have a disk partitioned the way you want it.
[*]Boot the windows CD. Install to partition 1 as defined above (It will install its boot manager into the mbr of the first hard disk), Reboot and complete the windows setup now if you wish. Windows shold be useable now.
[*]When you wish to boot the linux installer in expert mode as per step 1. Do a complete install into the partitions that you set aside for linux in step 1. Near the end of the install, install grub into the mbr. It will find the windows system and add it into its grub boot menu.
[*]On reboot, select windows or linux from the grub menu.
[/LIST]
This avoids needing to use extra boot managers, which I am generall not confident in anyway and am not sure cause as much harm as good, or extra special/recovery etc CDs.

---

### Post by sandysandy on 2008-08-21
> **DavidTangye said:**
> Correct me if I am wrong someone, but I believe this is the safest easiest way to install windows then linux:

[LIST=1]
[*]Boot the linux installer in expert mode first (eg from the Ubuntu Alt CD or netboot etc), go just as far as the part about setting up partitions and do so. Set them manually to whatever you want eg partition 1 for windows, other primary and/or extended partitions for linux root, and swap. Then stop the install and reboot. So far you just have a disk partitioned the way you want it.
[*]Boot the windows CD. Install to partition 1 as defined above (It will install its boot manager into the mbr of the first hard disk), Reboot and complete the windows setup now if you wish. Windows shold be useable now.
[*]When you wish to boot the linux installer in expert mode as per step 1. Do a complete install into the partitions that you set aside for linux in step 1. Near the end of the install, install grub into the mbr. It will find the windows system and add it into its grub boot menu.
[*]On reboot, select windows or linux from the grub menu.
[/LIST]
This avoids needing to use extra boot managers, which I am generall not confident in anyway and am not sure cause as much harm as good, or extra special/recovery etc CDs.

it may be advisable to use gparted Cd to partition the disk into the required partitions. thereafter install windows and then ubuntu or other linux flavours.

regards

---

### Post by mike_f on 2008-08-21
> **sandysandy said:**
> have a look at this tutorial on installing XP after Ubuntu.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
also post snapshots of ur partitions from gparted.
regards

It is a very good tutorial but it leaves out (IMO) an important step. Always consider the need for a) backing up personal data like My Documents, huge media libraries, etc and b) sharing same data with Ubuntu.

Always create a primary (extended) partition with one or more logical partitions to store shared data in. The shared data partition should be formatted NTFS which Ubuntu mounts in a user friendly way. Also, the swap partition and even Ubuntu itself can be installed in logical partitions.

Previous posters were correct, Windows should always be installed in a primary partition. IMO primary partitions should only be used for operating systems.

If any other primary partitions are FAT32 or NTFS, mark them hidden (using Gnome partition editor) before installing Windows or you will put yourself into drive letter mapping hell.

Finally, add an 'unhide (hdx,y)' line to the Windows entry in /boot/grub/menu.lst, just in case something marks the partition hidden. 'x,y' is the same value as the 'root (hdx,y)' line.

HTH!

---

### Post by willix on 2008-08-22
> **mike_f said:**
> 
Previous posters were correct, Windows should always be installed in a primary partition. IMO primary partitions should only be used for operating systems.



Are you absolutely sure about this??? That's sounds like a pretty heavy constraint (since one can only have 4 primary partitions on one drive).
  Has it not to do with the positioning of the second stage boot loader rather than the type of the partition it is in? I remember something about some drive/system that can't boot if the boot stage is further than the 1024th cylinder or something alike. Anybody remember the exact rule and when/for what it applies?

guywithcable:
The FAT16 was initially put there because I thought a first small partition which I would mount on /boot was a good idea (because of what I just mentioned above). As it turned out, I didn’t need it for linux; Might need it now for windows though!


Nico0020:
I hope you don’t mind me posting in your thread as it's basically the same problem (I wanted to create a new thread with the exact same title [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]
So far, I've followed the same steps as the tutorial sandysandy mentioned (without the repartitioning since I already had a free partition) and I agree it's quite  neet

---

### Post by Nico0020 on 2008-08-22
cool, thank you for all the advice everyone.  I am finally going to start working on this in about an hour.  Anyone know about how much space I should desginate to windows?  My original install I still had a bigger windows partition, but I want it to be the other way around.  Basically all I will have one windows is the primary install and want about 5 GB to play with.  I want to keep the partition as small as possible. 

In the end I will have 
Linux File System
SWAP
HOME
Windows
2nd linux File system 
(for trying out new versions before I update to check for problems.)

---

### Post by guywithcable on 2008-08-22
> **willix said:**
> Are you absolutely sure about this??? That's sounds like a pretty heavy constraint (since one can only have 4 primary partitions on one drive).
  Has it not to do with the positioning of the second stage boot loader rather than the type of the partition it is in? I remember something about some drive/system that can't boot if the boot stage is further than the 1024th cylinder or something alike. Anybody remember the exact rule and when/for what it applies?

guywithcable:
The FAT16 was initially put there because I thought a first small partition which I would mount on /boot was a good idea (because of what I just mentioned above). As it turned out, I didn&#8217;t need it for linux; Might need it now for windows though!


Nico0020:
I hope you don&#8217;t mind me posting in your thread as it's basically the same problem (I wanted to create a new thread with the exact same title [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]
So far, I've followed the same steps as the tutorial sandysandy mentioned (without the repartitioning since I already had a free partition) and I agree it's quite  neet

Have you already installed both Windows and Linux, because if you have, I can help you reinstall Grub so they will both play nicely together. I don't know if the tutorials have explained this already, but here goes.

I'm going to assume you have installed Linux (root partition) on /dev/sda3 and Windows on /dev/sda6. If you have not, you can adjust the hard drive numbering accordingly.

Boot up into the Ubuntu live cd and go to a terminal.

Type ```
sudo grub
``` and you should be taken to the grub terminal.

Type ```
find /boot/grub/stage1
``` to determine your root partition. I have assumed that it is hd0,2 (/dev/sda3).

Type ```
root (hd0,2)
``` or whatever your root partition is.

Type ```
setup (hd0)
``` to install Grub to the master boot record.

Type ```
quit
``` to exit the Grub shell.

You should now have Grub as your boot loader. You may want to check your /boot/grub/menu.lst in /dev/sda3 to make sure Grub is aware of your Linux and Windows partitions before rebooting.

---

### Post by guywithcable on 2008-08-22
> **Nico0020 said:**
> cool, thank you for all the advice everyone.  I am finally going to start working on this in about an hour.  Anyone know about how much space I should desginate to windows?  My original install I still had a bigger windows partition, but I want it to be the other way around.  Basically all I will have one windows is the primary install and want about 5 GB to play with.  I want to keep the partition as small as possible. 

In the end I will have 
Linux File System
SWAP
HOME
Windows
2nd linux File system 
(for trying out new versions before I update to check for problems.)

If it's XP, you'll want about 10 GB total. In my experiences, an average XP install grows to about 3 GB. For Vista, I'd say about 15 GB. My old Vista install grew to almost 9 GB! ([http://www.guywithcable.com/main/computers/91-windows-vista-87-gb](http://www.guywithcable.com/main/computers/91-windows-vista-87-gb))

You can also grow and shrink your partitions after you make them with Gparted. Boot the live cd and go to **System** > **Administration** > **Partition Editor**. Remember to be patient, it takes **forever**.

---

### Post by willix on 2008-08-22
OK done and dusted...
 
I repartition my system in order to have a 8G NTFS partition as my first primary partition. Reinstalled windows on it and still has the same problem (i.e. invalid partition table). I looked at the partition table and I again had two bootable partition (sda0 and sda4). I removed the flag on sda4 and everything was downhill from then on.
Windows finished installing, I added a few drivers, downloaded SP2 and 3, blablabla... and finally rebooted from my Ubuntu CD and rewrote the MBR.
I am now the owner of a windows XP installed after Ubuntu :-)
 
The only question I'm still wondering about is what would have happened if I had tried removing the flag on my extended partition before repartitioning (i.e. installing windows on an extended partition). I'm kind of surprise XP has to be on a primary. I might try it on day, just for the sake of it.
 
Anyway, many thanks to you all for the time spent helping me getting this system up on time. 8)

---

### Post by mike_f on 2008-08-25
> **willix said:**
> Are you absolutely sure about this??? That's sounds like a pretty heavy constraint (since one can only have 4 primary partitions on one drive).
  Has it not to do with the positioning of the second stage boot loader rather than the type of the partition it is in? I remember something about some drive/system that can't boot if the boot stage is further than the 1024th cylinder or something alike. Anybody remember the exact rule and when/for what it applies? 

You may be right, the source of my statement might be hard to track down. 
However due to previous episodes of drive letter mapping hell, I'm leery about installing Windows onto a logical partition. If not careful the Windows boot manager can bite you..... 
If you feel lucky, try it. Just remember that Windows reinstalls usually take twice as long as any Linux one :) .
I don't think of four primary partitions as an install constraint because I always install the Windows o/s in the first or second primary partition (remembering the 'first 1024 cyl only bootable' limit). Heck, you could install three copies of Windows :confused: and put everything else into logicals. Per previous post I ALWAYS put user/shared data into a separate partition; any o/s can become unstable and require wiping its partition.

EDIT: I looked back at your PM error message
"PowerQuest PartitionMagic has found an extended partition on disk 1 that crosses the 1024 cyinder boundary and is not marked as an Extended partition. This condition can cause data corruption on this disk." 
which has me puzzled - it doesn't make much sense. I'm pretty sure any partition can cross the boundary but it can't be bootable (if Windows). This is why I recommend a) backing up immediately, b) using both PM and SysRescue disk - both have peculiarities.

---

