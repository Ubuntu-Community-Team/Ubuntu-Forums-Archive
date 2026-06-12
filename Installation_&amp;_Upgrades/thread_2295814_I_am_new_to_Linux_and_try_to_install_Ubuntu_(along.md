---
title: "I am new to Linux and try to install Ubuntu (alongside Windows 7 at this point.) I h"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by Ian_Holton on 2015-09-21
I am new to Linux and try to install Ubuntu (alongside Windows 7 at this point.) I have come unstuck at the first (second, third, fourth.....) hurdle. I hope someone can help.

I shrunk C: under Windows Disk manager to free up 170GB. Then I rebooted via the Ubuntu DVD and hit Install. After several failed attempts due to my ignorance of Linux file structure and terminology differences with Microsoft, I got Ubuntu to say it had installed on a 100GB space that I thought was in the 170GB spare and I had asked it to structure as Ext4 (all completely new to me) and had asked to change to “forward slash” - root directory.

When I rebooted, after a time I got the message "Gave up waiting for root device" followed by many other lines of message amongst which one which said it is “Dropping to Shell” which I guess is the line output rather than the Windows view.

To add to the fun, the PC will no longer boot under Windows, complaining that there is a disk read error.

Should I take my PC to a scrap merchant, or is there hope?

Thanks for any help!

---

### Post by Bashing-om on 2015-09-21
Ian_Holton; Hello; Welcome to the forum.

I bet
> 
Should I take my PC to a scrap merchant, or is there hope?

fixing this issue is no big deal.
As you are learning linux is not Windows, and an altered mind set is required.
Let's look at what we have to work with,
Boot up the liveDVD(USB) to "try ubuntu" mode.
At the desk top key combo ctl+alt+t will yield a terminal.
Please post back the outputs - Between Code Tags - of terminal command:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we can expect that (RE-)installing grub ( GRand Unified Bootloader ) will enable you to boot ubunu, and once booted, we can then have grub pick up the Windows install and chainload the Windows' boot code onto grub's boot menu.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Ian_Holton on 2015-09-22
Bashing-om - many thanks indeed for your reply and the hope that not all is lost! 

Here is the output from the sudo command....

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80f49af4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048      409599      203776   42  SFS
/dev/sda3          409600   637280255   318435328   42  SFS
/dev/sda4       637280256   976771119   169745432   83  Linux

```

Thanks too for the FAQs link - it looks really helpful.
Certainly a new mindset!

Many thanks for your help - I look forward to understanding what the output means.

Ian

---

### Post by yancek on 2015-09-22
The "SFS" under System in the fdisk output shows you are using the windows proprietary "Dyanmic" disk.  It won't work AFAIK unless you change that in windows.  I don't use windows so I don't know how you would do that.   Do you have a windows installation DVD to repair the MBR so you can boot windows.  There might be other ways but you'll have to either wait for a windows user or do an online search for it.  Some good news, you still have your windows partitions.

---

### Post by Bashing-om on 2015-09-22
Ian_Holton; Well;

As you can see the partitions on the hard drive are still there. so no all is not lost and yes there is some hope.
BUT, not a lot more from me unless you want to 'experiment' and see how much I can learn.
what we have here is:
> 
/dev/sda2   *        2048      409599      203776   42  SFS

where: The SFS is for dynamic partitions. You get that from Windows as a proprietary overlay over physical partitions when you use MBR and want more than 4 partitions.
Now as this is proprietary to MicroSoft I do not know how well grub (ubuntu) will play .

I just have no experience with this type.
However, in this install of ubuntu I do see another problem - there has been no provision for a /swap partition for ubuntu to use . If you have 8 gigs of ram and do not intend to hibernate, and not doing heavy duty number crunching; not having a /swap partition is not a issue .
-------------------------------------------

Houston, We may have a problem:
[http://ubuntuforums.org/showthread.php?t=2285603&highlight=SFS](http://ubuntuforums.org/showthread.php?t=2285603&highlight=SFS)
[http://ubuntuforums.org/showthread.php?t=2269149&highlight=SFS](http://ubuntuforums.org/showthread.php?t=2269149&highlight=SFS)
[http://ubuntuforums.org/showthread.php?t=2254808&highlight=SFS](http://ubuntuforums.org/showthread.php?t=2254808&highlight=SFS)

Looks as if the only solution is to revert the SFS partitions. Will not hurt my feelings in the least if we wait for oldfred to comment.

[INDENT][INDENT]there is this fly in the ointment
[/INDENT][/INDENT]

---

### Post by cobalt2 on 2015-09-23
Boot from the Ubuntu LiveCD. At the setup menu select 'Try Ubuntu'. Open up a terminal and install Boot Repair.
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update 
sudo apt-get install -y boot-repair && boot-repair

```
Boot Repair will start automatically. Then follow the instructions, and Boot Repair will delete and rebuild your GRUB. Restart your computer and your GRUB should be in working order.

When running Ubuntu from DVD, your changes will not be saved when the liveCD session ends (except for changes made to your GRUB by Boot Repair), so if you want to use Boot Repair again, you will have to redownload and reinstall it.

---

### Post by Ian_Holton on 2015-09-24
Many thanks for all replies. I tried Cobalt2's suggestion of boot-repair, which seemed to go OK up until closing down to restart when it threw up some problems (rsync or something?) and I hit Return at which point it closed down.

When I power on, it now goes straight to "Press the ESC key to show Startup Menu" and no amount of clobbering the ESC key (or anything else, including my head) shifts it from that screen. Although if I hit ESC enough times it starts to beep back at me.

I guess something radical is needed at this point?

---

### Post by ian-weisser on 2015-09-24
Do you want to recover your Windows install? If so, re-read posts #4 and #5 of this thread. Those posts tell you what you must do first. There is no point fiddling with Ubuntu until you recover your Windows MBR, boot to Windows, and convert those SFS partitions back to ordinary NTFS using Windows tools. Anything else will merely cause more damage.

Or do you want to eliminate your Windows install, forever deleting all your data? If so, get out your Ubuntu install media and reinstall properly.

---

### Post by Ian_Holton on 2015-09-25
> **ian-weisser said:**
> Do you want to recover your Windows install? If so, re-read posts #4 and #5 of this thread. Those posts tell you what you must do first. There is no point fiddling with Ubuntu until you recover your Windows MBR, boot to Windows, and convert those SFS partitions back to ordinary NTFS using Windows tools. Anything else will merely cause more damage.

Or do you want to eliminate your Windows install, forever deleting all your data? If so, get out your Ubuntu install media and reinstall properly.

I'd be happy to eliminate Windows install. But I can't see how I can install Ubuntu from my Ubuntu install media if boot can't get past the "Press the ESC key to show Startup Menu"? As I understand it I need to get to that page before I can select the Ubuntu media?

---

### Post by ian-weisser on 2015-09-25
> **Ian_Holton said:**
>  "Press the ESC key to show Startup Menu"
That seems like Windows...you are already past EFI and the choice to boot from something else.

---

