---
title: "Installer doesn't see drive"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by ex_isp on 2012-05-11
Attempting to put 12.04 on dual boot for a customer.  When booted to live cd, can see the hdd, mount it, read it.  Shows up as sda2.

When I try to run the install, the drop down at the bottom shows sda but no partition options.  If I try to run the install, it says "no root partition defined".

Has Win7 64 bit installed with an ASUS P5G41T-M LX PLUS m/b, 4 GB ram and a WD Caviar 320 Sata hdd.

Thoughts?

This is driving me nuts!

---

### Post by Enigmapond on 2012-05-11
Probably because you selected to do your own partitions. Does this computer have Ubuntu on it already? If so just let it overwrite the existing one...if not just let it auto partition for the new OS. If you do it manually you need to tell it what partition to write to and where to but the boot.

---

### Post by ex_isp on 2012-05-11
this hdd has never had linux of any shape on it.  is brand new machine we just built.  12.04 will not auto partition it or let me manually partition it.

Only software on it is the default win7 load

---

### Post by darkod on 2012-05-11
If the disk has been used in raid before, it still has meta data remains. Windows ignores this but ubuntu doesn't and it will not show it as destination for installing.

If you are NOT running raid on it, you can check this from live mode with:
sudo dmraid -E -r /dev/sda

If asked whether you want to remove raid data, confirm.

Another situation when partitions are not shown is an error in the partition table. But I think the above will solve it for you.

---

### Post by ex_isp on 2012-05-11
> **darkod said:**
> If the disk has been used in raid before, it still has meta data remains. Windows ignores this but ubuntu doesn't and it will not show it as destination for installing.

If you are NOT running raid on it, you can check this from live mode with:
sudo dmraid -E -r /dev/sda

If asked whether you want to remove raid data, confirm.

Another situation when partitions are not shown is an error in the partition table. But I think the above will solve it for you.

This is a new hdd as is the rest of the build, but I will try this and see if I get anymore info.
Thanks darkod!

Will post back with results in 10 or 15 mins... (have customers here) ;-)

---

### Post by darkod on 2012-05-11
OK, let us know and we'll take it from there. Corruption in the partition table sometimes can also be ignored by windows but not by ubuntu.

---

### Post by ex_isp on 2012-05-11
Ran sudo dmraid -E -r /dev/sda and told it to remove any/all old meta data.  rebooted and went into bios just to make sure this wasn't an ahci issue.

Same result.  Boot back to 12.04 cd (the same one I've loaded all my home systems with) and I can see and explore the hdd from live.  Install says no root partition but the add/change/modify partition options are locked and inaccessible.

Still stuck

---

### Post by darkod on 2012-05-11
OK. Boot into live mode, open terminal and post the output of:
sudo fdisk -l (small L)
sudo parted /dev/sda print

The no root partition error is logical, you are not specifying any partition as root. But you can't specify since it doesn't let you manipulate them. Lets see why.

---

### Post by ex_isp on 2012-05-11
I'm now at home.  Just phoned work and sent this to my partner to try.  Should have results in 5-10 mins

OK. Boot into live mode, open terminal and post the output of:
sudo fdisk -l (small L)
sudo parted /dev/sda print
  

He will paste results and I'll re-post

---

### Post by ex_isp on 2012-05-11
From:     Juan Donosa <juandonosa@yahoo.com>
Reply-to:     Juan Donosa <juandonosa@yahoo.com>
To:     Chris <ex_isp@cox.net>
Subject:     Re: linux try
Date:     Fri, 11 May 2012 16:13:23 -0700 (PDT)


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7faca53a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      196607       97280    7  HPFS/NTFS/exFAT
/dev/sda2          196608   625141759   312472576    7  HPFS/NTFS/exFAT


ubuntu@ubuntu:~$ sudo parted /dev/sda print

Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  101MB  99.6MB  primary  ntfs         boot
 2      101MB   320GB  320GB   primary  ntfs

ubuntu@ubuntu:~$

---

### Post by ex_isp on 2012-05-11
Additional info.

Have also tested Mint9 (LTS) on this box with same result.

No surprise there eh?  ;)

---

### Post by darkod on 2012-05-11
I can't see anything wrong man. I thought you might have overlapping partitions or something, but they are fine.

Could it be one of those rare cases where it doesn't have a driver for the controller? But you said you can read it from live mode...

Desperate attempt: What if you try the alternate install cd? It has a text installer as opposed to graphical, but otherwise you end up with the same desktop system.

---

### Post by ex_isp on 2012-05-11
> **darkod said:**
> 

Desperate attempt: What if you try the alternate install cd? It has a text installer as opposed to graphical, but otherwise you end up with the same desktop system.

Not familiar with "alternate install cd".  different iso?

---

### Post by ex_isp on 2012-05-11
BTW, some beautiful photos you took  ;-)  I'm guessing their yours...  crystal waters on the peninsula...

---

### Post by darkod on 2012-05-11
> **ex_isp said:**
> Not familiar with "alternate install cd".  different iso?

Yeap, different ISO. You have all of them here, choose carefully between desktop/alternate/server and 32bit/64bit:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

PS. Photos? You lost me... :)

---

### Post by ex_isp on 2012-05-11
> **darkod said:**
> 

PS. Photos? You lost me... :)

Profile says Spain which piqued my curiosity... found this

[http://www.panoramio.com/user/1383062](http://www.panoramio.com/user/1383062)

made assumption

---

### Post by ex_isp on 2012-05-11
And let me add my friend, I appreciate the efforts here...  it's a strange one

Like you said, controller?, but can see in live.  Bizarre.

---

### Post by darkod on 2012-05-11
> **ex_isp said:**
> Profile says Spain which piqued my curiosity... found this

[http://www.panoramio.com/user/1383062](http://www.panoramio.com/user/1383062)

made assumption

Nope, that seems like Croatia. And the name Darko is common in ex-Yugoslavia territory. I guess his surname starts with D too. :)

PS. "My" sea is better, just don't tell him, they are touchy about their sea. :)

---

### Post by ex_isp on 2012-05-11
> **darkod said:**
> Nope, that seems like Croatia. And the name Darko is common in ex-Yugoslavia territory. I guess his surname starts with D too. :)

PS. "My" sea is better, just don't tell him, they are touchy about their sea. :)

LOL  Alright, won't mention a thing...keep it under wraps!

---

### Post by darkod on 2012-05-11
> **ex_isp said:**
> LOL  Alright, won't mention a thing...keep it under wraps!

I hope it's not breaking forum rules... See attachment. :)

---

### Post by drs305 on 2012-05-11
In some cases a corruption on the Windows partition causes recognition problems in Ubuntu. You might try running chkdsk from a Windows repair disk until it reports no more errors to see if solves things.

Since you can read the contents after mounting it may not be the problem, but if you are being driven nuts and have a repair disk around, it may be worth a try.

---

### Post by ex_isp on 2012-05-11
> **darkod said:**
> I hope it's not breaking forum rules... See attachment. :)

Nice!  We don't have that in Arizona!

---

### Post by ex_isp on 2012-05-11
> **drs305 said:**
> In some cases a corruption on the Windows partition causes recognition problems in Ubuntu. You might try running chkdsk from a Windows repair disk until it reports no more errors to see if solves things.

Since you can read the contents after mounting it may not be the problem, but if you are being driven nuts and have a repair disk around, it may be worth a try.


Thanks for chiming in on this drs.  This pain in the neck load on new machine, new hardware has been going for three days now at work.

All hardware is new, though that doesn't mean that something isn't faulty.  Did actually do spinrite test on the drive yesterday and chkdsk this morn.  No problems indicated or reported.

---

### Post by ex_isp on 2012-05-12
BTT    Any others have thoughts or suggestions on this thread?

Thanks in advance to all!

Ex

---

### Post by darkod on 2012-05-12
You can try opening the disk with fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It can locate and repair smaller errors in the partition table.

Even if it doesn't find anything wrong, if it lists the partitions correctly, you can try writing the table with 'w'. In theory it should simply write the same table. But if there is some issue with the current table, simply overwriting it might change something. I know it's desperate, but all else looks good.

On the desperate note, you can try to connect it to another sata port, double check that sata mode is NOT set to RAID by any chance...

PS. Did you try with the alternate image?

---

### Post by ex_isp on 2012-05-12
Some good thoughts there darko.  Won't be back on it till Monday.  Have emailed myself this info to test.

Many thanks!

---

### Post by cryptotheslow on 2012-05-12
Quite a strange one.

How about booting into windows and using its disk management to shrink the 2nd partition sufficiently, then boot into the LiveCD "try it" environment and use GParted to create the required ext4 and swap partitions in the now empty space, finally move onto the installer and use the "something else" option to define which partition to put / and swap on. (Presuming that the installer sees the new partitions at this point).

---

### Post by ex_isp on 2012-05-12
> **cryptotheslow said:**
> Quite a strange one.

How about booting into windows and using its disk management to shrink the 2nd partition sufficiently, then boot into the LiveCD "try it" environment and use GParted to create the required ext4 and swap partitions in the now empty space, finally move onto the installer and use the "something else" option to define which partition to put / and swap on. (Presuming that the installer sees the new partitions at this point).

Had actually (though not documented here) installed an early sata 80 GB drive as a second physical disk.  Used Gparted from the live boot to format the 80 GB to ext4.   Installer still did not see a usable partition on which to put /.

I'm 55 and 3/4 bald.  lol  Don't have many hairs left to pull out  :P  Just know this ones killin' me.

---

### Post by ex_isp on 2012-05-14
Ok.  This seems to be a problem with the installer seeing NTFS structures on some systems.  Did 12.04 on my Dads desktop tonight and had the same problem as with the previous system.  "no root file-system found". 

Difference here, on the second attempt, I said use the whole disk.  (had xp, sp3 on previously.)
When using the whole disk, it installed no prob and am using it right now.

Tried two installs with dual boot (xp/12.04) with same result.  No root file system.  Just did "use entire drive" and it went in flawlessly.

hmmm

gurus?

thoughts?

---

### Post by darkod on 2012-05-14
The message said found or defined?

The no root filesystem defined is standard when using manual install but not specifying which partition to be used as root. Don't forget that when installing manually it doesn't assume anything for you. You have to tell which partition to use for what.

If you CAN NOT see any partitions, it is clear you can't specify which one to be root.

But if you are just looking at this wrong, and the disk displays free unallocated space for example, you need to create the partitions first.

Another explanation might be an error in the partition table. Erase and use all disk deletes the partition table (so the error is gone with that) and it creates a new empty one creating root and swap partition on it during the install.

The same "fix" might work if you create new table yourself, you can do this in Gparted in Device - Create Partition Table. Note that this DELETES all partitions and data on the disk, so first copy everything you need. Also, if you want windows on the same disk you would have to reinstall. That's why it hasn't been mentioned before, it's not actually a fix, it's starting from scratch.

---

### Post by ex_isp on 2012-05-16
Little late getting back to you darko...

Actually did flatten the hdd, removing all partitions and traces of MBR.
Used Gparted from live...and could see the new partition.  Still would not 
install to it.  The installer sees sda, but all options are grayed out.

I'm beginning to wonder if this is the first of UEFI I've seen and that is
the problem...?

This UEFI thing may turn ugly.

Never did get it going, Put the customer on a slightly older Core2 board instead and am currently looking for what boards we may be using in the future for Linux servers and workstations.

Any comments there, if this is indeed a UEFI issue?

---

### Post by darkod on 2012-05-16
Actually there is nothing pointing to UEFI.

1. Windows can use UEFI only with gpt table on the hdd. Your hdd has msdos table. Windows wouldn't work with uefi + msdos.

2. When using uefi boot, the first partition on the hdd always has to be a small (approx 300MB) FAT32 partition of type EFI System partition. That's where boot files go.

You don't have neither of that on your system. Hardly UEFI.

But yes, in general, UEFI right now does have issues if you want to make a dual boot working. If there is an option to disable UEFI boot in BIOS, I would prefer that option. At least right now.

---

### Post by Guilden_NL on 2012-11-30
> **darkod said:**
> If the disk has been used in raid before, it still has meta data remains. Windows ignores this but ubuntu doesn't and it will not show it as destination for installing.

If you are NOT running raid on it, you can check this from live mode with:
sudo dmraid -E -r /dev/sda

If asked whether you want to remove raid data, confirm.

Another situation when partitions are not shown is an error in the partition table. But I think the above will solve it for you.

Here's a "gran dosis" of good Karma for you!

I've dealt with RAID for years on both Windows and Linux and have been 100% Linux for eight years.  I just bought a new Asus ZenBook UX51 which comes with two 256GB SSD in RAID 0 configuration with Win 8.  (RAID 0?!?)  So I broke the RAID in BIOS and loaded a clean install of Win 8 Pro so I can stay current with Windoze, even though I do everything in Linux (well, there's the missing Linux version of Visio that hurts. Every shot at matching it has fallen well short)

I was staring at why everything I ran could see the second SSD, fdisk -l, GParted, etc, but the loader refused to see it.

Wonderful advice my friend! I really appreciate it.  I will attribute this to you over in a large ZenBook owners' forum.  I will be the first to figure out how to dual boot Win 8 with Linux on these. Everyone else went Linux only with RAID 0.  Actually you are the one who helped me figure it out!

Gracias!

---

### Post by Bachi on 2012-12-12
Guilden, which forum do you mean? It would be really great if you could share your experiences so far and post a how-to on installing Ubuntu along Windows 8 on the Asus UX51. I have a test device from Asus here another 3 days, but will return it if I cannot get Ubuntu / Win8 to run in a dual boot configuration. 

Thanks - Martin

---

