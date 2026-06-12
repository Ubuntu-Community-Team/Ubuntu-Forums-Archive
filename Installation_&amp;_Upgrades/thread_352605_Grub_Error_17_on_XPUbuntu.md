---
title: "Grub Error 17 on XP/Ubuntu"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by DistroTech on 2007-02-03
I was running a dual boot Edgy / XP setup before that was working perfectly fine.  

Inintially, I had had a GRUB error 18, which involved partition sizes being too big for my BIOS, so I tried to make a /boot partition, but accidentally resized the entire Linux partition to be too small.  

So, I wanted to make my 3.3 GB Edgy into at least a 19 GB Edgy.  Using Partition magic on my Windows side, I was able to change around a few things.

I decided it was best to delete Edgy, resize the partitions, and reinstall.  I figured that with GRUB installing itself again, it would configure correctly.

It did not.

Here is what fdisk -l displays...

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       12158    97659103+   7  HPFS/NTFS
/dev/hdd2           21900       22002      827347+   f  W95 Ext'd (LBA)
/dev/hdd3   *       22003       24321    18627367+  83  Linux
/dev/hdd5           21900       22002      827316   82  Linux swap / Solaris


Here is my menu.lst file...

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


 This entry automatically added by the Debian installer for a non-linux OS
 on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Any help would be ENORMOUSLY appreciated.  I have done a few of the general methods for configuring GRUB that are posted in the forums, but none seem to help.  Thanks in advance for everything!

---

### Post by DistroTech on 2007-02-03
Anyone?

---

### Post by DistroTech on 2007-02-03
:(

---

### Post by Herman on 2007-02-03
Hello DistroTech,
Don't worry, you are not alone...
Your story bears a slight similarity to this one, [Partitioning Tools ( And which ones not to use )]("http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html")
But I haven't read your entire post yet in detail, so I'll get back to you shortly if I see something I can help you with,
Regards, Herman :)

---

### Post by Herman on 2007-02-03
DistroTech,
I can't see anything wrong with your Grub menu entries there, unless I'm missing something.
What error messages are you getting? Grub error 18 still?

Try this link and see if it helps you,
Grub error 18......................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

If you are already using Partition Magic then it might be best to stick with it now. I prefer GParted or any of the 'Parted based partitioners myself, (personal preference), but I also suspect that mixing different partitioners is even worse than sticking with a non-linux one. I had a corrupted partition table once a long time ago after trying out as many different partitioner as I could get my hands on. I think it's best to find one you like and stick with it.
Maybe just reducing the size of your partition until it's inside the 137 GB limit will solve your problem. That has worked for some people in the past.  :)

Regards, Herman :)

---

### Post by DistroTech on 2007-02-04
Herman,

Thanks for the reply!

I am getting GRUB Error message 17, I fixed the error 18 on my first install about two months ago, look at my post history.

I read through what you gave me, and started putting some pieces together.  If using three different partition programs messed this up, why not start over and use only one?

I used the Ubuntu 6.10 Alternate Install CD (Live CD isn't quick enough for me) and deleted the hdd2 (FAT32 Storage), hdd3 (Linux), and hdd5 (Swap) entries.  I manually partitioned the free space to be 80 GB of FAT32, 19.5 GB Linux, and 512 MB Swap.

It installed fine, and got through the GRUB install part fine.  Unfortunately, I still get the same error.

I don't want to have to backup the first partition, since it is 83 GB of things.  Do you think I have to format the harddrive and start over?

Any advice would be very helpful.  The problem may still be Partition Magic making everything all messed up, but I did attempt to only use one partitioner for this install.

Thanks a lot!

-DT

---

### Post by DistroTech on 2007-02-04
Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       12158    97659103+   7  HPFS/NTFS
/dev/hdd2           12159       21946    78622110    5  Extended
/dev/hdd3           21947       24321    19077187+  83  Linux
/dev/hdd5           12159       21884    78124063+   b  W95 FAT32
/dev/hdd6           21885       21946      497983+  82  Linux swap


That is an updated fdisk -l

What is the hdd2?  Extended Filesystem type?  The numbers dont add up here, and I manually partitioned this and did not see it...could this partition be what GRUB isn't recognizing?

---

### Post by Herman on 2007-02-04
> What is the hdd2? Extended Filesystem type? The numbers dont add up here, and I manually partitioned this and did not see it...could this partition be what GRUB isn't recognizing? That's your extended partition, that's okay. It's normal. We can have four primary partitions per hard disk because there are only four sixteen byte spaces for the partitions to be written in the partition table in the Master Boot Record in the first sector of the hard disk.
By making one of them special, called an 'extended' partition, it is possible to have more partitions than just four per hard disk. A string of other partitions can be linked in a series inside the 'extended' partition. These are called called 'logical' partitions. if you look at the sector numbers or cylinder numbers they occupy, you'll see that the logical partitions are all inside the extended one.

Meantime, I think I see the problem, try editing your boot entry in menu.lst to this and see if it helps,

```
 title           Ubuntu, kernel 2.6.17-10-generic
root            (hd[COLOR=Red]**3**[/COLOR],2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
``` I don't know how I missed that earlier.
 See how you go.

Regards, Herman :)

---

### Post by DistroTech on 2007-02-04
That makes sense with the Extended now, and actually is a neat little trick I didn't know.  I knew about a limited number of primaries, but linking the logicals to the primaries is a great feature.

Anyway, I changed the entry to (hd3,2) and it didn't work.  Blast!

This is a new install, so that was an old menu.lst...although I'm fairly certain they were identical anyway.  I'll try changing it again, seeing what happens.

-DT

---

### Post by Herman on 2007-02-04
Double Blast!

...Okay, the gloves are off now! Time to resort Grub's Command Line Interface! Not everyone knows about this, but Grub is no ordinary bootloader, it is actually an operating system in its own right.  We can enter commands and have it carry them out.
Click on this link, and try Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
We can use GRUB's Command Line to [investigate your computer]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")
and find out how Grub sees your hard disks and partitions and [boot linux from Grub's Command Line]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI").
Take notes, because the same commands that you will use for booting Ubuntu from Grub's CLI will be the ones to add to your menu.lst operating system boot entry.
Try that and see what happens! That should fix it! 

Regards, Herman :)

---

### Post by DistroTech on 2007-02-04
This may just be one of the weirdest problems ever!  Lol.

Alright, tried the manual booting...here's a command line that doesn't make sense for ya...

grub> geometry (hd1)
drive 0x81: C/H/S = 24321/255/63, The number of sectors = 390721968, /dev/hdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x82

grub> geometry (hd0)
drive 0x80: C/H/S = 2482/255/63, The number of sectors = 39876480, /dev/hda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> find /vmlinuz
 (hd1,2)

grub> find /sbin/init
 (hd1,2)

grub> root (hd1,2)

grub> kernel /vmlinuz root=/dev/hdd3

grub>


It says it finds them on the drive, but doesn't display any of the responses that GRUB is supposed to...Ever hear of anything like this?  

My guess is that GRUB is missing a component to read the partition for some reason...

Thanks for all your help man, I think we're getting closer to solving this somehow...I really don't want to have to delete Linux and restore the XP MBR...That would be a surrender!

-DT

---

### Post by Herman on 2007-02-04
> It says it finds them on the drive, but doesn't display any of the responses that GRUB is supposed to...Ever hear of anything like this?Yes, I have noticed that sometimes, although it hasn't happened to me often enough for me to work out a likely cause for that. Possibly the type of BIOS in the machine being used. I just now tested one of my computers here and it didn't give me the feedback that the other machines do either.  I think it would be best to just continue regardless.

We won't give in! Well, I won't give in if you don't. Thanks for sticking with me, I hope you aren't minding this too much. I actually enjoy it as a challenge as much as some people enjoy a good puzzle.

What happens when you apply the next two commands, initrd and boot?

Regards, Herman :)

---

### Post by DistroTech on 2007-02-04
grub> initrd /boot/initrd.img-2.6.17-10-generic
Error 1: Filename must be either an absolute pathname or blocklist

grub> initrd /boot/initrd.img-2.6.17-10-generic

Error 16: Inconsistent filesystem structure

Hmm...Something tells me THAT isn't good...I won't do boot, cause that probably won't turn out well with errors like this...

I also enjoy these things too, its always a good challenge...unfortunately this is a family computer (a family that DOES use Linux...and Windows) and they need to be able to boot into it...My own comp has BSD, Kubuntu, and I'm attempting to get OS X...but probably will never be able to do that on PC Hardware.

-DT

---

### Post by tagginannie on 2007-02-04
> **Herman said:**
> Double Blast!

...Okay, the gloves are off now! Time to resort Grub's Command Line Interface! Not everyone knows about this, but Grub is no ordinary bootloader, it is actually an operating system in its own right.  We can enter commands and have it carry them out.
Click on this link, and try Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
We can use GRUB's Command Line to [investigate your computer]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")
and find out how Grub sees your hard disks and partitions and [boot linux from Grub's Command Line]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI").
Take notes, because the same commands that you will use for booting Ubuntu from Grub's CLI will be the ones to add to your menu.lst operating system boot entry.
Try that and see what happens! That should fix it! 

Regards, Herman :)

Just a suggestion try Lilo witch I find it to be less flaky than Grub.. I never
had any problems booting five Linux distros plus Win 2003

Suzy:KS

---

### Post by Herman on 2007-02-04
Here's what I've got on the first grub error, but it doesn't make any sense really.
Grub error   1..................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#1_:_Filename_must_be_either_an_absolute")

And here's what I have for error 16. I agree with you, that might be cause for some concern, but we're not sure yet.
Grub error 16...................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16")

Hmmm. :-k
Which approach would you like to try next?  If you have any LiveCD with GParted in it, especially [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") itself, or a Ubuntu Desktop CD with GParted in it, you could maybe just take a look and see what GParted thinks of your filesystem. If it's really bad it will come up with a black rectangle around it instead of a coloured one.
It's drop dead easy to run a filesystem check on a partition in GParted LiveCD, just right-click on the partition, and click 'check'. That should repair any normal errors in the filesystem if that's the problem. Maybe not if the filesystem is bad enough to have that black rectangle though. I don't think it will be the filesystem itself though, you just installed it, it's brand new. 

Here are a few of my links that I hope you won't need, but that might help possibly,                [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")  [What to do if you have a bad superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup")
                   [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check")

If the problem is in your partition table, GParted LiveCD also has TestDisk in it, which can often repair the master boot record. I have played with it a little, but I don't know as much about it as I'd like to.
It could be a problem with Grub like you mentioned earlier, if you want to test that and see if there could be a problem with your Grub you could try booting from some other Grub like for example a [Super Grub Disk.]("http://supergrub.forjamari.linex.org/")

> Just a suggestion try Lilo witch I find it to be less flaky than Grub.. I never
had any problems booting five Linux distros plus Win 2003

Suzy:KS ...or there's Suzy's approach, how do we install LiLO in an unbootable system though Suzy, I think we can by mounting it with a Live Linux CD like Ubuntu Desktop CD and chrooting into it don't we? I seem to remember doing that once to try it out. Steve Horsley helped me with it. Hmmm.

Well it's up to you, DT, which direction do you feel like going in?

Regards, Herman :)

---

### Post by DistroTech on 2007-02-04
I am willing to try any approach to get the system up.

Right now, I am downloading the GParted live CD (I'm on a Kubuntu Live CD, but the GParted just crashes when I try to see anything).  I will post anything I find out from that...

If I need to switch to Lilo, I don't mind.  It looks okay to me, and I have no extreme attachment to GRUB (It hasn't been TOTALLY good to me :) )

I'll let you know the situation...

---

### Post by DistroTech on 2007-02-04
Okay, I ran GParted from the command line...

I did a check on both drives, here's the output

ubuntu@ubuntu:~$ sudo parted -i /dev/hdd
GNU Parted 1.7.1
Using /dev/hdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) check 1
No Implementation: Support for opening ntfs file systems is not implemented yet.

(parted) check 2
Information: The ext2 file system passed a basic check.  For a more
comprehensive check, use the e2fsck program.
(parted) check 3
Information: The ext2 file system passed a basic check.  For a more
comprehensive check, use the e2fsck program.
(parted) check 4
Error: Partition doesn't exist.
(parted) check 5
(parted)
(parted) check 6
(parted)
It seems to think everything is fine, other than my swap.  For the swap, it does a check for bad sectors, and then doesn't display an output after that...hmpf...

---

### Post by DistroTech on 2007-02-04
Taking a slight sleep break...feel free to PM or e-mail with insights...

I'll post back at this thread circa 6 hours...

---

### Post by tagginannie on 2007-02-04
> **Herman said:**
> Here's what I've got on the first grub error, but it doesn't make any sense really.
Grub error   1..................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#1_:_Filename_must_be_either_an_absolute")

And here's what I have for error 16. I agree with you, that might be cause for some concern, but we're not sure yet.
Grub error 16...................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16")

Hmmm. :-k
Which approach would you like to try next?  If you have any LiveCD with GParted in it, especially [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") itself, or a Ubuntu Desktop CD with GParted in it, you could maybe just take a look and see what GParted thinks of your filesystem. If it's really bad it will come up with a black rectangle around it instead of a coloured one.
It's drop dead easy to run a filesystem check on a partition in GParted LiveCD, just right-click on the partition, and click 'check'. That should repair any normal errors in the filesystem if that's the problem. Maybe not if the filesystem is bad enough to have that black rectangle though. I don't think it will be the filesystem itself though, you just installed it, it's brand new. 

Here are a few of my links that I hope you won't need, but that might help possibly,                [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")  [What to do if you have a bad superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup")
                   [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check")

If the problem is in your partition table, GParted LiveCD also has TestDisk in it, which can often repair the master boot record. I have played with it a little, but I don't know as much about it as I'd like to.
It could be a problem with Grub like you mentioned earlier, if you want to test that and see if there could be a problem with your Grub you could try booting from some other Grub like for example a [Super Grub Disk.]("http://supergrub.forjamari.linex.org/")

 ...or there's Suzy's approach, how do we install LiLO in an unbootable system though Suzy, I think we can by mounting it with a Live Linux CD like Ubuntu Desktop CD and chrooting into it don't we? I seem to remember doing that once to try it out. Steve Horsley helped me with it. Hmmm.

Well it's up to you, DT, which direction do you feel like going in?

Regards, Herman :)

If you have alternate install CD you all ready have the Super Grub disk. Just use the SGD to remove Grub and then install Lilo using Ubuntu install disk. I really can't in to much detail I am getting to kick my family out the door for
their super bowl party.



Ahhhhhh Peace and quiet for few hours \\:D/

Suzy

---

### Post by DistroTech on 2007-02-04
Alright, fell asleep much longer than I thought...

Anyway, how do I access SGD on the Kubuntu Live CD?  And is there an option to specify LILO as my bootloader in the Ubuntu Alternate?

---

### Post by Herman on 2007-02-04
Suzy,
As usual, you are right, I wrote this how-to myself a long time ago about how to use an 'Alternate' CD to do that. I would need to test this to se if an 'Edgy' 'Alternate' CD will do it. It used to work for 'Breezy', but then I didn't think it was working with 'Dapper', but I could be wrong. (I often am wrong). So it's worth a try maybe.
This will install Lilo to the Ubuntu partition so you can boot with GAG Boot Manager. GAG Boot Manager will also boot Windows.
> ** Install Lilo from Breezy Install CD**
  [RIGHT]I don't think this will work any more with a Dapper CD.
  [/RIGHT]
   [CENTER]  INSTALL LILO BOOT LOADER TO UBUNTU PARTITION.....
  [/CENTER]
   
   (So you can boot with GAG boot manager).
   GAG boot manager link:  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
   The GAG bootmanager does not need to disturb your MBR and can be used from a floppy disk or CD-ROM without affecting your original MBR that boots Windows. You can install GAG to your MBR later sometime if you want.
   GAG boot manager is 'operating system independant', so you can install and uninstall operating systems without losing your boot.
  
  When you use this method to install Lilo it is not necessary to run Liloconfig (as shown above).
  
  
   1. Boot the computer with the 'Breezy' install CD.
   2. Complete the questions for the first stage of the installation as if you were installing, until '[!!] Partition Disks' is reached.
   3. Select 'Manual Partitioning'.
   4. Select your Ubuntu partition.
   5. (a) change mount point from /media/hda4 (or whatever) to /.
   (b) change 'bootable' off to 'bootable' (a progress bar will display).
   (c) choose 'done setting up the partition'.
   (d) choose 'finish partitioning and write changes to disk.
   6. Sign says: 'If you continue, changes will be written to disk, etc,''Continue?'choose 'Yes'.
   7. A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
   8. A second red warning screen says 'Install the base system failed' choose 'continue' again. (we don't care!).
   9. This sees you back in the 'Ubuntu Installer Main Menu', and once there you can scroll down to 'Install Lilo boot loader to a hard disk'.
   10. 'Install Lilo to target' '/dev/hda: new Ubuntu partition' (not your MBR if you are doing this for GAG). A progress bar should display as Lilo gets installed.
   11.A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
   12. A second red warning screen says 'Install the base system failed' choose 'continue' again.
   13. Then you will be back in the 'Ubuntu Installer Main Menu' again, but be careful not to press 'enter' on anything you don't want,but scroll down immediatley to 'Abort Installation'.
   14.Exit the installer.
   15.Remove the install CD from your CD drive quickly as soon as you can before it boots from it again!
   

---

### Post by DistroTech on 2007-02-04
Well, I've got some good GNUs and bad GNUs...

Heh,,,

But anyway, I tried out Super Grub Disk, which is an amazing program.  

The first thing I did was boot into my Windows partition...and experienced some problems.  Partition Magic immediately did its own thing.  I forgot that I had specified it to complete a task on boot, and that was where this problem had started anyway.  I had redone my partitions using PM, and when it tried to reboot it couldn't find GRUB.  Now it can't find the partition it was trying to modify.  So I can't boot Windows.  And that scares me, it really does.  If that partition is fried...so am I.

Linux won't boot at all, through any methods (I tried most in the menu), leading me to think that GRUB is completely corrupted.

Oy...

-DT

---

### Post by Herman on 2007-02-04
I will be back in a few hours, but I think you should run a LiveCD like Edgy 'Desktop' or equivalent, and [mount your filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm") (partitions) if you can and take a look and see if you can see any of your files. 
If you can see them you can rescue them with the LiveCD to some other media. I can explain how in detail later, depending on what media you can use. (CD,DVD, external hard disk, etc).
If you cannot 'see' your files then it will be a little more work, but still possible to try to recover, something like TestDisk (on [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")) might be needed, and a little good luck.

Just try mounting with a LiveCD for a start and see what you can find out.
I'll be back later today...

Regards, Herman

---

### Post by DistroTech on 2007-02-04
It looks like you're starting to come to the same conclusions I am.

Before I did this, I was able to mount both the Windows and Linux partitions pretty easily, I'm not at the comp right now, but when I am I'll mount to see if there's any damage.

I have a good DVD burner and a good stack of DVDs...about 75 GB of stuff to recover through a LiveCD will not be fun though.

I'm hoping there's still a way to fix this, I haven't tried safe mode or Last Good Configuration options in Windows yet, so I'll see if I can get those working too.

If anyone is familiar with the quirks of Partition Magic and how to resolve them, your insights are both welcome and appreciated.

I always wanted to move the Windows partition to the 200 GB and I was thinking about getting Vista...looks like I could do both.

-DT

---

### Post by DistroTech on 2007-02-04
Both hard drives are still acessable and seem intact.

No data recovery necessary!  Hurrah!

---

### Post by DistroTech on 2007-02-04
Also, I am now posting from a working Windows boot...huzzah!!!

I am pretty damn happy about that.  SGD was able to boot into it this time without any problems.  Its running fine...and it didn't do CheckDisk, which is slightly odd because of all the partitioning, but not really a problem I care about.  

When I try and boot Linux, it gives me an error **18**, which is what I had before.

Could the problem actually be GRUB mis-diagnosing the real problem?

How can I tell how much space my BIOS can boot from?  Knowing that might help the problem.

---

### Post by tagginannie on 2007-02-05
> **Herman said:**
> Suzy,
As usual, you are right, I wrote this how-to myself a long time ago about how to use an 'Alternate' CD to do that. I would need to test this to se if an 'Edgy' 'Alternate' CD will do it. It used to work for 'Breezy', but then I didn't think it was working with 'Dapper', but I could be wrong. (I often am wrong). So it's worth a try maybe.
This will install Lilo to the Ubuntu partition so you can boot with GAG Boot Manager. GAG Boot Manager will also boot Windows.

Good how-to and I don't see why it shouldn't work with Dapper, This my first Debian based distro that I used (only tried it to because a friend who has been using Debian for years kept bugging me)  they don't look that much different

Suzy:KS

---

### Post by Herman on 2007-02-05
>  When I try and boot Linux, it gives me an error **18**, which is what I had before.
Could the problem actually be GRUB mis-diagnosing the real problem? Yes, it can be, Grub is a pretty good tester and indictator of problems ('a great debugging tool' to quote the Gnu Grub Manual), but it isn't always exact with the error messages.  They are a pretty good indicator, but they are not always right. I have had Grub error 18 after messing around with my partitions in a machine with an 80.0GB hard disk and a 30.0 GB disk, both IDE. The thing is, those same disks had been in the machine for quite some time and it was quite capable of booting them, so I don't know what was wrong there. When I got my partitioning back to normal the problems cleared up and everything has been working fine ever since. So I guess that means my machine has a 'buggy BIOS'. I'll just have to leave it at that until I learn more.

>  How can I tell how much space my BIOS can boot from?  Knowing that might help the problem.  Well, to find out about your BIOS,  as the machine is booting up, you hoover your finger over the pause key. Hit the pause key for each time the monitor gets a new picture on it, and hit enter and then pause again as soon as the monitor changes. You might see a screen with the information you are looking for, if not, look for some printing there that will tell you how to enter CMOS program, or BIOS. Maybe you need to press Esc, or Delete, or an 'F' key, or Ctlr+Alt+F1, or something.
In the CMOS, you need to use your arrow keys and esc and enter keys and tab key to get around. There will be instructions to tell you that. You should see something like 'System Information' or 'Product Information'. When you select that it might have the details like the BIOS date in there for you, so you can make a note of it.
Since you have Windows, you can use a BIOS Agent or BIOS Wizard from one of these sites,
 [http://www.unicore.com/global/](http://www.unicore.com/global/) or [http://www.esupport.com/bioswiz/index2.html](http://www.esupport.com/bioswiz/index2.html)
or type DEBUG after the C:\ prompt.

Someone might be knowledgable and kind enough to tell us a Linux command for displaying BIOS information, I can't think of one at the moment, but I would be surprised if there isn't one.

When you know what BIOS version you have, go to your motherboard manufacturer's website and see what information you can find out about your motherboard and BIOS. There might be a more modern BIOS flash available for your motherboard. If so, usually it will be a free download, and normally you copy it to a floppy disk and reboot. *Be sure to read all the instructions and follow them carefully*. It might possibly improve your computer quite a lot!

           Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. (According to information I have been able to find, someone please correct me if these are wrong).
            2.11 GB or 4095 cylinder limit
            3.26 GB or 6322 cylinder limit
            4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
            8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
            33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
            137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
           

Here are some other good BIOS links:[BIOS (Basic Input / Output System)]("http://webpages.charter.net/netw_1/bios.htm")  |  [The Definitive BIOS Optimisation Guide]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")

Regards, Herman :)

---

### Post by DistroTech on 2007-02-06
Hmm...well, I didn't forget about the forums, or this problem.

No, it was not miraculously solved with me forgetting to thank you guys.  No way!  Lol.

I did try a few other things, and was hoping they would work.  Getting Windows back up was awesome, but I still want Linux to work (KDE is too cool).

I thought that with an error 18, I could fix this by fooling the BIOS.  I tried the following things:

-Making a /boot partition
-Making a 10GB installation with a 15GB /home and a 15GB /opt
-Making a 5GB installation with a 15GB /home and a 15GB /opt

Things just aren't working out...I can still try a minimum install, but this just isn't as easy of a fix as I thought it was.

I'm hesitant to update the BIOS (I did analyze it, thought finding the proper update is tricky), because if THAT goes down, then my life is over.

My BIOS is supposed to be able to boot from anything up to 50GB...so, to quote Seinfeld: "What's the deal with the Grand Unified Bootloader? I don't get it!"

---

