---
title: "Can I make an extended partition?"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by jasoncruz98 on 2011-11-07
[SIZE=2]I want to dual-boot Windows 7 and Ubuntu 11.10 on my hard drive (HP Pavilion g4)

Right now I have 4 partitions on my hard drive, [/SIZE] [SIZE=2]

/dev/sda1, (ntfs) which has the SYSTEM label. [/SIZE][SIZE=4][SIZE=2]
/dev/sda2, (ntfs) which contains Windows 7.
/dev/sda3, (ntfs) which has the RECOVERY label.
/dev/sda4, (fat32) which has the HP_TOOLS label.

Can I make /dev/sda1, /dev/sda2, /dev/sda3 or /dev/sda4 into an extended partition and install ubuntu on a logical partition without anything bad happening to my laptop?






[/SIZE]

[/SIZE]

---

### Post by Hakunka-Matata on 2011-11-07
> **jasoncruz98 said:**
> [SIZE=2]I want to dual-boot Windows 7 and Ubuntu 11.10 on my hard drive (HP Pavilion g4)

Right now I have 4 partitions on my hard drive, [/SIZE] [SIZE=2]

/dev/sda1, (ntfs) which has the SYSTEM label. [/SIZE][SIZE=4][SIZE=2]
/dev/sda2, (ntfs) which contains Windows 7.
/dev/sda3, (ntfs) which has the RECOVERY label.
/dev/sda4, (fat32) which has the HP_TOOLS label.

Can I make /dev/sda1, /dev/sda2, /dev/sda3 or /dev/sda4 into an extended partition and install ubuntu on a logical partition without anything bad happening to my laptop?[/SIZE][/SIZE][SIZE=4][SIZE=2]

By starting two threads for the same subject, you've thrown us a bit of extra challenge in keeping up with where you are on the problem.  I suggest you mark one of your threads [SOLVED] and just use the other, or merge them, I don't know how to do that.

Now about your HDD.  You have four primary partitions on your HDD already, that's the maximum allowed on MBR style HDDs, you knew that right?  

So you have to delete at least one of the primary partitions.  And since you're messing with what Windows OS thinks it knows about the HDD layout, you should take care to delete and resize windows partitions (ntfs) using Windows tools, like Disk Manager.  Use gparted to make new partitions, but not to resize, delete, windows partitions.  For Windows XP, it is OK to use gparted in linux to resize the partition, but not with Vista, or 7.

Where do you stand now, how does your HDD partitioning look now?
[/SIZE][/SIZE]

---

### Post by BillyBoa on 2011-11-07
To avoid any trouble (and I feel that you are going to have) maybe is better to use wubi.exe included on the Ubuntu CD. With this you can have a perfectly working Ubuntu, inside Windows.

---

### Post by Matti L on 2011-11-07
If you make a recovery DVD then you can delete recovery and hp tools partitions. Deleting recovery partition should be an option in the start menu somewhere.

---

### Post by Bucky Ball on 2011-11-07
> **BillyBoa said:**
> To avoid any trouble (and I feel that you are going to have) maybe is better to use wubi.exe included on the Ubuntu CD. With this you can have a perfectly working Ubuntu, inside Windows.

Wubi intended to try Ubuntu, not for permanent use (and slower than a hard drive install) and the Wubi 11.10 version I wouldn't go anywhere near (Wubi can be problematic enough without contending with all the issues that go with a new release). 

No-one seems to have mentioned ... how are you going to get an extended partition around what's already there? You are going to need to wipe the partitions you are wanting to put in the extended partition, make an extended partition big enough to hold 'em, then recreate your partitions in the new extended one, then put your data back. In other words, you have some serious backing up to do. Nothing bad is going to happen with your laptop (unless things get pear-shaped and you lose your temper!). You just need to back up before you try doing anything as you are in for a bit of a major operation. As mentioned by Hakunka Matata, four primary partitions is your max. Best bet, leave the Windows partition on a primary (cos it has to be), create an extended partition with the rest of the drive and put everything else in there (Ubuntu doesn't care whether it's on a primary or logical in an extended).

Your only other option is to create enough free space to create an extended partition big enough to hold your data and your Ubuntu install, create appropriate partitions, install Ubuntu and move your data in there, then delete the old duplicate partitions.

I always advise sitting down with a cup of tea or another refreshment, a piece of paper and an old-school writing implement, taking your time and planning your partitioning well before actually doing the job (DON'T do it on the fly). That way you should only have to do it once and you can plan for the future so any resizing or other partition manipulations are minor rather than the major operation you are facing now.

Incidentally, it is against forum rules to double post. I have asked mods to merge. ;)

---

### Post by oldfred on 2011-11-07
Other thread was closed.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by jasoncruz98 on 2011-11-07
What I really want to know is can I install Ubuntu 11.10 on a logical partition inside my C drive (which contains Windows) and boot it normally without Windows crashing?

And I also have another question: Can I install Ubuntu 11.10 on a logical partition inside the SYSTEM partition without my laptop crashing?

---

### Post by Bucky Ball on 2011-11-07
> **jasoncruz98 said:**
> What I really want to know is can I install Ubuntu 11.10 on a logical partition inside my C drive (which contains Windows) and boot it normally without Windows crashing?

And I also have another question: Can I install Ubuntu 11.10 on a logical partition inside the SYSTEM partition without my laptop crashing?

  
No, and no. C is a partition, not a drive. How can you make a logical partition inside a primary system partition??? You can only make a logical partition inside an extended one. 

Are you talking about Wubi or a fair dinkum dual boot with Windows and Ubuntu on separate partitions?

---

### Post by jasoncruz98 on 2011-11-08
Is there a way to change the primary partition and make it into an extended partition so I can put a few logical partitions inside it?

---

### Post by Quackers on 2011-11-08
No. You may (or may not) be able to copy what is in a primary partition then delete that partition. You could then create an extended partition inside which you can create a logical partition to which you can copy back what was in your original primary partition.

---

### Post by jasoncruz98 on 2011-11-08
Thank you Quackers for answering my question.
 
Now am I able to do what you listed above, in this case copying the C partition and then deleting it? Then I would be able to copy the contents into an extended partition.
 
But would anything happen to my usage of Windows 7?

---

### Post by Quackers on 2011-11-08
Copying and moving the C: partition may not be good. Windows won't boot from inside a logical partition (unless its boot files are in a separate primary partition).
Choose a different partition to copy/move.
If you need more space try defragmenting the C: drive then shrink it with Windows Disk Management console.

---

### Post by jasoncruz98 on 2011-11-08
> 
Its an important partition, it contains hardware diagnostics, and is used when the bios is flashed (updated), It makes flashing the bios a much safer operation, if you remove the tools partition and attempt flashing the bios it will be done from inside windows which is Very risky business, if bios flash fails it can render the notebook useless and will have to be repaired by HP.
  
 
I saw this online in the HP Support Forum. Based on this information, If I put the HP-TOOLS partition into a logical partition, will anything bad happen to my system?

---

### Post by Quackers on 2011-11-08
It may be, as you have a system partition which probably holds your Windows boot files, but it is not something that I would recommend.
What I would do is delete the HP_TOOLS partition (I believe these tools are for diagnostic purposes and are available separately via the HP website, if needed).
This will give you a "spare" partition to play with, but not the space needed for an Ubuntu installation.
What you would then need to do is defragment your C: drive then shrink your C: drive by using the Windows Disk Management console. This will give you some free space. This free space can then be turned into an extended partition which can then hold as many logical partitions as you want.
Ubuntu will boot from a logical partition.

---

### Post by jasoncruz98 on 2011-11-08
I already shrunk the C partition and now I have 500+GB of unallocated space.
 
If I want to play safe, then I guess my only option would be creating multiple Recovery disks using HP Recovery Manager and then deleting the RECOVERY drive.
But, how is the Windows 7 Recovery disk different from the Windows 7 installation disk? Won't it basically do the same thing?

---

### Post by Quackers on 2011-11-08
If you go down that route I would recommend that you verify the recovery dvd's once made. More than one copy would be a good idea, yes.
The recovery dvd's will recover your pre-installed Windows system to the state it was in on the day you bought it.
An installation disc will install a brand new (non-OEM) version of Windows.
It is not normally the case that an installation disc is provided with an OEM Windows installation (nor even recovery discs nowadays).
Presumably your Windows installation disc is a different version of Windows?

EDIT  A recovery disc will likely replace all your current partitions with new ones (including recovery/ HP_TOOLS etc). An installation disc will not.

---

### Post by jasoncruz98 on 2011-11-08
> 
HP Client Manager from Symantec is a FREE hardware management tool for HP client computers that provides in-depth client inventory, driver and utility updating, remote BIOS management, hardware monitoring, diagnostics, and problem resolution.

 
 
I found this on the Symantec website. If I install this on my computer, would I then be able to safely delete the HP-TOOLS partition? I would at least make a backup of the HP-TOOLS partition in case anything goes wrong.

---

### Post by Quackers on 2011-11-08
I honestly don't know about that. It may be an option for you.
In all honesty I have never needed to flash my bios on any of my systems.
You could certainly try to copy the HP TOOLS partition and then replace it as a logical partition later. However there may be hidden files in that partition that are not easily copied.
As long as you have valid recovery discs you could always go back to your original disc configuration - but it does mean that a lot of updates need to be run after.

---

### Post by satanselbow on 2011-11-08
I can honestly say that attempting to move/change partition type to logical etc etc of your Recovery partition and/or Tools will be an epic fail and ultimately leave you  with a system that you unable to (Windows) recover should you need to.

This may also extend to replacing your harddrive should it fail - recovery disks made on one drive may not recover to a replacement drive if the drive signature does not match (ie same size / manufacturer etc).

"Recovery discs" may also require the presence on the "tools" folder on the drive to be able to restore that drive... catch 22.

The only certain method freeing up primary partitions - and having a restorable windows system - is by having full version windows media cd/dvd (depending on version).

Whilst it is considered "grey" by some I can only suggest that you download clean Windows installation from "somewhere" and say to hell with the recovery/tools partitions altogether.

When you bought your machine you paid for the "key" to use windows (sticker on bottom of machine) where and how the Windows OS is installed onto your disk is irrelevant.

Think about counterfeit versions of windows - do MS make you reinstall? NO! They sell you a valid key! As long as you install the correct version for your key there really is no problem.

OEM partition greed related rant over :popcorn:

---

### Post by Bucky Ball on 2011-11-08
You have 500Gb of free space? What are you waiting for? Create an extended partition in there and get started putting logicals in that.

You can only create an extended partition on free space and if you move the contents of the C: partition you are moving Windows and that will be that. You can't do that. What you are asking on both counts is impossible and not sure why you're asking when you have 500Gb of free space. ;)

I generally make the backup CDs using the HP software in Windows which allows me to reinstall Windows, wipe the drive completely, reinstall Windows on a 30Gb partition, make the rest one big extended partition and off you go. 

NOTE: Always defrag your drive two or three times before shrinking. If you don't do this you will not get a correct read out of available space you can shrink as Windows spits the data all over the partition. You need to cram it all back together again to get a more realistic idea of how much you can shrink the drive. For future reference because your fine for now.

---

### Post by jasoncruz98 on 2011-11-09
> I generally make the backup CDs using the HP software in Windows which allows me to reinstall Windows, wipe the drive completely, reinstall Windows on a 30Gb partition, make the rest one big extended partition and off you go.

But then don't you need the HP-TOOLS partition which allows you to flash the BIOS?

---

### Post by Bucky Ball on 2011-11-10
You don't need that to flash the bios. You can flash it by downloading the bios .exe file from HP and execute it in Windows. That's that. All the link in the toolbox does is take the legwork out of it by downloading the correct bios for you machine so you don't need to do it manually then executing the file ... so you don't have to do it manually.

---

### Post by jasoncruz98 on 2011-11-11
Thank you for solving my problem. Now I finally dual-booted Windows 7 and Ubuntu 11.10 and I am ready to help others.

---

### Post by Bucky Ball on 2011-11-11
11.10? How's it running? You may need some help yourself but that's what the forums are here for. Well done, good luck and enjoy ... ;)

---

