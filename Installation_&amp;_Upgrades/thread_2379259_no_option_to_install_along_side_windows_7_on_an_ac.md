---
title: "no option to install along side windows 7 on an acer"
date: 2017-12-03
forum: Installation &amp; Upgrades
---

### Post by missmoondog on 2017-12-03
was trying to install lubuntu 16.04 on my brothers acer aspire 5253-bz846 with amd radeon hd6250 graphics, amd dual core c-50 processor yesterday but had no option to install it along side windows 7. haven't ever seen that happen before. it ran perfectly fine without installing it and ran much better than windows 7.

i haven't messed with resizing or partitioning in ages and didn't really want to risk losing his stuff. i did try it some what though but windows reported it had errors and to do a chkdsk, which i did both the quick check where it only checks 3 stages and the full check where it checks all 5 stages. it didn't find any errors though! i did a chkdsk using the live dvd also and it found nothing too.

don't really know what else i can say or do about this, but after seeing how well it ran using the live disc, it would've been really sweet to have been able to install lubuntu. 

as a side question, what ever happened to that wubi tool that let you install linux using that?

any help would really be appreciated although i have to give him his laptop back today.

thank you

---

### Post by RobGoss on 2017-12-03
You can always use the Windows management partition tool to create a partition to install Ubuntu on then, just boot in to the live desktop and when you choose to install Ubuntu choose that partition. I do recommend making a complete backup of any important data just in case something goes wrong

---

### Post by ubfan1 on 2017-12-03
Probably Windows took all four primary partitions, and the installer cannot create any more.  You will need to shrink a Windows partition, then backup/copy all the files on one partition so itmay be deleted and an extended partition created, then you can create logical partitions in the extended partition for Ubuntu (and maybe the original contents of the primary as a logical).  Assume the worst, and have verified backups.  You have a one day time limit, but don't rush things.  Maybe get the repartitioning done first, then attempt the install when you have more time.

---

### Post by ajgreeny on 2017-12-03
Maybe your brother's machine has already used the four partitions that are possible if using BIOS and not the newer UEFI firmware system.

From the live Ubuntu system run terminal command ```
sudo parted -l
``` and show us the output back here.

Wubi is no longer supported and was never meant as a dual boot possibility but more as a test of your hardware with Ubuntu, so you can forget about using that now; it has gone.

---

### Post by missmoondog on 2017-12-03
> **RobGoss said:**
> You can always use the Windows management partition tool to create a partition to install Ubuntu on then, just boot in to the live desktop and when you choose to install Ubuntu choose that partition. I do recommend making a complete backup of any important data just in case something goes wrong

Windows partitioning tool wouldn't work. Told me disc had errors. Did 2 disc checks, the quick one and long one. Neither reported erros!

> **ubfan1 said:**
> Probably Windows took all four primary partitions, and the installer cannot create any more.  You will need to shrink a Windows partition, then backup/copy all the files on one partition so itmay be deleted and an extended partition created, then you can create logical partitions in the extended partition for Ubuntu (and maybe the original contents of the primary as a logical).  Assume the worst, and have verified backups.  You have a one day time limit, but don't rush things.  Maybe get the repartitioning done first, then attempt the install when you have more time.

Did notice disc had 3 partitions and 4th partition said free space equaled the entire size of disc! Couldn't shrink windows partition as every time I tried shrinking/formatting, said disc had errors.

> **ajgreeny said:**
> Maybe your brother's machine has already used the four partitions that are possible if using BIOS and not the newer UEFI firmware system.

From the live Ubuntu system run terminal command ```
sudo parted -l
``` and show us the output back here.

Wubi is no longer supported and was never meant as a dual boot possibility but more as a test of your hardware with Ubuntu, so you can forget about using that now; it has gone.

i believe machine is WAY to old to have UEFI firmware. I believe it is 6+ years old. I was looking for that in bios though and didn't see any such thing.

I believe the issue is Windows is using 3 partitions, if i was looking at that right! I gave him back his laptop already, but am planning to go over there tomorrow. Will try that command then and post back. 

Going to try and talk him into letting me wipe out windows and install lubuntu!! :)

I'm going to go out on a limb and say laptop should work correctly with it installed seeing as how well it ran from the live disc. Don't you people think so?

Thanks for replies folks!! :)

edit:
sucks that wubi isn't around. i used that several times while in the process of getting used to linux and never had any issues with it. :(

---

### Post by kansasnoob on 2017-12-03
I highly recommend dual-booting. We just need to see the output of 'parted -l' to know what we're dealing with. If only 3 partitions exist and it's using an msdos partition table then you'll likely need to see how much disc space is being used in Win 7. It's always safest to shrink Windows using its own partitioning tool and it may be necessary to cleanup, defrag, and make a few tweaks within Windows to accomplish the resize.

---

### Post by ubfan1 on 2017-12-03
Posting the output ajgreeny asked for might clear up the partitioning questions -- it sounds like there may be some partition overlap if one is equal to the entire disk size.  Dual boot is nice in case there's that one thing that you still need Windows for (like taxes!).  If you've got the disk space, let your bro get used to lubuntu and decide after not using Windows for months, he'd rather have the disk space devoted to lubuntu.  It's getting harder to just reinstall W7 -- Microsoft might not be "activating" new copies anymore, so you might need a backup of the disk image.  If the install media runs on a machine, the install should work, and may work better if some proprietary drivers are available.

---

### Post by kansasnoob on 2017-12-04
> **ubfan1 said:**
> Posting the output ajgreeny asked for might clear up the partitioning questions -- it sounds like there may be some partition overlap if one is equal to the entire disk size.  Dual boot is nice in case there's that one thing that you still need Windows for (like taxes!).  If you've got the disk space, let your bro get used to lubuntu and decide after not using Windows for months, he'd rather have the disk space devoted to lubuntu.  It's getting harder to just reinstall W7 -- Microsoft might not be "activating" new copies anymore, so you might need a backup of the disk image.  If the install media runs on a machine, the install should work, and may work better if some proprietary drivers are available.

Good point. I have actually purchased Win 7 product keys very recently off Ebay but why buy what you don't need? Every Windows user should have their keys printed out somewhere safe. This does a good job of finding them:

[http://www.rjlsoftware.com/software/utility/winproductkey/](http://www.rjlsoftware.com/software/utility/winproductkey/)

Windows 7 torrents are available here:

[http://mirror.corenoc.de/digitalrivercontent.net/](http://mirror.corenoc.de/digitalrivercontent.net/)

I've used them and they're clean, but no telling how long they'll be there.

---

### Post by gordintoronto on 2017-12-04
WUBI has been dropped.

When you boot a Live CD, can you check the health of the hard drive? I'm not sure what tools Lubuntu provides for this, in Xubuntu I use GSmartControl.

---

### Post by mastablasta on 2017-12-07
> **missmoondog said:**
> Windows partitioning tool wouldn't work. Told me disc had errors. Did 2 disc checks, the quick one and long one. Neither reported erros!

Did notice disc had 3 partitions and 4th partition said free space equaled the entire size of disc! Couldn't shrink windows partition as every time I tried shrinking/formatting, said disc had errors.


how did you check the disk. windows disk check actualyl checks the file system. to check the drive itself you need to use diagnostic software made by manufacturer or you can also use the various freeware and opesource software - for example the one found on Ultimate Boot CD (UBCD)

a good tool for changing primary into secondary partition, move partitions etc. is mini tool partition wizzard.

needless to say do a disk clone before any work with partitions (i suggest Clonezilla or Redo Backup)

---

### Post by missmoondog on 2017-12-10
> **mastablasta said:**
> how did you check the disk. windows disk check actualyl checks the file system. to check the drive itself you need to use diagnostic software made by manufacturer or you can also use the various freeware and opesource software - for example the one found on Ultimate Boot CD (UBCD)

a good tool for changing primary into secondary partition, move partitions etc. is mini tool partition wizzard.

needless to say do a disk clone before any work with partitions (i suggest Clonezilla or Redo Backup)

yes, i used the windows chkdsk tools as that is what it said to do because it said disc had errors. the live lubuntu installer also said to check disc once and it did that on it's own. i've never had any luck with that ultimate boot cd thing.

when things calm down after the holidays, i'll pursue the issue of just installing lubunto on the whole disc, after making a backup of windows, and see how that goes. so stay tuned to this topic!! :)

thanks for the replies

---

### Post by mastablasta on 2017-12-11
to check the disk you need to use diagnostic software made by manufacturer. usually they are available for free on manufacturers website.

live lubuntu installer is likely checking the install disk (USB or DVD) for errors. that is if you are referring to "**check disk for defects**" option. it doesn't check the hard drive, i believe.

checkdisk searches for windows file system errors and corrects them. it can not correct the mechanical errors on the drive. it also can not check the linux file systems. FSCK does that for ext4 for example.

---

### Post by gordintoronto on 2017-12-11
"live lubuntu installer is likely checking the install disk (USB or DVD) for errors. that is if you are referring to "check disk for defects" option. it doesn't check the hard drive, i believe."

Different distros come with different disk checking programs. Even with the Live CD, you can temporarily install others. For example, GSmartControl lets you point at any drive in the system, and get the diagnostic info. No need to go to the manufacturer site.

---

