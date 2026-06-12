---
title: "Windows 7 Dual-boot Gone After Ubuntu Install"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by james_wilson3 on 2016-03-25
Hello everyone.

I have two drives, an SSD and an HDD. In my SSD are two OSes, Windows 7 and Ubuntu 15.10; in my HDD is one OS, Windows 8. 

My problem is that, when I boot up Ubuntu, I'm given only the boot options for Ubuntu and Windows 8; however, Windows 7 is where all my important things are, and from doing some research, I suspect that when I factory-reset Ubuntu, I somehow destroyed the UEFI for Windows 7. I still have the files on the drive thankfully, it just doesn't give the boot option for Windows 7.

I factory-reset Ubuntu by plugging in the USB install and booting through the USB, coming to the option in which I could upgrade to Ubuntu 15.10 from 14.xx, erase Ubuntu and reinstall it (which is what I chose), and erase the whole drive and install Ubuntu.

Using gparted, for my SSD, with my (self-proclaimed) awesome ASCII skills, the partitions look like this:

[unalloc. 101MB][/dev/sda1 ntfs, boot flag][/dev/sda2 linux-swap][/dev/sda3 extended][/dev/sda6 ext4, mountpoint /][/dev/sda5 ext4][unalloc. 2.55 GB]

/dev/sda1 contains my Windows 7 installation, and under "Flags" it says boot, although as I've stated before, I don't get the option to boot from it. I suspect the initial unallocated memory to be where my Windows UEFI was (also based on how the partitions in my HDD with Windows 8 appears, where /dev/sdb2 is type fat32, mount point /boot/efi, with flags boot, esp), and therefore I can't select it to boot anymore.

I don't have the Windows 7 install CD with me anymore, and I was hoping someone could help me with enabling Windows 7 once again. I don't prefer to try a paid option (such as EasyRE), and I have tried BootRepair, although it doesn't seem to have worked either. Any advice would greatly be appreciated, this is a bit frustrating for me.

EDIT: Inside the mounted Windows 7 disc which I can access on Ubuntu, I do have bootmgr in the home directory, as well as the boot folder with bootmgr and memtext of file type .exe.mui inside the en-US folder.

---

### Post by oldfred on 2016-03-25
But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you have BIOS/MBR, you have to be booting Windows in BIOS mode. 
Windows only boots from MBR with BIOS.
Windows only boots from gpt partitioned drives with UEFI.

And Windows only boots with BIOS from the drive set as default in BIOS boot, and the primary NTFS partition with the boot flag.
So you probably boot all Windows installs from sda1. But with Windows 7 that normally is just a small 100MB boot partition and main install is on next NTFS partition. Your description is not showing that partition? Report will show more detail.

---

### Post by james_wilson3 on 2016-03-25
Here's that report you requested.

[http://paste.ubuntu.com/15502501/](http://paste.ubuntu.com/15502501/)

---

### Post by oldfred on 2016-03-25
You sda drive is BIOS/MBR with Windows boot files in it. That is only for BIOS/CSM/Legacy boot.
Your sdb drive is UEFI/gpt with Windows for UEFI boot.
You have to go into UEFI to choose which way to boot each system. And some UEFI may have to turn on/off UEFI or CSM settings to match system you want to boot.

Grub only boots systems installed in same boot mode, either UEFI or BIOS. UEFI and BIOS are not really compatible once you start to boot you cannot change, but can boot from UEFI boot menu or one time boot key like f10 or f12, check manual.

You also have Ubuntu booting in UEFI mode from ESP on sdb2, but it is on sda which is MBR partitioned.
The gpt partitioning is the standard for UEFI boot and your configuration is a bit mixed.

I do not think you could have booted the Windows in sda1 with UEFI. You may have used UEFI boot menu, but booted in BIOS mode.

Check boot options with one time boot key first.

---

### Post by james_wilson3 on 2016-03-25
My current boot options when using one time boot key are my SSD, my HDD, ubuntu, and the USB I installed ubuntu with.

---

### Post by oldfred on 2016-03-25
With UEFI, you often have multiple entries even for one drive.
You may have both a BIOS boot and a UEFI boot.
And with UEFI you can in effect have an unlimited number of folders/systems in ESP - efi system partition.

And flash drive installer from Ubuntu is configured for both UEFI & BIOS, if secure boot is off. If Secure boot is on, then only UEFI Secure boot is offered.

---

### Post by james_wilson3 on 2016-03-25
I think I have secure boot off; at least, that's what the BIOS menu on booting tells me.

Also, don't know if this helps in terms of clarity, but also in my BIOS, there's "Windows 8 Features" with "Other OS" (selected) and "Windows 8" as options, and a tabbed subtitle that says "Boot Mode Selection", with "UEFI and Legacy" (selected), "Legacy Only", and "UEFI Only" as options. In terms of motherboard, the company is Gigabyte.

I already had Ubuntu installed, and it gave me the boot option for Windows 7 before, not my Windows 8 on my HDD. But after the factory reset, the Windows 7 option disappeared, and the Windows 8 is the one available.

---

### Post by LostFarmer on 2016-03-25
Can not say for sure but would guess:  your old linux install was on sda5 in MBR mode, when you updated to  Ubuntu 15.10 , you booted the install USB in EFI mode so it installed in EFI mode to sda6

When linux was booting in MBR mode it would see Win7 and not Win8, likewise when linux was installed in EFI mode it would see Win8 and not Win7 to boot.

What is on sda5 ?  You selected to format it during the Ubuntu 15.10 install or latter ? 

What would like work is replace the hdd (win7) mbr boot code currently non-working grub, with a MSWindows compatible code and use the one time boot key.

---

### Post by james_wilson3 on 2016-03-26
I didn't really format any partition during the Ubuntu 15.10 install (I initially formatted partitions when installing my previous 14.xx version); I just selected the option to "erase Ubuntu", my previous 14.xx version, and reinstall from the new 15.10 install in my USB. Still not super familiar with Ubuntu, so if you can elaborate a bit more on what you mean by replacing the mbr boot code (my Win7 install is on the SDD with Ubuntu) grub with a Windows compatible code, that would help. Most I'm familiar with currently with the term "grub" is that I can bring up its command prompt on Ubuntu boot, and when I try to boot from anything other than "ubuntu" (aka my HDD or SDD), I get the "grub rescue" command prompt.

If reinstalling Ubuntu not in EFI mode is possible so that I can boot to Windows 7, that would probably be more reasonable. Otherwise, any help is appreciated.

---

### Post by oldfred on 2016-03-26
Again with both UEFI & BIOS you can only boot systems installed in same boot mode as you boot Ubuntu/grub.
Your Ubuntu is now booting in UEFI mode, so it can only also offer to boot the Windows 8 install which is also UEFI.

You show a Windows MBR boot loader in MBR of sdb. If you in UEFI boot menu, choose to boot in Legacy mode the sdb drive that should boot the Windows install on sdb.

```
 BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0004,0003
Boot0000* ubuntu	HD(2,GPT,340fa8a5-daec-4a5d-86f2-f028613cd268,0x96800,0x31800)/File(EFIubuntushimx64.efi)
Boot0003* Hard Drive 	BBS(HD,,0x0)AMGOAMNO........o.S.a.m.s.u.n.g. .S.S.D. .8.5.0. .E.V.O. .2.5.0.G.B....................A...........................>..Gd-.;.A..MQ..L.2.S.N.1.S.N.G.A.8.5.1.2.8.7. .B. . . . ......AMBOAMNO........o.T.O.S.H.I.B.A. .D.T.0.1.A.C.A.2.0.0....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . .Z. .1.3.6.V.Y.J.S.K......AMBOAMNO........q.S.a.n.D.i.s.k....................A.............................>..Gd-.;.A..MQ..L.4.C.5.3.1.0.0.1.4.1.1.2.3.0.1.0.4.1.2.3......AMBO
Boot0004* UEFI: SanDisk	HD(1,MBR,0x0,0x20,0x1dcffe0)/File(EFIBOOTBOOTX64.EFI)AMBO 


```

Your entry 0003 may be the BIOS boot of SSD.

With UEFI hardware, better to always be consistent. 
Or only use UEFI with gpt partitioning on all drives.
Or only use BIOS with MBR partitioning on Windows drive(s). You can still use gpt with Ubuntu if not a Windows boot drive.

---

### Post by james_wilson3 on 2016-03-26
When I select my SSD in the UEFI menu and I save and reboot, I get the "boot/grub/i386-pc/normal.mod not found" error and am thrust into a grub rescue prompt.

Just to make sure I am selecting it right, it says something like P1 (or P3, forget which number): Samsung SSD ...

---

### Post by oldfred on 2016-03-26
If you want to boot a BIOS version of Windows from sdb, you must have the BIOS version of Windows boot loader in MBR.
Best to use your Windows repair disk. MBR for all BIOS versions of Windows is the same, so fixMBR will work from just about any version.

You can also use Boot-Repair's advanced options to install a Windows type boot loader. Be sure to boot in BIOS mode for that. Choose install and drive correctly. Boot-Repair can only do minor fixes to Windows so always best to have working Windows repair flash drive.

---

### Post by james_wilson3 on 2016-03-26
Sorry, I'm just a little confused with what you said. I'm trying to boot Windows 7 on sda, but you're saying I should boot it from sdb, is what I'm understanding.

When you say Windows repair disk, that's the OS installation disk I imagine if I haven't created one already. That's fine, I'll just have to find that somewhere. You say fixMBR works from any version, so do you mean that I could create a system recovery drive in Windows 8 and use that to fix my Windows 7 install? Once I create the drive, how do I go about using it to fix W7?

---

### Post by oldfred on 2016-03-26
Sorry mixed that up. 
BIOS drive is sda, so you want the Windows boot loader in the MBR of sda.
And sdb is the UEFI system.

Always best to have all systems in BIOS mode or all systems in UEFI mode to avoid confusion.

Best to ask on Windows forum for Windows issues. But I have some links:

 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html) 

      
 Repair Windows UEFI ows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

---

### Post by LostFarmer on 2016-03-26
There are many ways to do things.  In your case the pastebin say that  sdb has Win7/8 boot code in the MBR, so you can use 'dd' to copy the boot  code to sda.  
> Windows 7/8/2012 is installed in the MBR of /dev/sdb. 
First you need to verify when you boot into the live linux that sda is in fact the 234G Win7 hdd and not the 1.8t Win8  hdd , to do so in a terminal run
```
sudo fdisk /dev/sda -l
``` (note -l is a small L)     Changing the comps firmware boot device could change which hdd is listed as sda/sdb.
To write the mbr boot code on sdb to sda:
```
sudo dd if=/dev/sdb of=/dev/sda bs=1 count=435

``` The above command will write the mbr code from sdb to sda.  the 'if' = input file/device and 'of' = output file/device, be sure they point to correct hdd shown by fdisk command.

That should be all you need to do, your Win7 (sda1) does have the needed boot flag already set.

If you do not understand, do not do.

The 'dd' command can be very useful and very destructive, if one does not have the command written correctly.

---

### Post by james_wilson3 on 2016-03-26
Hmm, so you're saying that you saw that sdb has Win7 boot code in the MBR (master boot record holding the boot sector that can boot Win7 again), is that right? Is this because as oldfred said in post #4 that my "configuration is mixed"? To my understanding, what he said is that /dev/sda contains BIOS/MBR, which means the boot record in sda is good for BIOS/CSM/Legacy booting (a.k.a. what I need for Win7), whereas sdb has UEFI/gpt (the newest standard: GUID partition table), which means sdb is good for UEFI booting (a.k.a. what I need for Ubuntu/Win8/Win10).

Below is the terminal print-out to your recommendation for sudo fdisk:
```

/dev/sda1          206848 390831847 390625000 186.3G  7 HPFS/NTFS/exFAT
/dev/sda2       390832128 423057407  32225280  15.4G 82 Linux swap / Solaris
/dev/sda3       423059454 483053567  59994114  28.6G  5 Extended
/dev/sda4            2048      4095      2048     1M  7 HPFS/NTFS/exFAT
/dev/sda5       453058560 483053567  29995008  14.3G 83 Linux
/dev/sda6       423059456 453058559  29999104  14.3G 83 Linux

```

I'm not going to try the 'dd' command yet since I don't fully understand it yet. I think if you could clarify it a bit more, that would be good. To my understanding from this Wikipedia article (yes, I know the integrity of Wikipedia may not be prime, but I'm still an undergrad in computer science, go figure (on the side, any place I should go to that's great for reading documentation and the like with regards to Linux? I feel I know where to go with questions (here/Stack Overflow))), [https://en.wikipedia.org/wiki/Dd_(Unix)#Master_boot_record_backup_and_restore](https://en.wikipedia.org/wiki/Dd_(Unix)#Master_boot_record_backup_and_restore), you're trying to have me repair the MBR through 'dd'. 

A few questions: the "bs" flag is the block size count (the size of the memory block being read), and the "count" flag is how many blocks are read? And second: by me carrying out this command, what happens to my Ubuntu install because it's in sda? Because it requires UEFI to boot, would it nullify it? It doesn't make sense for me that it'd still be compatible since UEFI is the newer implementation. 

Also, just want to say thanks to you guys for helping me out; Ubuntu/Linux, I've learned to be so efficient for code-writing among other things, but it's a bit worrisome when trying things on the internet (I was successful in disabling sound permanently while trying to enable alsa-mixer [long story], hence my upgrade to Ubuntu 15.10 from 14.xx, and now this).

---

### Post by oldfred on 2016-03-27
UEFI and BIOS are not compatible.
So having one drive as BIOS and other drive as UEFI is more like two totally different computers.
But you can read data from one to the other, it is just the way they boot.

With gpt partitioning you can also boot in BIOS mode. The gpt has a protective MBR which normally just has one partition table entry saying entire drive is gpt. That is so old MBR partitioning tools see that disk is used and do not automatically try to partition it. But space for BIOS boot code is also in that protective MBR.

I prefer not to use dd unless absolutely no other way. DD's nickname is Data Destroyer for a reason. Any typo, reverse from/to or even an extra space can totally damage a system so it cannot be repaired.
But putting grub or Windows boot loaders into MBR for BIOS boot is relatively easy. And Boot-Repair makes it easy, but with your configuration you only use Advance mode, not any auto fix options.
And if a Windows user you should know how to restore a Windows boot loader from a Windows repair flash drive.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL] Windows 7 can be installed in UEFI boot mode. It just is that DVD is only configured for BIOS and has to be copied to a flash drive and the efi boot files have to be moved to correct place.

---

### Post by james_wilson3 on 2016-03-28
I see. Thanks for the warning. Okay, so in other words, Windows repair flash drive. I'll go for that, and then immediately upgrade to 10 so I don't have to worry about BIOS booting anymore. Thanks for the help, guys.

---

### Post by oldfred on 2016-03-28
Updating to Windows 10 will not change how you boot. Windows 10 is both BIOS & UEFI.
But either way you do have to make sure Windows fast start up or always on hibernation is off.

You have to backup erase drive, repartition with gpt and reinstall if you want UEFI.
Windows only boots from MBR with BIOS.
Windows only boots from gpt partitioning with UEFI.

---

### Post by james_wilson3 on 2016-03-28
Okay, so I thought that since Win10 is both, I could UEFI boot since sda is already UEFI. But you're saying I need to basically backup my sda (a.k.a move the files to my HDD), erase it and repartition it, and then reinstall Win10 where it was at because gpt needs to basically format it? I'm guessing because the partition is currently MBR and I need to delete it and make a UEFI partition. So how do I do that? I'm guessing

```

sudo gdisk  /dev/sda

```

Currently it says only MBR is present, not GPT. So in other words, recreate the partition, then carry out the above command. But I don't know what option/command I should use for "converting MBR to GPT format in memory" after, as it says when I run the command currently.

---

### Post by oldfred on 2016-03-28
I have always used gparted.
        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB or data partition(s):
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4 
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

---

### Post by psfal on 2016-03-30
Just a drive-by thanks for the insight in this post. I was looking for a solution to this very issue. After reading this post I disabled Secure-boot and both OS work...

---

