---
title: "New hard drive partitioning"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by stas7 on 2015-12-29
Hello,
I just installed a new 1TB HDD and going to use it for Ubuntu (for developing using C++ and Eclipse) and for storing/sharing data with Win7 (which is my primary OS and installed on small SSD). I may need to install say Win8/10 on the HDD in future.
I partitioned HDD using gparted, however win7 refused to format any partition created with gparted so I had to recreate them in win7 with "computer management".

Could you have a look at my partitioning if its reasonable in any sense? 
Would like to make sure that I didn't do it in a stupid way. currently the HDD is almost empty and I could repartition it if necessary. After I move lots of data to it, this would be much harder.
Also not sure if the size of swap partition for Ubuntu is good (I have 16GB of RAM and going to use hibernation in Ubuntu).
Ubuntu boot loader is installed on HDD and Win7 boot loader is installed on SSD.
I also copied Lenovo recovery partitions using Norton Ghost from original HDD. sda7 and sda8 are Windows partitions for storing data/photos etc and I am going to share them with Ubuntu (from what I found linux has no issues with accessing/modifying NTFS partitions). Or is it better to use FAT32 for this purpose?

I am pretty new to Ubuntu, any advise is helpful.
Thanks!
The gparted screenshot is getting compressed, don't know how to avoid it (its in .png and original looks much better).

---

### Post by grahammechanical on 2015-12-29
You are using MBR partitioning with that hard disk. Which is fine for  Windows 7 but I do not think that Windows 8/10 will be happy installed  on hard disk with MBR partitioning. I think that Windows 8/10 need a  GUID partition table (GPT). I may be wrong.

A second point. If  you install Windows 8/10 after Ubuntu has been installed you will most  certainly lose the Ubuntu boot loader (Grub). And some have found that  updating Windows 10 can loose the Ubuntu installation completely. There  are several posts on this forum dealing with problems caused by  installing windows 10 & updating it. Some have been dual booting Windows  7 & Ubuntu on an MBR partitioned disk and then they upgraded to  Windows 8 & on to Windows 10 and it was Good-by Ubuntu.

So, I  would think about using GPT on that disk. No need then to worry about a  4 primary partition limit and extended and logical partitions. I would  also suggest installing Windows 8/10 before installing Ubuntu. And I  would most definitely have a separate partition for /home. Then when you  need to re-install Ubuntu you will not lose the data and user  configuration files in the /home folder.

25 - 30 GB for Ubuntu ( / )
as much as you like for /home
swap = more than the amount of RAM if using hibernation
Use the something Else option to install

Oh, one more thing. It just may be that you have Windows 7 on a motherboard that has a UEFI boot system. If that is the case then you need to read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The motherboard may have a BIOS boot system but if it is a early UEFI motherboard then Windows 7 would be installed in BIOS/Legacy/compatibility mode.

Regards.

---

### Post by yancek on 2015-12-29
I think you should be able to install windows 10 MBR but that is something you should investigate and the microsoft site or a windows forum would be a better place to do it.
If I understand correctly, you have never had windows on the drive you are showing and the windows partitions are ones you created and moved files to (Lenovo Recovery).  sda1 is marked as "boot" partition.  How did that get there?  In any case, you need a primary partition on which to install the windows boot files or it will fail.  You could install the system on a logical partition but the boot files MUST be on a primary partition for windows to boot.  If you are not experienced in installing different versions of windows, I think you will have  problems with this setup.  You could shrink one of the logical partitions and create another primary for windows.  Personally, I think you would be better off installing windows first and putting your multiple windows installs on the same drive.

---

### Post by oldfred on 2015-12-29
I also suggest gpt partitioning whether system is BIOS or UEFI. As then you can use drive on newer UEFI system without major repartitioning/reformatting.

But Windows only boots in UEFI mode from gpt, so if system is BIOS only, you may want to keep the MBR, if putting Windows on it. I prefer Windows on one drive and Ubuntu on another if you have multiple drive. But with an SSD often better to have both on SSD.

I started converting to gpt with all new or totally reformatted drives soon after I used gpt with 10.10. 

I wanted newer UEFI system for several years and thought I might move drives to new system, so I included both an ESP - efi system partition & bios_grub partition at beginning of drive so I could boot either way and not have to try to add the ESP later when drive was full of data.
But I had added SSD in 2011 to old system and it worked so well, I did not get new UEFI system until last year and by then drives are old enough I did not want them on very new system.

---

### Post by stas7 on 2015-12-29
Thanks for your replies! yes I never had Windows on this HDD. sda1 partition I copied from original HDD cause I think it's needed by recovery partition (it's a Lenovo notebook) which I would like to keep.
I don't know whether it has BIOS or UEFI. it's ThinkPad T430s.
Right now I don't need to install any OS besides Ubuntu on HDD, just want to have an opportunity to install another OS in future - who knows whatever reason may arise. its a notebook and I cannot just add another drive, so I would like to keep it as flexible as possible.
I haven't heard about GPT - will Google. if it's more flexible then MBR then that's very interesting.
is there any other issue with GPT besides that Windows doesn't boot with BIOS?
can I use gparted from ubuntu 15 livecd to do GPT?
let me know if I haven't clarified smth.

The mSATA SSD is 120gb which barely enough to keep win7 with software, so there is no way I could fit ubuntu there.

---

### Post by oldfred on 2015-12-29
While it is possible to convert from MBR(msdos) to gpt(GUID), normally you do it when drive is new or totally erased or backed up. Best not to convert unless easy and have no or little data to restore.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table

[/URL]Windows 7 can be installed in UEFI boot mode, but default from DVD is BIOS with MBR(msdos). Newer versions offer both UEFI & BIOS by default and how you boot install media is then how it installs. But forcing an UEFI/gpt install on a MBR drive will erase it.

---

### Post by stas7 on 2015-12-29
I can delete all partitions from HDD and partition in GPT from scratch, no need to convert. But I don't wan't to touch SSD drive.
Is it possible to have MBR on one drive and GPT on second drive(HDD)?
I found on inet that with legacy BIOS one cannot boot any OS from GPT partitioned drive (it was windows related forum, so no sure what they meant). This might be an issue. can one boot ubuntu from GPT drive with BIOS?

---

### Post by oldfred on 2015-12-30
My part 2006 part 2009 system that was BIOS only had XP on sda & Ubuntu on sdb. When I totally converted it to 64 bit and reinstalled Ubuntu on sdb, I converted to gpt. I did have to turn on AHCI mode when I updated to a new SSD in 2011 and XP does not boot with AHCI on in BIOS. So I finally turned off Windows. :)

Or you can boot Ubuntu in UEFI or BIOS mode from gpt on one drive and Windows in UEFI with gpt or BIOS with MBR on anther drive.

But grub will only boot systems installed in same boot mode as grub/Ubuntu is installed. You have to boot from UEFI or one time boot key often f10 or f12 if not in same boot mode.

I started adding both an ESP - efi system partition for UEFI boot for future use as well as the bios_grub partition for BIOS boot on all new gpt partitioned drives. And with new UEFI system I still have a bios_grub partition but have not used it. It is only 1MB so not any space on drive.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]15-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by stas7 on 2015-12-30
I walked through BIOS menus and it seems that it supports UEFI (at least there's word UEFI in several places). There are options like 'boot UEFI only' and 'boot legacy OS only' and 'boot both'.
So I will do GPT on HDD and choose boot device during startup.
About swap: in windows I had issue that OS cannot commit all RAM to applications if swap is turned off, so I often had 'out of memory' errors with 16gb ram. after turning on swap I haven't seen such error. is it the same in linux?
I've read ubuntu swap faq, for 16gb ram and hibernation it recommends from 16 to 32gb swap which is too ambiguous.

also is gParted from ubuntu 15 livecd a good tool for beforehand partitioning in GPT?

---

### Post by oldfred on 2015-12-30
I have only used gparted to create partitions, but gdisk is a good command line tool. I do use gdisk to review & configure changes sometimes.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. You must do this first.

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I only suggest 2GB for swap. But then you cannot hibernate. But I also do not suggest hibernation if dual booting. When still using XP I used a shared NTFS data partition and then neither system can be hibernated or you may lose data.
If you want hibernation (which in some versions also has issues), you need enough space for all of RAM just incase all of RAM is full. But drive mfg & system count memory differently. Or you need 16GiB not GB. Quick estimate is about 10% more.
 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

---

### Post by stas7 on 2015-12-30
> **oldfred said:**
> I have only used gparted to create partitions, but gdisk is a good command line tool. I do use gdisk to review & configure changes sometimes.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. You must do this first.

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I only suggest 2GB for swap. But then you cannot hibernate. But I also do not suggest hibernation if dual booting. When still using XP I used a shared NTFS data partition and then neither system can be hibernated or you may lose data.
If you want hibernation (which in some versions also has issues), you need enough space for all of RAM just incase all of RAM is full. But drive mfg & system count memory differently. Or you need 16GiB not GB. Quick estimate is about 10% more.
 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

In which units does gParted counts space? say when I enter 1MB partition in gParted, its size is counted on base 10 or base 2?

---

### Post by oldfred on 2015-12-30
I have never paid attention. 

Gdisk shows me this, so I think I selected 500 for ESP & 2 for bios_grub, but I selected 25 for / system partitions.

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  efi
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  trusty
   4       246163456       250068991   1.9 GiB     8200  
   5       236079104       246163455   4.8 GiB     8300  iso_ssd
   6        52230144       103429362   24.4 GiB    8300  xenial

```

---

### Post by stas7 on 2015-12-30
Thanks again for your help. I created GPT table from scratch and now creating partitions in gparted. 
I am making shared NTFS partition which I will mount somewhere in /home and store most of data there. Do I still need separate partition for /home? If yes, what's the smallest size can it be? I don't know what it is used for.

---

### Post by oldfred on 2015-12-30
The /home is where all your data is stored. Both your user configurations and default locations of any data you save. Each user has a /home so their own data & settings may be different.

I keep /home inside /. It uses about 2GB of my / partition, but most of that is .wine as I use Picasa which runs in .wine. Configurations are tiny or usually less than 500MB. But I create data partition and link all my data folders back into /home, so default saves look and  act the same, but are really in the data partition.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by stas7 on 2015-12-31
Here is new partition table with GPT (interface was different in gParted from what you described, so hope I've chosen the right option).
Please aprove so that I could start using the new drive:) I tried to follow all recommendations:)
Ubuntu is not yet installed. Lenovo recovery is copied with gParted from original Lenovo HDD.
[ATTACH=CONFIG]266469[/ATTACH]

---

### Post by oldfred on 2015-12-31
@mj3mari
Moved to your own thread. Better to not hijack another thread as your partitioning questions are different then OP.

@stas7
Partitioning is very personal depending on what you want to do with system. My own optimal partition scheme is almost always not what I want several years later, but I do not trust main working hard drive(s) for more than a few years anyway and start fresh on new drive. So whatever you do within reason is fine.

If only making /home 15GB, I might just include it in / (root). Either make root larger or immediately set up links so your data is in your NTFS partition.

My defaults (system mounts removed):
```
fred@trusy-ar:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        24G   13G  9.8G  58% /
/dev/sda1       500M   13M  487M   3% /boot/efi
/dev/sdb4       385G   96G  270G  27% /mnt/data
/dev/sdb5        28G  3.7G   23G  14% /mnt/backup
```

---

### Post by stas7 on 2015-12-31
> **oldfred said:**
> @stas7
Partitioning is very personal depending on what you want to do with system. My own optimal partition scheme is almost always not what I want several years later, but I do not trust main working hard drive(s) for more than a few years anyway and start fresh on new drive. So whatever you do within reason is fine.


sure, it can never be perfect for everybody. just wanted to make sure I didn't do smth silly and irreversible again like using MBR in the beginning. So I assume there is nothing terribly wrong with this partitioning and start copying data to HDD (I will think about joing /home and root).
GPT seems to be much more flexible than MBR and can be adjusted more easily. Thanks a lot!
Happy coming New Year everybody!

---

