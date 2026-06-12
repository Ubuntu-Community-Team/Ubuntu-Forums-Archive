---
title: "A Little Help With Partitioning On Fresh Install Please :D"
date: 2022-03-02
forum: Installation &amp; Upgrades
---

### Post by ddddd5 on 2022-03-02
Hello all !

(For **TL;DR** version, please skip to the part below the image)

I'm about to perform a clean ubuntu install on a new drive. The last time I did it was ~6 years ago, and the partitions hadn't turned out as intended since I was a n00b (still am:grin:)


Also, it was all kinds of wrong, owing to having ubuntu installed first, and then try add win 10 alongside. Oh and it was in Master Boot Record partitioning, which had made things even more difficult to the best of my recollection, but I had made it work somehow.

I've been using it ever since, and this is what it looks like(I know, I know:lol:):

[IMG]https://i.imgur.com/Zz27dSg.png[/IMG]


Now I'll do it in UEFI mode only(something I've never done before) in the BIOS (instead of uefi+legacy), and the installation drive in GUID Table Partition.

I'd like to first have the **win 10 partition for X gigabytes **(since I'll install windows first, and then have ubuntu alongside), and then the **ubuntu partition for Y gigabytes**, and then a separate partition for **media and stuff for Z gigabytes**. And finally a swap partition.** I want to do it all manually in GParted before i start installing windows**. How should my partition table look like to yield the desired result ? Oh and I'd probably want **/home**, should it be under "**/**" (root?) ? Although I have /home in my current install, can't see it in the partition table up above. Can the root partition actually come after the windows partition ??

Any help is much appreciated ! Very many thanks in advance ! :D

---

### Post by ubfan1 on 2022-03-03
Ensure your machine can use UEFI mode (All since 2012 can with secure boot, and some even earlier without secure boot).  Put a gpt partition table on the new disk, then let the Windows install create what it needs, probably an EFI partition, a Windows reserved partition, and a Windows partition.  Maybe Windows will put more partitions on the disk, who cares with gpt.  The big Windows partition should then be shrunk with Windows tools, chkdsk run, power options selected to avoid hibernation, etc.  I suppose you could put an EFI partition on the new disk before Windows, so you can make it definitely big enough to hold the 10 MB or so of Ubuntu bootloaders, The recommended size 300-500MB, but probably even the default Microsoft EFI will be big enough.

Then run the Ubuntu install, and the free space you made from shrinking the Windows partition will be used.  Again, if you want a separate swap partition, make it now, because the latest ubuntu installs will use a swap file.  Doesn't really matter where the root / partition is on the disk.  /home is useful to separate your files from the system when you want to reinstall a new system, but I like 60GB roots, so with your space, I'd just make a bigger root and forget /home.

---

### Post by oldfred on 2022-03-03
With UEFI you cannot just create a NTFS partition for Windows. It wants multiple partitions.
You may want to create ESP first so it is a bit larger than Windows defaults. Then install Windows & let it create all the partitions it wants.
Use Windows to shrink its NTFS partition and reboot so it can run a required chkdsk after any resize.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 

Then you can create your / & data partitions with gparted and use Something Else to install Ubuntu.
You may want two data partitions, one NTFS for data you want to share with Windows and another ext4 just for Linux. Then / can include /home and be smaller, depending on whether using snaps or not which need more space.
Best to only mount Windows "c: drive" partition as read only if using it at all in Linux. 
And Windows fast start up must be off to use NTFS partitions from Linux.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

I use Kubuntu and 20.04 now uses 10GB including /home. But all data normally in /home including Firefox & Thunderbird profiles are in separate data partition. And I do not have snaps.

---

### Post by ddddd5 on 2022-03-03
Oh boy.. I'm now more confused than when I started :lol: I also forgot to ask about a **/boot** partition (which wasn't used above, but in a linux mint install I had done previously by the looks of it), do I need to make a separate **/boot **partition manually ? Or in UEFI / GPT, I don't need to, at all ?


So the best way you guys are saying is, to put a gpt partition table on the new disk (done), have the windows installed, use windows to downsize the windows NTFS partition (marked with [the red rectangle in here ?]("https://i.imgur.com/uN20vrn.png") ) , and then install ubuntu in the remaining space ? Do I need to worry about going back to GParted to create the rest of the partitions at that point ? Best to just start the Ubuntu installer, no ? Choose something else, put a [SIZE=4]**/ **[/SIZE]partition, put an additional partition for** media and stuff (Z)**, and then that's it ? Where should the swap partition go :lol: ?

Oh and one last thing. This new drive is nvme, is there anything to look out for ?

And finally thanks *a lot* for the replies. I've learned quite a bit of new stuff already.

---

### Post by grahammechanical on 2022-03-03
If you load the Ubuntu live session (Try Ubuntu) and run the Disks utility you will see the partitions that Windows has created on that nvme drive. With UEFI and GPT there will be an EFI system partition. That is where Windows has put its boot files and that is where Ubuntu will put its boot files. It is only if you make the mistake of installing Ubuntu in MBR/Legacy/CSM mode that a boot partition will be created. You will then have difficulty dual booting Windows and Ubuntu. 

Regards

---

### Post by ddddd5 on 2022-03-03
> **grahammechanical said:**
> With UEFI and GPT there will be an EFI system partition. That is where Windows has put its boot files and that is where Ubuntu will put its boot files. 



Ahhhhh, this makes so much sense, and i remember now :KS I needed the manually created boot partitions for the MBR partitioning in the older PC :) So because ubuntu shares its boot files in the EFI partition created during windows install, on a disk with GPT, I don't need to worry about creating a /boot partition. Got it &#128077;


> **grahammechanical said:**
> 
It is only if you make the mistake of installing Ubuntu in MBR/Legacy/CSM mode that a boot partition will be created. You will then have difficulty dual booting Windows and Ubuntu. 

Regards

Oh yes, very much so. I had to do a GRUB bootloader repair from a live USB session. But maybe it was more because windows went in after, and its bootloader messed up GRUB.

---

### Post by oldfred on 2022-03-03
Ubuntu's default install now is only / (root).
But with UEFI it also wants the ESP which is the EFI system partition FAT32. 
Ubuntu desktop installs do not normally need a separate /boot partition, but if you are using full drive encryption with LVM, then you may need a separate /boot partition.
Installer also defaults to a swap file of 2GB, many suggest a 4.1GB swap partition. I typically make it the last partition  (furthest right) so ESP which should be fixed is first, swap which should be fixed is last and then you can later adjust partitions if needed. 

If planning on moving/changing a lot of partitions LVM offers advantages, but is more complex, and really should be on its own drive, not with Windows as Windows will not work with LVM.

---

### Post by ddddd5 on 2022-03-03
> **oldfred said:**
> 
But with UEFI it also wants the ESP which is the EFI system partition FAT32. 

Uhh.. So **grahammechanical **has mentioned above that with GPT partitioning, windows and ubuntu share their boot files in the EFI system partition created by windows now, so after the windows install is complete, I don't need to do anything manually before commencing the ubuntu install, is that right ? 
> **oldfred said:**
> 
Ubuntu desktop installs do not normally need a separate /boot partition, but if you are using full drive encryption with LVM, then you may need a separate /boot partition.

Think I won't be going that advanced yet, but even so thanks for the tip.
> **oldfred said:**
> 
Installer also defaults to a swap file of 2GB, many suggest a 4.1GB swap partition. I typically make it the last partition  (furthest right) so ESP which should be fixed is first, swap which should be fixed is last and then you can later adjust partitions if needed.

That is a very good tip, thank you very much ! 
 > **oldfred said:**
> 
If planning on moving/changing a lot of partitions LVM offers advantages, but is more complex, and really should be on its own drive, not with Windows as Windows will not work with LVM.
No, I just want to make the partitions right the way I want on the first try, and leave them be, rather than having to fiddle with them later and risk breaking something.

---

### Post by oldfred on 2022-03-03
My  now retired laptop only had 1.5GB of RAM. If I loaded more than one larger app and a couple of smaller apps, I could tell it went to swap. Screen would turn gray for a second or two and it would be very slow. I learned not to use a lot of resources and my 4GB system never used swap.
The only reason for swap equal to RAM is if hibernating. And hibernating not really recommended. You typically can boot as fast using NVMe drive.

My Kubuntu system right now says I have 13GB of RAM available for new apps. Linux does caches apps in RAM so evenually RAM may fill, but not with active applications. Only if editing video or very large photos and a few other cases may you use all of RAM for working application.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ free [/COLOR]
              total        used        free      shared  buff/cache   available 
Mem:       16274376     1347952    11528548      719556     3397876    13868876 
Swap:       1425444           0     1425444
[/FONT]
```

My last reboot with Kubuntu which is a bit faster than full cold boot or Ubuntu. And I have made some settings changes to eliminate things I do not want or use that slow booting.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 3.795s (kernel) + 5.773s (userspace) = 9.569s  
graphical.target reached after 5.760s in userspace
[/FONT]
```

There are multiple posts on slow boot, but then many suggested settings changes.
I do now prefer Kubuntu which is a bit lighter weight than Ubuntu but still full featured.

---

### Post by ddddd5 on 2022-03-03
Alright then, gotcha.

I'm pretty open minded when it comes to different distros, but why does support for newer versions end so soon compared to ubuntu tho :confused: Had a look at both ubuntu mate and kubuntu, but security and maintenance updates for both of them end in April '23..

With all that said, snappiness is the most important metric for me in a DE, since I'm a casual user. I'm very happy with 16.04 in my current setup in this regard. However, 20.04 wasn't really snappy on a live session, which got me concerned.

---

### Post by yancek on 2022-03-04
>  I'm pretty open minded when it comes to different distros, but why does  support for newer versions end so soon compared to ubuntu 

It's a decision made by the developers.  It takes a lot of time and work to maintain support so that is why Ubuntu has LTS versions (releases in April of even numbered years) and other Ubuntu derivatives have shorter support times (3 years).

---

### Post by ddddd5 on 2022-03-04
> **oldfred said:**
> Ubuntu's default install now is only / (root).

Installer also **defaults to a swap file of 2GB**, many suggest a 4.1GB swap partition.

So I just had a one last look before proceeding with the install, and this bit here caught my eye.

Does this mean with the new versions of ubuntu (take 20.04 for example), I don't need to make a separate swap partition *at all*, if I'm content with 2 GB of swap ? It just automatically uses some space (2 GB) under [SIZE=4]**/**[/SIZE]  , and I don't need to touch anything during install to make use of swap ?

---

### Post by oldfred on 2022-03-04
If it finds a swap partition, it will automatically use it.
I have  a swap on HDD, but an install to my external SSD wanted to use the swap partition on internal HDD. That would only work as long as booting external on same system. But I do not do that, so I have to either use default swap file or create swap partition on external drive.

Its easier to make whatever choice you want. But you can convert later.
But creating swap file after the install requires multiple terminal commands and edit of fstab.
I find I never use swap with my normal use of system, so swap is more for protection if some process ever runs away. But I typically close apps I am not using, so do not have a lot of active different apps in RAM running, but many may be cached in RAM and then reload quickly.

---

### Post by ddddd5 on 2022-03-04
> **oldfred said:**
> 
But creating swap file after the install requires multiple terminal commands and edit of fstab.


Ouch.

So I get no swap at all if i don't create a separate swap partition during install ? Honestly, I'm better of creating one during install then.


One more question,

To use a partition (read *and* write)  both by windows *and* ubuntu, I should partition it as NTFS, is that right ?

---

### Post by oldfred on 2022-03-04
If you do not have a swap partition, it automatically creates a swap file.
Its just if you want to change from a partition to a file, it is a bit of a hassle.

Windows only reads NTFS (and FAT32). So the shared partition should be NTFS.
FAT32 has limits, so only for smaller partitions with smaller files.
You must have Windows fast start up off for Ubuntu to be able to see NTFS partitions.
Fast start up sets hibernation flag which then prevents Linux NTFS driver from writing into it.

---

### Post by ddddd5 on 2022-03-05
Sooo, reporting back from new dual boot [IMG]https://i.imgur.com/MToUhfG.png[/IMG] :D

Thanks for all the help, everything went just [IMG]https://i.imgur.com/AnHUYNr.png[/IMG]

Now just performing the minor modifications I need, and ironing out funny-weird bugs as is the custom :)

---

