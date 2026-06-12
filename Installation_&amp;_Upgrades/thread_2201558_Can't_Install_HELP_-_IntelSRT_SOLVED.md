---
title: "Can't Install HELP - IntelSRT SOLVED"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by Brendan_Doyle on 2014-01-24
I'm having trouble getting past this, when I press change, the  installation closes. It tells me I need to select a root in the  partition menu. I am trying to install Ubuntu and get rid of windows, I  noticed when I went to install it doesn't ask me if I want to replace  Windows as well.

[ATTACH=CONFIG]249712[/ATTACH]

---

### Post by Bashing-om on 2014-01-24
Brendan_Doyle; Hi !

Back up to the partitioning set up, choose the partition you want as "root" -> change ->and in the next screen input '/' -no quote marks - in the "use as" box. [to the installer root = / ]

No option to install along side Windows: Maybe, the installer thinks you know what you are doing in the "something else" method of installation (?). Did you see that option prior to choosing "something else" ?

[INDENT]The install wizard is smart, but
[INDENT][INDENT][INDENT]sometimes it wants things explained - explicitly.[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2014-01-24
Hello!

Please be considerate of those with low bandwidth or periodic data restrictions and use the attach functionality (the paper clip icon) rather than pasting large images.

Thanks.

---

### Post by Brendan_Doyle on 2014-01-24
I didn't ever see a partitioning set up. I don't know if this is useful information, but I am trying to put Ubuntu on an HP pavilion DM4-3090SE. I heard that the 4 partitions this computer comes with make an issue, and as suggested I deleted my HP_TOOLS partition, but it's still not working.

---

### Post by Brendan_Doyle on 2014-01-24
I did a terminal code, and it came up with this.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x99e03f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   933101567   466345984    7  HPFS/NTFS/exFAT
/dev/sdb3       933101568   968433663    17666048    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted /dev/sda print all
Error: /dev/sda: unrecognised disk label
```

---

### Post by Brendan_Doyle on 2014-01-24
This is what GParted is showing.







[ATTACH=CONFIG]249713[/ATTACH][ATTACH=CONFIG]249714[/ATTACH]

---

### Post by fantab on 2014-01-24
Post the output of:

```
sudo parted -l
```

---

### Post by Brendan_Doyle on 2014-01-24
> **fantab said:**
> Post the output of:

```
sudo parted -l
```

Here it is.

```
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Model: ATA ST9500423AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   478GB  478GB   primary  ntfs
 3      478GB   496GB  18.1GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

---

### Post by QIII on 2014-01-24
Hello again.

Don't mean to nag, Brendan_Doyle.  Looks like you are new to the forums.

It helps others distinguish what you are posting from the terminal and what you are typing if you put all code between code tags.

So please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Cheers!

---

### Post by fantab on 2014-01-24
> Error: /dev/sda: unrecognised disk label                                  

Is there another HDD in the picture? or is it a SSD? If its a SSD, did it come pre-installed?

What Windows do you have, Eight or Seven? Did it come pre-installed?

---

### Post by Brendan_Doyle on 2014-01-24
> **fantab said:**
> Is there another HDD in the picture? or is it a SSD? If its a SSD, did it come pre-installed?

What Windows do you have, Eight or Seven? Did it come pre-installed?

This computer has a 500gb hybrid drive with a SSD partition, or something like that. Windows 7 and it came pre-installed.

[http://www.amazon.com/HP-dm4-3090se-14-0-Inch-Screen-Laptop/dp/B006OEL9GU](http://www.amazon.com/HP-dm4-3090se-14-0-Inch-Screen-Laptop/dp/B006OEL9GU)

---

### Post by slooksterpsv on 2014-01-24
The red exclamation on the /dev/sdb2 (the 446GB volume) tells me that's where Windows is installed and it: 
1 has a hibernation file (Windows 8 no longer "shuts down" to get rid of the hibernation file you have to choose restart) or 
2 has errors on the disk that check disk needs to correct.

/dev/sda seems like it's an SSD - respond to fantab's questions posted above, that will help us out greatly.

EDIT: Ahh I see the /dev/sda doesn't have a partition table meaning it must be brand new (or it's been wiped) most likely brand new; you will have to create either an MBR or GPT on that drive to use it. if you don't want to use that. Restart in Windows, run the check disk, retry the Ubuntu and let us know.

---

### Post by Brendan_Doyle on 2014-01-24
> **slooksterpsv said:**
> The red exclamation on the /dev/sdb2 (the 446GB volume) tells me that's where Windows is installed and it: 
1 has a hibernation file (Windows 8 no longer "shuts down" to get rid of the hibernation file you have to choose restart) or 
2 has errors on the disk that check disk needs to correct.

/dev/sda seems like it's an SSD - respond to fantab's questions posted above, that will help us out greatly.

EDIT: Ahh I see the /dev/sda doesn't have a partition table meaning it must be brand new (or it's been wiped) most likely brand new; you will have to create either an MBR or GPT on that drive to use it. if you don't want to use that. Restart in Windows, run the check disk, retry the Ubuntu and let us know.

It hasn't been wiped and its not brand new, it's used for windows system files I think, go to the link I posted, this laptop has a 20gb mSATA.

---

### Post by fantab on 2014-01-24
> **Brendan_Doyle said:**
> This computer has a 500gb hybrid drive with a SSD partition, or something like that. Windows 7 and it came pre-installed.

Okay.

Firstly, Check in your BIOS for 'SATA MODE' or HDD mode and tell us what it is set to: RAID or AHCI. 
If it is set to RAID then there is good chance that you have IntelSRT, which uses a sort of RAID technology to use SSD as a 'cacheing' device. This 'cacheing' makes Windows fast.
You have to disable IntelSRT in BIOS and set the SATA Mode to AHCI. The benefit of this is that you can free up your SSD and use it to install Ubuntu. OS will boot faster from SSD.
Ubuntu will not install easily if IntelSRT is enabled. If you like 'cacheing' service in Windows then you can use a 2-4gb USB drive to achieve the same.

Secondly check and make sure your Windows is not Hibernating. If it is then [disable Hibernation]("http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html").

Now boot with Ubuntu Live DVD/USB, install and tell us what options does it give....

---

### Post by Brendan_Doyle on 2014-01-24
> **fantab said:**
> Okay.

Firstly, Check in your BIOS for 'SATA MODE' or HDD mode and tell us what it is set to: RAID or AHCI. 
If it is set to RAID then there is good chance that you have IntelSRT, which uses a sort of RAID technology to use SSD as a 'cacheing' device. This 'cacheing' makes Windows fast.
You have to disable IntelSRT in BIOS and set the SATA Mode to AHCI. The benefit of this is that you can free up your SSD and use it to install Ubuntu. OS will boot faster from SSD.
Ubuntu will not install easily if IntelSRT is enabled. If you like 'cacheing' service in Windows then you can use a 2-4gb USB drive to achieve the same.

Secondly check and make sure your Windows is not Hibernating. If it is then [disable Hibernation]("http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html").

Now boot with Ubuntu Live DVD/USB, install and tell us what options does it give....

I dont think I could find what you wanted, here are some pics from my BIOS.

[ATTACH=CONFIG]249715[/ATTACH][ATTACH=CONFIG]249716[/ATTACH]

---

### Post by Brendan_Doyle on 2014-01-24
So is there any hope of me getting Ubuntu onto my laptop, or should I just give up? lol

---

### Post by fantab on 2014-01-25
That is ok...Generally OEMs use SSD as a 'cacheing' device with help from IntelSRT. Looks like you don't have it.

Does your Windows 'Hibernate'?

From Windows Disk management utility, in Windows, can you show the screenshot of both your SSD and HDD partitions?

---

### Post by Brendan_Doyle on 2014-01-25
> **fantab said:**
> That is ok...Generally OEMs use SSD as a 'cacheing' device with help from IntelSRT. Looks like you don't have it.

Does your Windows 'Hibernate'?

From Windows Disk management utility, in Windows, can you show the screenshot of both your SSD and HDD partitions?

[COLOR=#222222]I don't think it's hibernating because i shut off windows completely before booting ubuntu. Here is the screenshot.. I am also downloading Fedora 20 and going to see how that goes.[/COLOR]

[ATTACH=CONFIG]249719[/ATTACH]

---

### Post by fantab on 2014-01-25
Run 'chkdsk' on your HDD from windows: [**how to**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html")
Then Shrink one of your Windows Partition to make space for Ubuntu: [**how to**]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")
Leave the newly created space as 'unallocated'.
Run 'chkdsk' again. And reboot your Windows a couple of times.

Boot Ubuntu in "Try Ubuntu' mode. Open Gparted, Select 'unallocated/empty space' and make an EXTENDED Partition. After you have created an extended partition you will still see equal amount of 'unallocated space', its normal. Its where subsequent Logical partitions will be created.
Install Ubuntu from desktop... tell us if you can proceed.

Be careful with Fedora its installer is bit tricky and you might end up wiping out Windows.

By the way, your screenshot does not show SSD? See if you can find it in Gparted.

---

### Post by Brendan_Doyle on 2014-01-25
> **fantab said:**
> Run 'chkdsk' on your HDD from windows: [**how to**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html")
Then Shrink one of your Windows Partition to make space for Ubuntu: [**how to**]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")
Leave the newly created space as 'unallocated'.
Run 'chkdsk' again. And reboot your Windows a couple of times.

Boot Ubuntu in "Try Ubuntu' mode. Open Gparted, Select 'unallocated/empty space' and make an EXTENDED Partition. After you have created an extended partition you will still see equal amount of 'unallocated space', its normal. Its where subsequent Logical partitions will be created.
Install Ubuntu from desktop... tell us if you can proceed.

Be careful with Fedora its installer is bit tricky and you might end up wiping out Windows.

By the way, your screenshot does not show SSD? See if you can find it in Gparted.

I don't have a problem with getting rid of windows if i have to. I couldn't even get fedora to boot though, I couldn't get ubuntu to boot until i used its boot from cd help tool. how much memory should i shrink? can i "unshrink" the memory if this doesnt work?

---

### Post by Brendan_Doyle on 2014-01-25
I shrunk 27000MB. Now if this doesn't work how am I supposed to reallocate this unallocated data? it doesn't appear as if I can.

---

### Post by slooksterpsv on 2014-01-25
When you go into disk management, if you delete the 27000MB volume where it says Unallocated 27000MB (27GB approx), you can right-click on the partition you took the space from and choose Extend volume... and take up the rest of that space. You're not the only one having install issues. I am but due to the Radeon HD 8400.

---

### Post by Brendan_Doyle on 2014-01-25
> **fantab said:**
> Run 'chkdsk' on your HDD from windows: [**how to**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html")
Then Shrink one of your Windows Partition to make space for Ubuntu: [**how to**]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")
Leave the newly created space as 'unallocated'.
Run 'chkdsk' again. And reboot your Windows a couple of times.

Boot Ubuntu in "Try Ubuntu' mode. Open Gparted, Select 'unallocated/empty space' and make an EXTENDED Partition. After you have created an extended partition you will still see equal amount of 'unallocated space', its normal. Its where subsequent Logical partitions will be created.
Install Ubuntu from desktop... tell us if you can proceed.

Be careful with Fedora its installer is bit tricky and you might end up wiping out Windows.

By the way, your screenshot does not show SSD? See if you can find it in Gparted.

I did what you said and it's still not working. It wont even let me choose /dev/sdb as a device for bootloader. If I hit change or + the window install closes. If I hit - it says what it's been saying the whole time no root file.

---

### Post by Brendan_Doyle on 2014-01-25
I do not see this when trying to install. 





[ATTACH=CONFIG]249720[/ATTACH]

---

### Post by fantab on 2014-01-25
That is because Ubuntu installer is not seeing your Windows. Usually this means either Hibernating Windows or there not being any space for Ubuntu to install. 

Can you see the last option "Something Else"?

I am running out of ideas. Go through the 'oldfred's' post again.

Also try to find out where that SSD is... check with Gparted. (I suspect the issue is with SSD and cacheing.)
[http://www.thewindowsclub.com/enable-disable-disk-write-caching-windows-7-8](http://www.thewindowsclub.com/enable-disable-disk-write-caching-windows-7-8)

---

### Post by slooksterpsv on 2014-01-25
Don't SHUTDOWN your Windows computer as this makes the hibernation file. Instead you have to RESTART in order for it to not create a hibernation file. You can disable SHUTDOWN from creating it, but yeah they made hibernation the default for "speed".

---

### Post by Brendan_Doyle on 2014-01-25
Restart didn't change anything over just shutting down and booting. It's safe to say this isn't because Windows is hibernating. Did you guys not see the 20gb recovery partition? That's my ssd, and it holds recovery files.

Heres some screenshots of the farthest I can get in install and everything I see.

[ATTACH=CONFIG]249721[/ATTACH][ATTACH=CONFIG]249722[/ATTACH][ATTACH=CONFIG]249723[/ATTACH]

---

### Post by Brendan_Doyle on 2014-01-25
Should I try ubuntu 12.04 LTS?

---

### Post by fantab on 2014-01-25
```
sudo fdisk -l

**[COLOR=#a52a2a]Disk /dev/sda: 32.0 GB[/COLOR]**, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6000000

**[COLOR=#a52a2a]Disk /dev/sda doesn't contain a valid partition table[/COLOR]**

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x99e03f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   933101567   466345984    7  HPFS/NTFS/exFAT
/dev/sdb3       933101568   968433663    17666048    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted /dev/sda print all
Error: /dev/sda: unrecognised disk label
```

```
sudo parted -l
**[COLOR=#b22222]Error: /dev/sda: unrecognised disk label[/COLOR]**                                  

Model: ATA ST9500423AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   478GB  478GB   primary  ntfs
 3      478GB   496GB  18.1GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

Look, you have a Hybrid Hard Disk or SSHD, which combines both HDD and SSD. 
The SSD part is most likely being used as a cacheing device. This process takes place with either IntelSRT or any other specific software, usually HDD/SSD OEM.
Your Windows is using it. So it uses either IntelSRT or some ohter software. Find out what it is? Look in HpTools or installed programs in Windows.

AFAIK this 'cacheing' is done by some implementation of RAID. Unless this is disabled it will be difficult to install Ubuntu. 
You can try disabling RAID with:
```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```

...run from the Live Ubuntu. Not really sure that it will work. Give it a try.

---

### Post by Brendan_Doyle on 2014-01-25
> **fantab said:**
> ```
sudo fdisk -l

**[COLOR=#a52a2a]Disk /dev/sda: 32.0 GB[/COLOR]**, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6000000

**[COLOR=#a52a2a]Disk /dev/sda doesn't contain a valid partition table[/COLOR]**

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x99e03f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   933101567   466345984    7  HPFS/NTFS/exFAT
/dev/sdb3       933101568   968433663    17666048    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted /dev/sda print all
Error: /dev/sda: unrecognised disk label
```

```
sudo parted -l
**[COLOR=#b22222]Error: /dev/sda: unrecognised disk label[/COLOR]**                                  

Model: ATA ST9500423AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   478GB  478GB   primary  ntfs
 3      478GB   496GB  18.1GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

Look, you have a Hybrid Hard Disk or SSHD, which combines both HDD and SSD. 
The SSD part is most likely being used as a cacheing device. This process takes place with either IntelSRT or any other specific software, usually HDD/SSD OEM.
Your Windows is using it. So it uses either IntelSRT or some ohter software. Find out what it is? Look in HpTools or installed programs in Windows.

AFAIK this 'cacheing' is done by some implementation of RAID. Unless this is disabled it will be difficult to install Ubuntu. 
You can try disabling RAID with:
```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```

...run from the Live Ubuntu. Not really sure that it will work. Give it a try.

Yes I told you guys quite a while ago I have a Hybrid Hard Drive. SSHD. And remember, I deleted HP_TOOLS to get rid of a partition. I'll try your code.

EDIT: Been reading reviews on amazon. This computer has IntelSRT, and there is some way to shut it off, just not sure how.

EDIT 2: Found it. Disabling.

---

### Post by Brendan_Doyle on 2014-01-25
[ATTACH=CONFIG]249732[/ATTACH]Okay I am making some awesome progress. I now have an entire SSD of almost 30GB of unallocated space. The caching has been disabled, lets try this out.

---

### Post by Brendan_Doyle on 2014-01-25
Yaaaaaaaayyyyyyyyuuuuuhhhhhhhhh!!! Success!

[attach=config]249733[/attach]

---

### Post by Brendan_Doyle on 2014-01-25
Sticky for anyone who has IntelSRT? Because it's a pain, lol.

---

### Post by fantab on 2014-01-25
Phew.... 
Congrats.

Where did Ubuntu install on SSD or HDD?

---

### Post by Brendan_Doyle on 2014-01-25
> **fantab said:**
> Phew.... 
Congrats.

Where did Ubuntu install on SSD or HDD?

Don't know yet, backing up photos I want to keep from windows to photobucket. It will be awesome if it installs to the SSD though. Onto the next thing, I am quite fond of my Lightroom and photoshop. I am wondering is WINE a good route to go so that I can use those programs still?

---

### Post by fantab on 2014-01-25
Check by running the following commands:
```
sudo parted -l
sudo fdisk -l
```

Since you are dual-booting I'd suggest you keep away from WINE as much as possible and use Windows for such tasks.

Do share how did you disabled intelSRT, someone could find it useful.

---

### Post by Brendan_Doyle on 2014-01-25
If you have a computer with IntelSRT, you should have a program called Intel Rapid Storage Technology, you go there, then go to the accelerate tab and disable as needed. 

Here are some screens, I recached the drive so I could show you guys the process, it's fairly simple. After you do this though go to disk management on windows and make sure you set the disk up. It will bring up a window asking you as soon as you go to disk management.

---

