---
title: "Installing 14.04 onto flash drive"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by walt11 on 2014-04-17
I've created the 14.04 installer DVD, and would like to use it to install the release onto a flash drive. If that works, would also like to install it onto an external hard drive. In both cases, I DON'T want to create a dual boot with the Windows 8.1 on my internal drive.

If I can install them, plan to boot them from the PC boot menu. I don't want to modify my internal drive, don't want GRUB on it.

MY PC is a Lenovo 64 bit laptop with UEFI, but hope I've surmounted the UEFI problem by changing to Legacy mode on the BIOS Menu.

Thanks.

---

### Post by oldfred on 2014-04-18
You have to have grub as that is the boot loader.
But you can choose to boot from UEFI menu or one time boot key (f12 on my system).
The os-prober will find the internal drive and add boot entries but only if flash drive is in same boot mode will those entries work. You can turn off os-prober.

You can configure flash drive to boot in either UEFI or BIOS boot mode or both.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

You do have to use Something Else or manual install, so you get the combo box on the bottom of the partition, mount & format screen on where to install grub2's boot loader. You want to be sure to change from default of sda to whatever flash drive is, sdb or sdc etc.

How large is flash drive? 
My 16GB has a 8GB / (root) and 8GB for data with no swap. But I do not use it a lot, it is more for emergency boot.

---

### Post by walt11 on 2014-04-18
Thank you for that quick response. Your responses have always been that way, and I greatly appreciate it.
There is much that I don't understand, and I will have to work through it, and the links you provided, and get back to you with more questions, over a period of several days.

One of the things which gives me pause immediately, is why I would have to have GRUB on my internal drive, even though I will not have Ubuntu on it. Is it because when I use the boot menu to boot the flash drive, it is actually GRUB which is providing that boot menu? I can understand why it would have to be on the flash drive, but I am very uneasy about making my Windows system inaccessible because of the boot problems I always get into with GRUB if it is on the internal drive.

In any case, (many) more questions to come.

---

### Post by oldfred on 2014-04-18
You do not need the grub boot loader on your internal drive. And you do not want that.

But you do have to have grub as it is boot loader, but have to install the boot loader to the MBR of the flash drive or external drive. Only Something Else or manual install gives an option on where to install a boot loader.

Then you keep the Windows boot loader on the internal drive, and set BIOS/UEFI to boot external first. Then if external not found, it will default to internal. You may have to set that boot order in BIOS.

If Windows is UEFI, I do suggest you make flash drive UEFI or any external drive UEFI. But use gpt partitioning whether you want BIOS or UEFI boot as Ubuntu can boot from either way from the new gpt partitioning.

With UEFI the issue is less than it was with BIOS/MBR. In BIOS/MBR system only boots from MBR of drive. Each system overwrites MBR with its boot loader.  Only if you have more than one drive can you have multiple/different boot loaders in each MBR.

But with UEFI each system installs its boot loaders in the efi partition. So a new install does not overwrite an old install just adds another boot folder. So a system with UEFI is somewhat like a boot configuration with multiple MBRs even if only one drive.

---

### Post by walt11 on 2014-04-18
Thanks! I didn't know I could make the external drive or flash drive UEFI. I didn't even know about gpt partitioning. Will look into those, and be back.

---

### Post by oldfred on 2014-04-18
Link in post #2 has detailed instructions on flash drive with gpt. It is also either BIOS or UEFI, but you do not have to make it both.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by TechAndNews on 2014-04-18
> **walt11 said:**
>  Would like to install onto a flash drive. Would also like to install onto an external hard drive. In both cases, I DON'T want to create a dual boot with the Windows 8.1 on my internal drive.

It sounds like you want to run Ubuntu/Linux off external media, possibly with persistence.

Please refer to these informative articles:

Live USB
[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

installation from USB Stick
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

LiveCD/Persistence
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Live CD
[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

Make a Live CD/DVD or Bootable USB
[https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)

There are also several Linux Distros whose main benefit is being small and lightweight enough to permanently boot off external media such as USB Flash Drives and so forth.

Lightweight Linux Distribution
[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)

List of Linux Distros that run from RAM
[http://en.wikipedia.org/wiki/List_of_Linux_distributions_that_run_from_RAM](http://en.wikipedia.org/wiki/List_of_Linux_distributions_that_run_from_RAM)

Good Luck, and Enjoy Linux. :)

---

### Post by walt11 on 2014-04-18
Thanks to both of you for all that helpful information. I would not have found that on my own - even after spending lots of time trying.

---

### Post by walt11 on 2014-04-23
> **oldfred said:**
> 
You can configure flash drive to boot in either UEFI or BIOS boot mode or both.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)


I was able to use the instructions at the link you provided to install a bootable 14.04 system on my USB 3 flash drive. Thanks so much for your help. I would now like to do the same thing on my external USB 3 hard drive. How must I modify the instructions at H. for creating the partitions to include the large (1TB) data partition for the external? And then, which partition will have the boot flag?

---

### Post by oldfred on 2014-04-23
Grub does not use boot flag. 

With UEFI and gparted it uses the boot flag to indicate the efi partition (and only one per drive). But that is just a gparted convention as with gpt drives the efi partition is defined by a really long GUID which is not so easy to add, so gparted uses boot flag.
With gdisk it uses 4 char codes to define GUIDs. For and efi partition it is ef00 and for a bios_grub it is ef02.

You install to an external hard drive the same way, just partition sizes can be a lot larger. I suggest 20 or 25GB for / (root) and separate /home or data partition(s). If you may use drive with a Windows system, you may want a NTFS data partition so you can use it with Windows. Windows does not see Linux partitions.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by walt11 on 2014-04-23
Thank you for yet another incredibly fast response!

Yes, I do plan to use this drive on Windows, frequently, so I will need the large NTFS data partition, but I'm confused about where it should be. Doesn't it have to be first for Windows to see it? But how does that change the other partitions? Here are the instructions I followed for the flash drive (except I used larger sizes for the ext4 and swap partitions):
[INDENT]H. Create partitions
1a. Make a 1 MiB partition without file system (unformatted)
1b. Add the flag bios_grub.
2a. Make a 250 MiB partition with FAT32 file system and the label EFI
2b. Add the boot flag
3. Make a 6838 MiB partition with ext4 file system and the label pendrive (the size and label can be modified to fit the pendrive).
4. Make a 348 MiB swap partition (linux-swap) (the size can be modified to fit the pendrive).
[/INDENT]

Should I have the NTFS data partition first, followed by the others just as shown? Or do I need to make changes to these others because of the NTFS partition?

Sorry to be so dense, but I'm in information overload.

---

### Post by oldfred on 2014-04-23
I think Windows only sees a NTFS or FAT32 partition on a flash drive if it is the first partition.
But on external hard drives it should see NTFS partitions anywhere on drive.

Because you have a hard drive with lots more space, I would follow the sizes I posted above as starting points. But it depends a lot on if you want space for lots of data, or if thinking of testing other installs and want another 20 to 25GB / partition or two.

---

### Post by walt11 on 2014-04-23
Does it matter where the partition labelled EFI with the boot flag is? OK if it comes after the large NTFS partition?

---

### Post by oldfred on 2014-04-23
UEFI recommends it be first. Windows seems to make it second or third but the partitions before the efi are usually smaller recovery type partitions.

I did see one user who had it further into the drive, and it worked for him. I thought maybe the FAT32 driver with UEFI may have be able to read larger drives.

You do have to make sure drive is gpt partitioned. So if you already have a large NTFS partition did you partition drive with gpt?

---

### Post by walt11 on 2014-04-24
In the procedure I used yesterday, it starts out by creating a new gpt partition table, so that will be OK.

I was going to try it all earlier this evening, but I'm hung up on trying to take a Windows backup first. The backup program tells me [FONT=Tahoma][SIZE=2]**[COLOR=#ff0000]Cluster Run Error. Unused  cluster found in cluster run - Error code = 10. Please run 'chkdsk  /f'[/COLOR]**[/SIZE][/FONT] in the partition SYSTEM_DRV, which I read is the EFI partition having to do with booting - so it probably happened yesterday. It's booting fine, but I can't take a full backup untill that's fixed.

Unfortunately, I'm unable to run chkdsk on that partition - it doesn't accept the name, and doesn't have a drive letter. There's probably a simple way to do that, but I'm embarrassed to admit that I'm unable to find out how. Any suggestions?

---

### Post by oldfred on 2014-04-24
Somewhere I did see instructions. But you have to assign a drive letter to the partition as it does not normally have one. I forget exact command but it may just be assign, but do not know exact parameters required.

With FAT32 you can try the Linux tools. Windows tools probably are better.
See this:
       man fsck.vfat

Or something like this:

 You might need dosfstools and ntfsprogs as well.
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sdb1

   Must be unmounted
sudo dosfsck -a /dev/sdb1

---

### Post by walt11 on 2014-05-04
Gparted does not let me create an unformatted partition (for the bios_grub flag) but changes it to fat16. How can you make it unformatted?

---

### Post by oldfred on 2014-05-05
In gparted I see unformatted as the very last entry or at bottom of list.
Not sure if already formatted, if you have to delete and recreate?

---

### Post by walt11 on 2014-05-05
> **oldfred said:**
> In gparted I see unformatted as the very last entry or at bottom of list.

I did select the unformatted entry, but gparted changes my selection to fat16.

---

### Post by oldfred on 2014-05-05
I have never had an issue with gparted. Are you clicking the check in top panel to actually run change?

I might then try Disks or command line with gdisk.

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
gdisk is in repository.
sudo apt-get install gdisk

       In GPT fdisk (gdisk), give bios_grub a type code of EF02.

---

### Post by C.S.Cameron on 2014-05-05
shrinking the size of the partition before/after where you want the space should leave unformatted space, try gparted..

---

### Post by walt11 on 2014-05-07
> **oldfred said:**
> I have never had an issue with gparted. Are you clicking the check in top panel to actually run change?

Got around the gparted issue, and installed 14.04 on my external drive, but have major problems!
It placed an entry in my boot menu (replacing the one for the flash drive). But when I try to boot from it, I get grub prompt:

grub>

Since entry for flash drive was replaced, can't boot from it either.

---

### Post by oldfred on 2014-05-07
Did you install to the same flash drive as your installer? 

We normally use two flash drives, a smaller one as the installer and the target then is a larger drive.
Sometimes at grub menu we have to adjust a setting to get it to work as drive order changes without installer flash drive.

---

### Post by walt11 on 2014-05-07
> **oldfred said:**
> Did you install to the same flash drive as your installer? 

My installer is the DVD created from the downloaded iso file. I used it to successfully install 14.04 onto a flash drive. The installation process created a new entry in my PC boot menu, and when I booted from  that entry, the flash drive booted OK.

I did essentially the same thing to install 14.04 onto an external hard drive. Used the DVD again as the installer. Installation process created a new entry in my PC boot menu, and removed the entry for the flash drive. When I tried to boot from this new entry, instead of booting the external hard drive as I expected, I just got the grub prompt.

---

### Post by oldfred on 2014-05-07
Need to see details. 

From your DVD you can install Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Note there is not a trusty PPA, yet.

      
 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by walt11 on 2014-05-07
> **oldfred said:**
> Need to see details. 

From your DVD you can install Boot-Repair.

I'm afraid to use boot repair for fear it will modify my internal hard drive!

Here are details. My external hard drive is /dev/sdc. Partition table is gpt.

sdc1 1 MiB unformatted  with bios_grub flag
sdc2 250 MiB FAT32, label EFI, boot flag
sdc3 large NTFS partition for data storage in Windows
sdc4 32GB ext4 mount point / with the ubuntu install
sdc5 linux swap

Here's where I may have gone wrong. In the part of the installation which asks for "Device for boot loader installation" I gave it sdc2, not the root sdc. I did that because that's how I got the flash drive install to boot.

---

### Post by oldfred on 2014-05-07
Yes, you should say sdc whether BIOS or UEFI. If in BIOS mode you just installed grub to the PBR or partition boot sector of sdc2. Then whatever old boot loader was in sdc or none is trying to boot.

If UEFI you should be able to also say sdc, and it should know to install to efi partition, but there was a post where to get it to work they did have to specify the efi partition on a second drive as it wanted to default to an internal drive's efi partition.

---

### Post by walt11 on 2014-05-07
> **oldfred said:**
> Yes, you should say sdc whether BIOS or UEFI. If in BIOS mode you just installed grub to the PBR or partition boot sector of sdc2. Then whatever old boot loader was in sdc or none is trying to boot.

If UEFI you should be able to also say sdc, and it should know to install to efi partition, but there was a post where to get it to work they did have to specify the efi partition on a second drive as it wanted to default to an internal drive's efi partition.

I'm using UEFI. Haven't tried BIOS mode, and don't know if I will.

Now, for UEFI, do I have to re-install using sdc, or can I do something to fix it? And I'm somewhat worried about your second paragraph. I don't want it to default to my internal drive. (The installer program doesn't recognize my operating system - and I use "something else", as you directed.)

When I installed the flash drive, I did use sdc, and it didn't boot, so I re-installed the flash drive using sdc2, and it did boot! That's why I did that for the external hard drive.

---

### Post by oldfred on 2014-05-07
Post link to BootInfo report. Be sure to boot in UEFI mode from installer or run from your install on flash drive.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I think you litterally can copy the folders in the efi partition to another efi partition and they will work. Perhaps changing the grub in the efi partition. There can be some timing on updating UEFI as it also has NVRAM and remembers settings and may have to be updated or several reboots to refresh.

---

### Post by walt11 on 2014-05-07
Sounds rather complex for me. I think it will be just easier for me to re-install on the external hard drive, correctly (hopefully) this time.

When I did the previous install to my external hard drive, it removed my PC boot menu entry for the flash drive & replaced it with the external hard drive. I would like to have boot menu entries for both of them. Is there a way to do that?

---

### Post by oldfred on 2014-05-07
You still can edit 40_custom to add as many systems as you want to boot.
I have many test, mostly old now installs. So I turn off os-prober and copy into 40_custom only the entries I want to keep.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by walt11 on 2014-05-10
> **oldfred said:**
> Yes, you should say sdc whether BIOS or UEFI.

I started over, (re)installed onto my external hard drive, and this time specified the root, sdc, as "Device for boot loader installation". But, it still doesn't work. Still only get a grub prompt when I try to boot. I'm sure using Boot-Repair, as you suggested, would take care of it, but I'm afraid to use it for fear of ending up with a grub boot menu every time I boot normally into Windows. So I have given up on the external drive, and re-partitioned it to it's original size for data storage.

I still have the flash drive which, you recall, was working properly, booting into Ubuntu - until the installer DVD over-wrote the entry for it in my PC boot menu, so now I can't boot that either.

I may try to find out how to modify my computer's boot menu, so I will leave this thread open for a while. Thank you again for all your help which, as always, has been outstanding and much appreciated.

---

### Post by oldfred on 2014-05-11
With multiple drives and Boot-Repair you should not use the auto fix. It does just install grub to every hard drive.

But in Advance mode, you can choose system whether Windows or any Ubuntu install on any drive and then choose drive to install boot loader into. I do always suggest to keep boot loader on the same drive as install, but sometimes you may want it somewhere else. 
With Windows it does have to be the same drive as the Boot partition if BIOS based which may not always be the same drive as the main install or c: drive.

---

### Post by walt11 on 2014-05-11
Thanks for the warning about the auto fix. I was uneasy about using that anyway, but didn't realize it installed grub to every hard drive! I may go back and try Advance mode with the flash drive, and will let you know if I do.

---

