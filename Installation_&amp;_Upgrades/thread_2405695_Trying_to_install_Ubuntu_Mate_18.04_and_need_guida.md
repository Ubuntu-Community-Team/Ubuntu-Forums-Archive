---
title: "Trying to install Ubuntu Mate 18.04 and need guidance please"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2018-11-09
I am starting my bi-annual upgrade to the latest LTS (18.04.1) on a Win 10 Home Dell XPS i7 with 16GB ram, but am am a bit out of practice (and have never developed any competence that sticks). 

I have put this into "New to Ubuntu" even though I am not exactly new to Ubuntu, but my limited experience and my declining memory make it appropriate for me. Your patience (and simply worded replies) appreciated.

Using a bootable installation USB stick, I have the "Installation Type" screen open and it is showing me the following:

Free Space 1MB
/dev/sda1      efi       (size)524MB / (used) 55MB    Windows Boot Manager
/dev/sda2      fat32       41/41   [all size/used #'s hereafter are MB]
/dev/sda3      (blank)   134/unknown
/dev/sda4      ntfs       786/313
/dev/sda5      ntfs       989321/98659
Free Space 0MB
/dev/sda6      ntfs       925/438
/dev/sda7      ntfs       8467/7684
Free Space 1MB

Hereafter Win 10 may not be used very much, but I want to keep it as a dual boot. I think I want to devote approx 90% of the 1TB to UM 18.04

Since this is a UEFI machine, are there some UEFI/BIOS adjustments I need to make before proceeding further (and backing up a few steps if need be)?

If so, and once done, do I need to shrink the Windows part done to 100GB or so, or do I accomplish that by reducing sda5 to that approx amount.

Then I will need to make some allocations (in what I expect will become sdb?) for some or all of:

1)boot loader (or is that already taken care of above)

2) swap

3) system

4) files/data (I want to have this separated from /system)

5) any other?

As you can see, I am barely aware of some of the potential issues, and I will appreciate any guidance on how to proceed with respect to the above, as well as any suggestions you might make on how to do this. Thanks in advance.

---

### Post by oldfred on 2018-11-09
Only use Windows to shrink the NTFS partition and reboot immediately to let it run chkdsk which is required after any resize. 
Make sure Windows fast start up is off. Even if you turned it off before, Windows updates (which may be in background) may turn it back on.
Do not shrink NTFS too much. It really likes 30% free and at 10% free, your defrag may take forever.

New versions of Ubuntu now use a 2GB swap file. But if swap partition is found, it will use it. 

Since UEFI, your ESP - efi system partition is for UEFI boot. That is not Ubuntu's /boot and most desktops do not need a separate partition for /boot. 

Since UEFI system & UEFI installs, you want to make sure all new installs are also UEFI. And how you boot install media is then how it installs. So always boot in UEFI boot mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You always want to have good backups, both Windows and Ubuntu data. I do not back up Ubuntu system as I can reinstall very quickly but have backed up everything else, data, settings & list of installed apps, so I can to restore system in less than an hour.
I have also learned to backup the ESP. Multiple installs of Ubuntu will overwrite /EFI/ubuntu folder. But I want my main working install as default so I have to regularly restore that. You can totally reinstall grub from system you want as default, but really only have to edit a 3 line the /EFI/ubuntu/grub.cfg with correct UUID & partition.

---

### Post by Odyssey1942 on 2018-11-10
Thanks. When I opened Disk Management and chose shrink for the 921.38GB for the C: OS, a shrink screen popped up and apparently did some sort of analysis and calculated the "size of available shrink space" as 467GB and on the assumption that I should not reduce it to approx 30%, went ahead with the "available" amount and it is now working on the shrink.

got to thinking about it and am wondering why Windows felt that such a large % was the "available" amount, and also whether I could have gone for shrinking it to, say, 300GB. 

If so, is it too late to accomplish this, and if not how best to go about it?

Edit: Have just received a message saying, "There is not enough space available on the disk to complete this operation" Given that, according to the above, only 98 GB are in use and 989GB are free, what is the issue here?

---

### Post by oldfred on 2018-11-10
This may be older but still applies. Windows will not move certain files. But if you change some settings then it should work. 

       Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
30GB at an absolute minimum and you want at least 30% free inside the NTFS partition for Windows to work well
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Odyssey1942 on 2018-11-10
This is slow and not much progress. I wonder if there are not better alternatives.

Since I do not expect to use Windows very much, but just want to keep the license in an active state, what about replacing the 1T HDD, with a 120GB SSD? I can use 60GB for Win 10 with a new install and the other half for U Mate 18.04 new install, then reformat the HDD for a data drive for both OS's.

Alternatively, do a new Win10 install as sda but restrict it to say 100GB during the install, and install U Mate as sdb using the balance. This would have the advantage of starting fresh with both

What do folks think about these options?

---

### Post by oldfred on 2018-11-10
One user posted that he would buy a new system and before even booting Windows remove HDD and install SSD. Then later sell system with "brand" new unused Windows. He obviously upgrades system regularly.

SSD makes system a lot faster, booting & loading large files. Somehow my typing has not improved with SSD? Or big bottleneck is still between keyboard & chair. :)

---

### Post by Odyssey1942 on 2018-11-11
For Fred, know what you mean about typing. Similar issues here.

For all others as well, while reading and researching this, I continue to work on shrinking the HDD and have followed all the guidance I can find, but so far have only shrunk the Win partition to approx 655GB (can't look right now as defrag is running on that computer.) This is just too much to devote to what I expect will be limited use of Win10.

Have thought of another option which is to use the SSD only for Ubuntu Mate and do a clean install of win10 on the HDD after setting up a new partition of approx 200GB for it.

This seems to me to (maybe have advantage of?) preserve the original HDD for booting Windows and gives all the space on the SDD for UM.

How does this sound? Any obvious problems to those who understand this stuff better than me? 

BTW, if any others want to jump in here, hopefully whose instructions are not so hard for me to understand as are OldFred's. He clearly knows this stuff, but most of his (probably excellent) guidance is just too cryptic/elevated for me to comprehend. Thanks

---

### Post by slickymaster on 2018-11-11
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2018-11-11
With two drives best to disconnect one, when installing Windows. It likes to default to put its Boot partition on drive seen as default in UEFI/BIOS. And some have reported that it just erases whatever is one other drive to add its Boot partition as it does not correctly see ext4 partitions.

For both Windows & Ubuntu, how you boot install media UEFI or BIOS, is then how it installs. Your UEFI should give two boot options.

Post what you need clarifying & I will do my best to add info, or others can help add info.

---

### Post by Odyssey1942 on 2018-11-11
Fred, thanks for yours. My purpose in the above posts is firstly to get some guidance from more experienced others on which of these alternatives makes more sense to those who better understand all of this and can see the advantages of one over the other, or potential problems. Secondarily to later obtain help when, whatever alternative is chosen, the inevitable problems arise.

So, in the absence of such opinions, I am leaning toward using the SSD just for Ubuntu Mate, and using the HDD as the boot drive for Windows. (1) Do you see any significant reasons why not to do this?

If not, and since I have been unable to shrink the Win partition to less than 628GB (with 545GB free) I guess I need to reformat the HDD and do a clean install of Win10 into a partition of say, 200GB (although it may not need to be this large). (2) Do you see a preferred alternative?

---

### Post by oldfred on 2018-11-11
Just be aware that Windows in UEFI boot mode needs a variety of partitions and gpt.  
Do not know if you just install it, it then it will let you shrink it. 
Most mount turning off hibernation and some of the other settings as linked above (post #4) then allows more shrink. And some have posted that third party Windows tools may allow more shrink like EaseUS Partition Master.

I always thought keeping Windows & Ubuntu on separate drives was a good idea. But most have only one SSD and want both on that drive for speed. 
I have not installed Windows since XP in 2006, so do not know details of new versions.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

