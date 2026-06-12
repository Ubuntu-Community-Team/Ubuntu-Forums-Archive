---
title: "Ubuntu Installer does not detect windows nor partitions"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by hishabi17 on 2015-01-12
Dear forum users, I am very new to linux and I am trying to install Ubuntu as dual boot with windows 7. However the installer will not find any operative system on my computer nor recognise any of the partitions I made with Gparted. Has anyone any idea on how to fix this?

I know this problem has been posted and solved already in this thread here [http://ubuntuforums.org/showthread.php?t=2236762](http://ubuntuforums.org/showthread.php?t=2236762) however I think I followed the instructions (the ones in the second last post after which the person said he solved the problem) and I still did not get anything out of it. So I am not sure if I didn't follow the instructions in the correct way or they didn't work for me, I am not sure especially because I am not used to the terminology so I am unsure if I understood what the solution was.

I attatch the screenshots (actually pictures as I don't know how to screenshot in Gparted) of what I tried to use. I first tried having some unallocated space (it's only 20Gb but I don't think ubuntu requires more, right?) and then I tried making two partitions, one formatted as swap and one as ext4.

[ATTACH=CONFIG]259200[/ATTACH][ATTACH=CONFIG]259201[/ATTACH]

In both cases the ubuntu installer just didn't recognise any partition (not even the windows ones) saying my disk has 500Gb of free space, which of course is not true.

Sorry for the rather lengthy post, and thank you in advance :)

---

### Post by Bashing-om on 2015-01-12
hishabi17; Hi ! Welcome to the Forum .

Here's the deal .. The legacy partitioning scheme (MBR) due to addressing has a 4 - primary - partition limit. The way around this limitation is to make one of those partitions as 'extended' and within this 'extended' partition make up 'logical' partitions. ubuntu is happy to install in 'logical' partitions.

20 Gigs is a bit tight to install onto; but will do initially .. I see 30 Gigs as the recommendation. By the time you have used up the 30 Gigs, you will have the experience to know what to do .

Presently; One defrags Windows twice, then resize to make up that 'extended' partition' ( best for the long run ) .. run Windows check disks to insure the partition table for Windows is valid. Reboot and run check disk once more.
Install ubuntu into that "unallocated" space using the "something else" option. Make sure that ubuntu's boot loader - grub ( Grand Unified Bootloader) is installed to the device 'sda'. Though Windows will not recognize ubuntu's boot code; ubuntu will recognize Windows and chainload Windows onto it's boot menu.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-12
Thank you very much for the reply! 
I will try all that tomorrow morning and let you know if it works! a quick thing: which partition is going to be the extended? 
I mean is it going to look like: |windows|extended 30Gb|  or |windows|unallocated| and then ubuntu will make that unallocated into an extended partition while installing? 
If I understood correctly I need to defrag> defrag> shrink windows partition and make a 30Gb extended partition> check disk> reboot> check disk> install ubuntu?

Thank you again and sorry for taking a while to understand!

---

### Post by Bashing-om on 2015-01-12
hishabi17; Hey;

In your 1st screen shot you show trying to make up 5 primary partitions ( 2 are Windows) -> no can do .. 4 partitions max (as an extended partition being that container for 'logical' partitions is doable).

In the 2nd screen shot, still with 2 partitions for windows .. and 20 Gigs as unallocated space.
In this arrangement you do have a couple of options, leaving the 20 Gigs as is.
Not the long term best option: is to make up a '/' partition and a swap partition as 'primary' ; can do that 
Make that 20 Gigs "unallocated" space up as an 'extended' partition. and in this 'extended' partition make up the logical partitions for '/' and 'swap' .

At some later time, when you are the more comfortable with 'buntu, you can re-organize your hard disk(s).
The caveat for defrag and check disk still applies.

It is your system, set it up to your liking,
Keep in mind, in 'buntu it is always fixable: time effort and a liveDVD will do wonders.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2015-01-12
Defragment and run checkdisk on windows.  After that you have options of deleting the current Linux ext4 partition and swap partition from windows or doing it during the installation of Ubuntu.  It would probably be simpler to do it in Ubuntu so you can format the partition.  Windows is not capable of formatting for a Linux filesystem so you can't do it that way.  If you select the 'Something Else' installation option when installing Ubuntu, you will have more control over creating and formatting partitiions.  Take a look at the link below on how to install Ubuntu for dual-boot:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Scroll down the page to Installation Guide, Step by Step.

---

### Post by hishabi17 on 2015-01-13
Thanks a lot both of you! Now everything is more clear, I started working on it :)

---

### Post by Bashing-om on 2015-01-13
hishabi17; Great .


That's the spirit.
> **hishabi17 said:**
> Thanks a lot both of you! Now everything is more clear, I started working on it :)

We will get ya up and running 'buntu .

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-14
Hello again everyone.
I did defrag twice, deleted the ext4 partition and the swap, made an extended partition (this using gparted as I don't like the windows partition editor) so here is a screenshot of the partitions I now have
 [ATTACH=CONFIG]259230[/ATTACH]
and then I run check disk twice... 
it seems to me the situation hasn't changed much!
so I thought I post a screenshot of what I see when I try to use the ubuntu intaller, after it says it has not detected any other operative systems on my computer, I select the something else option and this
[ATTACH=CONFIG]259229[/ATTACH]
is what I see, it seems that it doesn't detect any of the partitions that are on the drive nor any file! 
I am afraid that if I continue the installation it will overwrite everything on the drive (I do have a windows system backup but would rather avoid having to reinstall windows!)
So where am I going wrong?
Also windows har done a couple of updates while I was rebooting to che the disk, I hope this has not changed things around, if you think it has then I can run the whole process again...

---

### Post by Bashing-om on 2015-01-14
hishabi17; Humm ...

I too am a bit mystified as to what is taking place. The 1st screen shot of the partitions looks proper to me.
Is it possible that Windows utilizes a quasi hibernation mode (fast boot) such that the drives are still held as in-use by Windows ?
When you boot back out of Windows, make sure Windows is completely shut down and powered off .

Maybe we can set this up manually ..?
Using the 1st screen shot as the guide, we make up 2 'logical' partitions that will reside in the 'extended' partition; using GParted.
click on the unallocated space 1st partition:  choose "New" -> partition type 'logical' -> use as '/' -> size @ 17.8 Gigs
2nd partition for swap: click on the unallocated space once more -> New -> type 'logical' use as 'swap' size @ 2 Gigs
Make sure the sizes of these 2 partitions does not exceed the size of the "container" ( the extended partition) - 20.06 gigs.
The system uses by default 5% of the space for it's house keeping.
Where '/' is "root" and will hold the ubuntu file system.
In Gparted tool bar edit menu -> commit to the changes (X2).

Now boot the installer .. does the installer now see the partitions ?
I would expect that '/' is identified as 'sda6'; point the installer to install in that partition .
I also expect that the installer will automagically recognize the 'swap' partition.
Make sure grub is installed to device 'sda' .

[INDENT][INDENT][INDENT]try'n to struggle through this - together
[/INDENT][/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-14
Thanks Bashing-om, I'll try that, also I deactivated the quick boot on windows, and I always turn it off using the "shut down" button in the start menu rather than a physical button on the computer so it cannot be the problem...
I will try now making the partitions you sugested :)

---

### Post by hishabi17 on 2015-01-14
What type of partition is the '/'? I cannot see it in the list, the list includes:
Btrfs
Ext2
Ext3
Ext4
F2fs
Fat16
Fat32
Hfs
Hfs+
Jfs
Linux-swap
Lvm2 pv
Nilfs
Ntfs
Reiser4
Reiserfs
Xfs
Cleared
Unformatted

---

### Post by Bashing-om on 2015-01-14
hishabi17; OH ...

the file type in your use case ls 'ext4'

[INDENT][INDENT]sorry bout that slip of my mind
[/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-14
Thank you, especially thanks for the patience and constant help! I'll finish this attempt tomorrow morning (I'm in Europe and is getting late now) :)

---

### Post by Bashing-om on 2015-01-14
hishabi17; Hey !

> **hishabi17 said:**
> Thank you, especially thanks for the patience and constant help! I'll finish this attempt tomorrow morning (I'm in Europe and is getting late now) :)


It is you with the perseverance . I do admire that. All I am doing is trying to hold your hand.

we want to share this
[INDENT][INDENT][INDENT]our operating system by choice
[/INDENT][/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-15
hello bashing-om, thanks, I do not give up easily :D 
However it still didn't work , I created the logical ext4 partition and swap partition within the extended, but the installer still gives me the same result of thinking the whole drive is empty without any partition! I'll try again the defrag check disk during the day. 
Do you think moving the extended partition to the left of the big Windows partition (so towards the start of the drive rather than at the end) could help? Moving the whole thing seems to be a several hours long job but if it can help I'll do it overnight :)

---

### Post by Bashing-om on 2015-01-15
hishabi17; Shucks;

I do not know what the source of the problem for ubuntu to recognize the partitions. Moving the partitions, I do not think will help. Unlike Windows, ubuntu does not require to be installed at the start of the hard drive.

Show us what the present situation is by providing a current screen shot from GParted;
and as well the outputs - from that live DVD - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
Perhaps what we have here is a mismatch of partitioning schemes GPT/MBR ?

There must be a reason .. I assure you it is not at all difficult to install ubuntu "along side" of Windows .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I just do not know -> seeking to find the why
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-15
So here it's a screenshot from GParted
[ATTACH=CONFIG]259265[/ATTACH]
and a few screenshots from the commands:
[ATTACH=CONFIG]259267[/ATTACH]
[ATTACH=CONFIG]259268[/ATTACH] here it asked a question, not too sure what it means but from what I could undestand the answer I needed to give was yes? well I did and the next screen shows what came out.
[ATTACH=CONFIG]259269[/ATTACH]
the 8Gb disk shown is the one I am booting from (I am using a live USB rather than a live DVD)

---

### Post by hishabi17 on 2015-01-15
and here the rest of the screen shots as I could't upload all of them in one post: [ATTACH=CONFIG]259270[/ATTACH][ATTACH=CONFIG]259271[/ATTACH]

from what I could understand there may be something not right but I wouldn't know where or how to solve it

---

### Post by oldfred on 2015-01-15
Was system Windows 8 with UEFI?
Windows only boots from gpt partitioned drives with UEFI.
And Windows only boots from MBR partitioned drives with BIOS.
If you reinstalled Windows in BIOS boot mode it incorrectly converts drive from gpt to MBR. It leaves the backup partition table. Then Linux tools only think you want to erase entire drive to correct the inconsistency.

But you can use fixparts to remove backup partition table. Since Windows is in BIOS boot mode, be sure to only boot in BIOS mode not UEFI mode.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by Bashing-om on 2015-01-15
hishabi17; Yepper,

I think I think /// What we have here is GPT partitioning .. and we are imposing MBR partitioning .. no can do.
Let me get into contact with another compatriot, see what he advises in this situation; as my Windows skills are next to none.

See what we can do
[INDENT][INDENT][INDENT]to wrangle out of this situation
[/INDENT][/INDENT][/INDENT]

---

### Post by hishabi17 on 2015-01-15
Hi oldfred, it isn't windows 8, but windows 7 Home premium (sorry for not saying earlier!) and I am not sure if it is BIOS or UEFI and not sure how to find out...
Hi Bashing-om, thanks! :)

---

### Post by oldfred on 2015-01-15
Was it gpt before/UEFI before?
As that seems to be the issue.

---

### Post by hishabi17 on 2015-01-16
Hello oldfred, I am not sure what you mean by "was it gpt before/UEFI before". I did not install the windows 7 on the computer and it's my first ubuntu install so I am unsure  what you mean by "before". 
I searched on google how to find out if my system is UEFI, I found from windows I need to go on disk management and check if in the status tab it says "EFI System Partitioning". In my case it  doesn't, I hope this answers your question :)
Here is a screenshot of what the windows disk manager says, it is in italian however as my windows is  installed in italian so I am not sure if this screenshot helps at all:[ATTACH=CONFIG]259302[/ATTACH]

---

### Post by oldfred on 2015-01-16
Did you try fixparts. It will not hurt if drive is already only MBR(msdos). Windows often leaves some gpt data on drive.

Are you using Something Else to install and use partitions you created with gparted?

Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by hishabi17 on 2015-01-16
Hello oldfred, I haven't tried fixparts yet mostly because I didn't understood well what it does, but I'll try it :) also I did post the commands you are suggesting yesterday and did use the something else option (and that does not recognise the partitions, I posted a screen of this as well)

---

### Post by hishabi17 on 2015-01-18
Hello oldfred and bashing-om, I managed to install it! I finally had time to read through the fixpart tutorial and use it (it wasn't actually difficult, I just have been very busy the past two days) and it worked, now the installer detected Windows and I used the option to install ubuntu alongside it and it is now installing :) thanks a lot for the help in the past days!!

---

### Post by Bashing-om on 2015-01-18
hishabi17; Outstandingly great !

Pleased you are finally up and running 'buntu .
Regret it took me this long to tumble onto what the problem was .. and thanks heaps to oldfred for his support .

[INDENT][INDENT]we are having fun now !
[/INDENT][/INDENT]

---

