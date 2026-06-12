---
title: "Dual Boot Re-Installation - Partitioning Guide/Help Request"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by jim89 on 2013-06-24
Hi all,

**Background**: 
I started a dual boot Windows 7/Ubuntu system at the start of this year.  Along the way I screwed up the Windows installation (yay me) and so was using  just Ubuntu for a couple of months. However, I now want to go back in to Windows  for some gaming I can't make work in Ubuntu so I'm about to trash the  entire hard drive and remake my set up. 

I have no data in Ubuntu (beyond one save game than I can accept losing) that I will want to recover, and **I want the install to be as clean as possible.**

My **system specs** are:
Intel i5 3750K
8GB Crucial Ballistix RAM
ATi 7970 GPU
Asus P8Z77-V (**UEFI**)
OCZ Vertex II 120GB SSD (Primary device)
Samsung Spinpoint 2TB HDD (Storage device)

**Question(s)**: 
Leaving the 2TB aside, what preparatory steps do I need to take on the SSD to get it ready for the installation? 

I was going to use GParted on an Ubuntu 12.04 LiveDisk to wipe the disk and then (re)make an 8GB swap space and ~20GB ext4 partition for Linux and give the rest of the disk over to NTFS for Windows. I'll then install Windows, get it all working and then install Ubuntu 12.04 along side of it; is there anything else that I need to cover? 

Will my MBR need wiping/re-jigging as well as I've had a dual boot before, or is it safe to leave that alone? What about the small portion of "System Reserved" space at the front of my disk - is this the MBR, should I wipe/leave it alone etc?

What partitions do I need to create/should I create?

Beyond the steps above, is there anything else I need to consider before going ahead and doing the re-fresh of my system? If anyone has an up-to-date, step-by-step guide for this sort of thing I'd very much appreciate that (did a search before this and found a couple but they're slightly older so I'm hesitant to follow them).



Thanks very much for any responses you can offer. Hopefully I can get back to a functioning gaming set up in Windows and a nice small and tidy 12.04 installation next to it for day-to-day browsing, TV, music etc. Look forward to hearing from you,

Jim.

---

### Post by Mark Phelps on 2013-06-24
IF you want to avoid the situation of having two partitions for Win7, then go ahead and create an NTFS partition with GParted but -- and this is Important -- when you boot into the Win7 installation media, be sure to REFORMAT that same partition.  Win7 works best on  partitions it formatted itself.

---

### Post by jim89 on 2013-06-24
Ok, will do. Thanks for the tip. Does the rest of what I've put look sensible?

I.e. should I wipe the entire drive, including the "System reserved" 100mb partition, before re-installing windows?

---

### Post by oldfred on 2013-06-24
The 100MB boot/recovery partition was added with Windows 7 where Vista did not have it. The main reason was to have a boot partition, so you could encrypt the main install as the boot files cannot be encrypted. But it also has the recovery or repair console which you may be able to get into to make repairs to main install. Generally better to have a repairCD or Flash drive to repair Windows anyway, so you can install Windows 7 to one NTFS partition.

Since hardware is UEFI capable, you have to make sure you boot install media for both Windows and Ubuntu in BIOS mode if you want BIOS installs. If you want UEFI installs you have to boot install media in UEFI mode. But do not mix as then it is difficult to dual boot (have to change UEFI to BIOS each time) .

---

### Post by jim89 on 2013-06-24
> **oldfred said:**
> The 100MB boot/recovery partition was added with Windows 7 where Vista did not have it. The main reason was to have a boot partition, so you could encrypt the main install as the boot files cannot be encrypted. But it also has the recovery or repair console which you may be able to get into to make repairs to main install. Generally better to have a repairCD or Flash drive to repair Windows anyway, so you can install Windows 7 to one NTFS partition.


So should I leave the current partition in place, or delete and merge it with the NTFS partition for Windows 7 and let Windows recreate the 100MB boot/recovery partition? The latter seems like it might be "cleaner" but I don't want to screw anything up. Thoughts?

> **oldfred said:**
> 
Since hardware is UEFI capable, you have to make sure you boot install media for both Windows and Ubuntu in BIOS mode if you want BIOS installs. If you want UEFI installs you have to boot install media in UEFI mode. But do not mix as then it is difficult to dual boot (have to change UEFI to BIOS each time) .
[/QUOTE]

So I had a bit of a google about UEFI vs. BIOS mode and found a few articles, including this one**: **[**superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi**]("http://ubuntuforums.org/superuser.com/questions/496026/what-is-the-difference-in-boot-with-bios-and-boot-with-uefi")

It's interesting, but I could use a bit of advice on which to go for, UEFI or BIOS, seems there are pros and cons on both sides! 

All comments and thoughts are most welcome. Thanks.

---

### Post by oldfred on 2013-06-24
I do not have UEFI, but hoped to soon, so started helping those installing with UEFI. Pre-installed Windows 8 with secure boot have complicated the UEFI install process greatly. If you do not have (nor really need) secure boot UEFI is a lot easier to install.

But BIOS is well known as it has been around for only 30 years. UEFI is new enough that both UEFI and systems either Windows or Ubuntu have some issues or bugs.
If you ever plan on a new drive over 2TB it has to be gpt partitioned. Then from gpt partitioned drives you can only boot Windows in UEFI mode. But Ubuntu will boot from a gpt partitioned drive with BIOS or UEFI. I use gpt with BIOS on my system, but cannot then install any version of Windows on my gpt drives (a good thing). I still have my old XP install on a MBR drive that dual booted with my gpt Ubuntu until I installed a SSD and had to change to AHCI and XP does not work with AHCI easily.

I think I am saying the same things as your link. It is more if you want the shiny new UEFI with perhaps some issues or the old reliable but soon to be retired BIOS system.

---

### Post by jim89 on 2013-06-24
> **oldfred said:**
> I do not have UEFI, but hoped to soon, so started helping those installing with UEFI. Pre-installed Windows 8 with secure boot have complicated the UEFI install process greatly. If you do not have (nor really need) secure boot UEFI is a lot easier to install.

But BIOS is well known as it has been around for only 30 years. UEFI is new enough that both UEFI and systems either Windows or Ubuntu have some issues or bugs.
If you ever plan on a new drive over 2TB it has to be gpt partitioned. Then from gpt partitioned drives you can only boot Windows in UEFI mode. But Ubuntu will boot from a gpt partitioned drive with BIOS or UEFI. I use gpt with BIOS on my system, but cannot then install any version of Windows on my gpt drives (a good thing). I still have my old XP install on a MBR drive that dual booted with my gpt Ubuntu until I installed a SSD and had to change to AHCI and XP does not work with AHCI easily.

I think I am saying the same things as your link. It is more if you want the shiny new UEFI with perhaps some issues or the old reliable but soon to be retired BIOS system.

Will try with UEFI for now. I think I can force the disk drive to boot in UEFI mode - I guess that means any installation will be in UEFI mode, too, right? 

Any thoughts on partitioning?

---

### Post by oldfred on 2013-06-24
I think to boot Windows in UEFI mode, you have to use a flash drive.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

Ubuntu will then boot from either UEFI or BIOS and then install in that mode. 
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

See link below.
Several links to Windows 7 and other systems without secure boot. But most of the info is on Windows 8 & secure boot which you should not have to worry about.

---

### Post by jim89 on 2013-06-25
Well seeing as how I don't have a USB drive around to force Windows 7 in to UEFI mode, I guess I'll stick with BIOS for now. 

Thanks for partitioning info, v. helpful. One more (hopefully final) question from me: when I am formatting my SSD to clean it out prior to installation, should I format and delete the 100MB system reserved space that Windows created for itself originally and allow Windows to recreate it?

Thanks,

J.

---

### Post by oldfred on 2013-06-25
Never installed Windows 7, so I do not know if it makes a difference. I might delete it just so it has an empty drive to start with.

---

### Post by jim89 on 2013-06-25
Cheers oldfred. After a bit of googling just now (been a looong day at work!) it seems it's fine: [http://www.sevenforums.com/installation-setup/106068-100mb-system-reserved-windows-7-a.html](http://www.sevenforums.com/installation-setup/106068-100mb-system-reserved-windows-7-a.html)

---

