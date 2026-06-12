---
title: "Dual-Boot"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by mollycule on 2011-03-15
I'm trying to dual-boot Win7 and Ubuntu 10.10 on my netbook.  Currently, my netbook has Ubuntu Netbook Remix, so I put a Win7 ISO on another flash drive, booted it, and then got stuck when it said that my disk drive wasn't in the right format to install Win7.  The instructions I'm looking at on how to do this whole thing ([http://lifehacker.com/#!5403100/dual+bo](http://lifehacker.com/#!5403100/dual+bo) … ct-harmony) say to use Gparted from the "live" install of Ubuntu, assuming the computer already has Windows on it, and run Gparted from the live Ubuntu.  I tried to run Gparted from the Ubuntu I already have installed on my netbook,  but I couldn't do anything because my hard disk was in use and there is no unallocated space.  When I try to boot the LiveCD files for GParted from my flash drive, I get a screen that says "BOOTMGR is missing, Press Ctrl + Alt + Del to restart." I used TuxBoot to put the iso on my flash drive, and the iso I'm using is gparted-live-0.8.0-3.  I also tried 0.8.0-1. 
Help? Tips? Thanks!  My netbook is an Asus Eee PC, by the way.

---

### Post by oldfred on 2011-03-15
Windows does not see Linux partitions. But you can create with gparted a primary NTFS partition with the boot flag and then winodws will see that and install to it. It will then install into one partition even though the standard install to a blank drive creates a hidden boot/recovery partition and a main install partition.

---

### Post by coffeecat on 2011-03-15
> **oldfred said:**
> Windows does not see Linux partitions.

@mollycule, as much as I do not want to contradict oldfred, for whose contributions to this forum I have enormous respect, I need to warn you of a dangerous potential the Windows installer has in your situation.

Windows does see Linux partitions, but if they are logical ones, it gets very confused and calls them primary partitions. Or rather Vista and W7 does (XP simply calls them unknown), so that  Disk Management can report an absurdly impossible number of primary partitions. See this thread for more details:

[http://ubuntuforums.org/showthread.php?t=1675458](http://ubuntuforums.org/showthread.php?t=1675458)

That would be merely a curiosity but it may be at the root of the Windows installer's propensity to corrupt the partition table when installing in the presence of Linux logical partitions. See my posts #42 and #44 in the following thread for the way XP and Vista can do this in a particular set of circumstances:

[http://ubuntuforums.org/showthread.php?t=1687873](http://ubuntuforums.org/showthread.php?t=1687873)

Win7 does the same as Vista in those circumstances.

I've done several other experiments with the Windows installer and this partition table corruption doesn't always happen, but my advice would be:

1 As oldfred says, create a primary NTFS partition for Windows with the boot flag set using Gparted.

2 When you run the Windows installer, don't let it reformat the partition. Just tell it to install to the partition you've prepared in Gparted. Depending on your partition layout it's at the reformatting stage that the Windows installer can do some silly things.

---

### Post by coffeecat on 2011-03-15
@mollycule, apologies, I missed this.

> **mollycule said:**
>  When I try to boot the LiveCD files for GParted from my flash drive, I get a screen that says "BOOTMGR is missing, Press Ctrl + Alt + Del to restart." I used TuxBoot to put the iso on my flash drive, and the iso I'm using is gparted-live-0.8.0-3.  I also tried 0.8.0-1. 
Help? Tips? Thanks!  My netbook is an Asus Eee PC, by the way.

I don't know about Tuxboot, but try this. Use the ISO for Ubuntu. The Ubuntu live ISO has Gparted on it. Also, use the startup disk creator app in your installed Ubuntu to create your live USB from the Ubuntu ISO.

One warning: if you are running Ubuntu 10.10 from the hard drive, make sure the ISO is also 10.10. There's a bug which means that the 10.10 startup disk creator won't create a usable 10.04 bootable pendrive, and vice versa.

---

### Post by mollycule on 2011-03-15
Thanks for the advice - running the "trial" of Ubuntu from my flash drive and using Gparted on it is working so far.  It's taking a while to create the partition, so I'll check back in when later if I get stuck on an instruction in the Lifehacker guide.  After I'm all done, I'll be sure to add the [SOLVED] prefix. We'll see how this goes!

---

### Post by mollycule on 2011-03-16
So I got both Windows and Ubuntu installed, but ended up having to install Ubuntu on the large partition since Windows used the two I had made.  On the instructions I was looking at, it said to  make the big partition in "ext4 journaling file system" format, so I did, but then Windows couldn't see it.  So I re-loaded the live Ubuntu, opened Gparted, and created another partition from the big one that contained Ubuntu, and then the rest became "unallocated".  It won't let me format it to NTFS, though, and when I click "New" it says "You cannot have more than 4 primary partitions."  I'm not sure what to do in order to get the one large storage partition that both Linux and Windows can see.
Here are the partitions I currently have:
/dev/sda1 NTFS 14.65 GB (Windows)
/dev/sda2 NTFS 15.00 GB (has Windows' 100 MB reserved on it, I think)
/dev/sda4 ext4 15.00 GB (has Ubuntu on it)
unallocated unallocated 185.31 GB
/dev/sda3 extended 2.93 GB
   /dev/sda5 linux-swap 2.93 GB

Is there a way I can shrink all of these partitions back down to one and just start over?  I wasn't able to follow the instructions right the first time because of some weirdness, but if I could just start fresh, I think they would work.  I don't care about losing data, it's all on an external hard drive, and I've got both OS's already ready to go on flash drives.

---

### Post by coffeecat on 2011-03-16
The "You cannot have more than 4 primary partitions" message is because you have 3 primaries and one extended (sda3). It's a limitation of the mbr partition table which you have. An extended partition is simply a special type of primary partition whose sole purpose is to act as a placeholder for one or more logical partitions. Your extended partition is quite small, containing only the logical sda5 swap partition.

It may be possible to enlarge the extended partition into the unallocated space depending on whether the unallocated space is contiguous to the extended partition.

Boot up the live CD, open Gparted and take a screenshot and post that so that we can see what the situation is. Also, open a terminal and post the output of:

```
sudo fdisk -lu
```That will complement what Gparted shows.

If doing this is inconvenient from the live CD and you can boot into your new Ubuntu installation, you could do both from your HD installation, but you'll have to install Gparted first.

Let's look at that first because it may be easy to do and that will save you from having to re-install everything.

---

### Post by mollycule on 2011-03-17
Sorry for taking so long to reply, I was gone most of the day yesterday.

Attached are two screenshots - one of the GParted window and one of the terminal with the disk info.

---

### Post by coffeecat on 2011-03-17
Thanks for posting those. They do indeed confirm what you posted earlier, but I wanted to be sure of the exact partition layout. Just a few comments on each partition and then a couple of suggestions.

sda1 and sda2 at 14.65 and 15GP respectively are NTFS. The 100MB used in sda2 will be mostly the filesystem itself I would think. Even before you add files, a filesystem uses up some of the available space. However, I think you are right that Windows has put the boot files in sda2 - since the boot flag is on that partition. I've seen the Windows XP installer do that before. I set up a relative's machine with sda1 for the C: drive and sda2 for data. I told the installer to use sda1, but it went and put the Windows boot files on sda2, all mixed up with my relative's personal files and the rest of Windows on sda1. Daft and untidy, as only Windows can be, but usable. I guess this is what it's done to you. Hence my cautionary comments earlier.

The next partition, sda4 (numerically out of order) is a primary and your Ubuntu root partition. You don't need Ubuntu on a primary partition but we'll come back to that.

After that comes the unallocated space of 185GB before the extended partition sda3 which contains the swap partition sda5. 

I can see three options:

1 - If you want to  leave Windows on sda1/2 and Ubuntu on sda4 as they are, you'll have to resize the extended partition backwards into the unallocated space, after which you'll be able to create more logical partitions in the enlarged extended partition. It's not the most efficient way of using your hard drive, but if you want to do that, post back and I'll give you some more details.

2 - Leave sda1 and sda2 as they are. It's a strange way of having Windows running, but it works. Then delete sda4, sda3 and sda5 (thus deleting Ubuntu), after which you can create one big extended partition in all the available space. In the extended partition you then create whatever partitions you need for Ubuntu, and a data partition to be shared between Windows and Ubuntu if you want, and then re-install Ubuntu.

3 - Start over and re-install everything. This gives you a chance to install Windows in a more efficient way. If you do this, I suggest you use Gparted to delete all partitions and then create one NTFS partition only at the beginning of the drive for Windows. Then start the Windows installer and install XP to that one partition. If the Windows installer is presented with only one partition it limits its chances of getting up to mischief. :wink: Having installed Windows, you can then create whatever other partitions you need. I would suggest one big NTFS partition for shared data as sda2, and then an extended partition in the rest of the space for all your logical partitions. Don't forget that Ubuntu's root partition can be a logical one. 

Post back if you need any help with any of that, and I'll be interested if oldfred has any other suggestions or amendments to mine.

One other thing to bear in mind. When using Gparted from the live CD to do anything with your partition layout, remember to right-click on the swap partition first and choose 'swapoff' otherwise you'll find the extended partition locked and you'll be unable to do anything with it.

---

### Post by mollycule on 2011-03-17
Thanks for the help!

I was a little confused about Option 2, like with what format the extended partition would be in and how to make it extended, so I decided to try and delete the Ubuntu partitions and just see what my options were.  GParted won't let me delete them, though; when I select the partition, and go to the Partition menu, the only allowed options are "Manage flags" and "Information." I also have the Disk Utility window open because it looks like I can do some stuff in there, and I selected the extended partition and clicked "Delete partition,"  but it said "Error deleting partition...the daemon is being inhibited."  I'm doing this all off the live version.

Also, if I were to do Option 3, would I be able to use the same product key that I used for the first installation? (I'd still like to have Windows 7) Or would Windows tell me that it's not a genuine key?

Again, thanks so much for the help!

---

### Post by coffeecat on 2011-03-17
> **mollycule said:**
> I was a little confused about Option 2, like with what format the extended partition would be in and how to make it extended

Once you have a large amount of unallocated space that is partitionable, simply click on it (in Gparted), then Partition menu > New, and in the 'Create as' field, choose extended. Don't change the figures on the left in the 'Create New Partition' window. Then you'll get an extended partition filling the whole of the previously unallocated space and you'll be able to create as many logical partitions as you want.

> **mollycule said:**
> , so I decided to try and delete the Ubuntu partitions and just see what my options were.  GParted won't let me delete them, though; when I select the partition, and go to the Partition menu, the only allowed options are "Manage flags" and "Information."

Did you remember to right-click on the swap partition and 'swapoff' as I mentioned? You won't be allowed to do anything until you do.

> **mollycule said:**
>  I also have the Disk Utility window open because it looks like I can do some stuff in there, and I selected the extended partition and clicked "Delete partition,"  but it said "Error deleting partition...the daemon is being inhibited."  I'm doing this all off the live version.

Don't have two partitioners open at the same time. That won't work. In fact that may be what's getting in the way. Disk Utility is excellent for straightforward tasks, but you really need Gparted for this.

> **mollycule said:**
>  Also, if I were to do Option 3, would I be able to use the same product key that I used for the first installation? (I'd still like to have Windows 7) Or would Windows tell me that it's not a genuine key?

You use the same product key, but have you already activated Windows XP on sda1/2? If not, there shouldn't be a problem when you come to activate if you re-install. If you have already activated you should be OK if you are re-installing to the same hardware. Even Microsoft allows you to re-install. Indeed, some would call that an regular necessity! :) But a problem may occur if you try to activate on different hardware from what the original product key was used for. And it all depends on the licence. You're allowed to re-install a retail copy of Windows on different hardware so long as you remove it from the previous machine. OEM install disks are another matter. But I'm not an expert on Windows licensing, so I can't guarantee anything where Microsoft is concerned.

Wanting Windows 7 as well adds a complication I wasn't aware of. Do you mean you want a triple-boot with XP, Win7 and Ubuntu? It's possible but you probably would want to start over with the odd way XP has used your sda1 and sda2 partitions.

Remember that Windows must boot from a primary partition and Windows installers can get mightily confused by the presence of Linux logical partitions. If you want that triple-boot, it needs thinking through.

**EDIT**: by the way. You might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

It might be helpful for you to read through that, including all the links. There's some things there that you don't need, but if you're going to do some serious partitioning involving both Windows and Ubuntu, then you need to be able to understand this stuff.

---

### Post by mollycule on 2011-03-17
Yes, I did forget to turn the swap off! All right, so that works now.  I went ahead and deleted the Windows partitions - I'd rather not waste space.
>  Do you mean you want a triple-boot with XP, Win7 and Ubuntu?
Did I say Windows XP earlier?  Sorry if I did.  I just want Ubuntu and Windows 7. :) Windows 7 is much friendlier with my school's wireless network than XP is, among other things.

So I got it all into a single partition, and then made the unallocated space an extended partition, and then made a 15 GB logical unformatted partition for Ubuntu, with a 15 GB unallocated partition before it for Windows, and then formatted the rest of the space to NTFS, just like the article said to.  I went to go install Windows, and all three partitions showed up (Disk 0 Unallocated Space Extended, Disk 0 Partition 1 Logical, and Disk 0 Partition 2: Storage Logical), but when I clicked on the one for Windows (the first one), it wouldn't let me install it, saying that "Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information."  So I re-loaded Ubuntu and went to GParted to make the Windows partition NTFS in hopes that it would then install on it, only now GParted won't run, it just keeps crashing! It opens, says "searching /dev/sda partitions" on the bottom, and then closes and the ! icon appears up at the top right of the screen and says "Sorry, GParted closed unexpectedly."  If it's not one thing it's another...thank you so much for helping me with this...sorry I'm such a noob D:

---

### Post by oldfred on 2011-03-17
Windows7 needs a good sized partition. I think I have seen recommendations of 30GB for 7 and 20GB for XP. You have to have a primary NTFS partition with the boot flag for it to install.  Did you set up sda1 as primary (it would be if sda1) and NTFS with the boot flag? The first install of windows will not install to a logical partition or sd5 & up, where Ubuntu does not care. It works in primary or logical. Windows will read a NTFS partition for data or a second install can go into a logical but must boot from the primary partition.

NTFS needs about 30% free space for it to work well. At 20% free it starts to slow down and at 10% free just about stops working.

I have had gparted fail to see partitions when windows had set the chkdsk flag on a NTFS partition. My XP booted but gparted would not even see my sda drive. I ran chkdsk from my XP disk and then gparted had no issues. This can occur even with new installs.

---

### Post by coffeecat on 2011-03-18
> **mollycule said:**
> Did I say Windows XP earlier?  Sorry if I did.

No, my mistake. Apologies. I don't know where I got XP from.

> **mollycule said:**
> So I got it all into a single partition, and then made the unallocated space an extended partition, and then made a 15 GB logical unformatted partition for Ubuntu, with a 15 GB unallocated partition before it for Windows, and then formatted the rest of the space to NTFS, just like the article said to.  I went to go install Windows, and all three partitions showed up (Disk 0 Unallocated Space Extended, Disk 0 Partition 1 Logical, and Disk 0 Partition 2: Storage Logical), but when I clicked on the one for Windows (the first one), it wouldn't let me install it.....

OK. Two recommendations to make it simple.

First, take note of what oldfred says about the need for size for Windows 7. 30GB is the recommended minimum but I wouldn't be comfortable with anything less than 50GB. Nor would Windows 7, I guess! :)

Second - remember what I said about trying to install Windows in the presence of logical partitions formatted for Linux? Simple advice - if you want a peaceful life, don't! :)

I suggest either:

Present the Windows 7 installer with a completely blank drive - no partitions at all. It *should* ask you how big you want the C: drive to be. (If it doesn't, back out and try the alternative below.) It will then create 2 partitions, a 100 MB boot partition (which Ubuntu will see as sda1) and your C: partition (which Ubuntu will see as sda2). It will sort out the boot flag for you. Having installed Windows, you'll be able to create your Ubuntu partitions in the spare space.

Or:

Use Gparted to create one and **one only** NTFS partition at the beginning of the drive large enough for use as the Windows C: drive. Leave the rest of the drive unallocated. Install Windows to that partition. Windows 7 will be happy installing to just one partition even though its default if it creates its own partitions is to make a small separate boot partition. Once Windows is installed and working, then and only then use Gparted from the live CD to create the rest of your partitions and install Ubuntu.

By the way - returning to your product key and activation question. You have up to 30 days to activate Windows after installation. The Microsoft server only knows about your use of the product key when your copy of Windows is activated. It's a good idea, therefore, to activate Windows only after you’ve installed Ubuntu, in case something goes wrong and you have to re-install. It avoids having to re-activate, which is when some people have problems.

---

### Post by mollycule on 2011-03-18
Every time I tried to create an extended partition on Linux, GParted would crash after doing it, so I just decided to nix that whole idea and have a 30 GB Windows partition NTFS, a 15 GB Ubuntu Ext4 partition, a 3 GB Linux swap partition, and then the rest be a NTFS Storage partition.  That worked, and I got Windows and Ubuntu installed, they both recognize the Storage drive, and life is great.  

Thanks for all the help!

---

### Post by coffeecat on 2011-03-19
You're welcome. I'm glad it worked.

I find that sometimes Gparted does crash on me from the live CD. Sometimes a reboot or sometimes a different CD or live USB does the trick. Anyway, you found a solution. Happy dual-booting!

---

