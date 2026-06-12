---
title: "Problems booting Windows 8 after installing Ubuntu"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by Sayre_Precure on 2015-03-24
I'm going to try and get all of this information in one post, so bear with me, it's a lot.  I'm rather new to Ubuntu, so to be entirely honest, I don't know what half the stuff below even means >.< 

I upgraded to Windows 8 the other day, and then proceeded to install Ubuntu.  Didn't have any issues, was able to boot up Ubuntu.  After goofing around on Ubuntu for a while, I tried to go boot from Windows, but wasn't able to find it.  

Tried    the following:

```
sudo fdisk -l

  Disk /dev/sda: 256.1 GB, 256060514304 bytes  

 256 heads, 63 sectors/track, 31009 cylinders, total 500118192 sectors  
 Units = sectors of 1 * 512 = 512 bytes  

 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x527cd163  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1  4294967295  2147483647+  ee  GPT  
 

 Disk /dev/sdb: 750.2 GB, 750156374016 bytes  
 255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 4096 bytes  
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes  
 Disk identifier: 0xbbc58b91  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1            2048   732547071   366272512    7  HPFS/NTFS/exFAT  

 /dev/sdb2       732547072  1094028369   180740649    7  HPFS/NTFS/exFAT  
 /dev/sdb3      1094029310  1465147391   185559041    5  Extended  
 Partition 3 does not start on physical sector boundary.  
 /dev/sdb5      1094029312  1431676927   168823808   83  Linux  

 /dev/sdb6      1431678976  1465147391    16734208   82  Linux swap / Solaris

```

```
sudo os-prober

  /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi  


```

   ```
sudo update-grub

 Generating grub configuration file ...  
 Found linux image: /boot/vmlinuz-3.16.0-33-generic  

 Found initrd image: /boot/initrd.img-3.16.0-33-generic  
 Found linux image: /boot/vmlinuz-3.16.0-30-generic  
 Found initrd image: /boot/initrd.img-3.16.0-30-generic  
 Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi  
 done  


``` 

I also tried using my Windows 8 Installation Disk to repair Windows, but it doesn't show up on my boot options.  I went into the BIOS and checked my DVD drive, and it shows that it's enabled.

Here is what I see and what occurs during boot:

Ubuntu 
     -boots up Ubuntu, no problems
Advanced options for Ubuntu  
     -Linux 3.16.0-33-generic
     -Linux 3.16.0-33-generic (recovery mode)
     -Linux 3.16.0-30-generic
     -Linux 3.16.0-30-generic (recovery mode)
Windows UEFI bootmgfw.efi
     -resarts my computer and returns me back to boot
Windows Boot EUFI loader 
     -goes to a screen that says "Preparing Automatic Repair" but as far as I can tell, never does anything else
EFI/ubuntu/MokManager.efi
     -Continue boot
     -Enroll key from disk
     -Enroll hash from disk
Windows Boot Manager (on /dev/sda1)
     -restarts my computer and returns me back to boot

I'm at a loss. Any and all help would be appreciated.

---

### Post by oldfred on 2015-03-24
Your sda drive has gpt signatures and your sdb drive is MBR(msdos).

How is/was Windows installed UEFI or BIOS?
Windows only boots from gpt with UEFI and from MBR with BIOS. But if installing Ubuntu in wrong mode you converted drive from one partition to another Windows will never work.

Fdisk does not work on gpt partitioned drives.

May be best to see full details of your installs. Run Summary report and post link it gives. 
With two drives do not run Auto fix. That just installs grub everywhere and it cannot fix partition issues. We need to see all partitions and boot configuration:

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Sayre_Precure on 2015-03-25
I believe it was installed BIOS.  I'd read that UEFI was a potential source of error when trying to dual boot.  I checked it when I first installed Windows 8 and from what I found, UEFI was disabled. 

I ran boot repair earlier, but to no avail.  Here's the summary: 

[http://paste.ubuntu.com/10675094/](http://paste.ubuntu.com/10675094/)

Thanks for your help.

---

### Post by oldfred on 2015-03-25
Your install of Windows is in UEFI mode on a gpt partitioned drive.

But your sdb 750GB drive is MBR(msdos) partitioned, with Ubuntu install in the MBR drive, but the grub boot loader in the efi partition on sda.
I used to think that was impossible, not sure if Boot-Repair repaired your Ubuntu install in UEFI mode. Would be much better if sdb was repartitioned to gpt with its own efi partition for Ubuntu. But that will normally erase all data on that drive. There is a conversion program but I have not used it and it has some risks, so good backups required anyway.

If you go into UEFI and its boot menu can you directly boot Windows entry? Or one time boot key often f10 or f12 but varies by brand.
Grub only boots working Windows, and you often need the Windows repair flash drive to fix Windows. I understand the first time you boot Windows it tells you to make that repair disk.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

    
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

      
 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Sayre_Precure on 2015-03-25
I have all my important files backed up to an external hard drive, so I'm not really worried about wiping my other hard drives.  If I need to just restart and do this all over again, it wouldn't be a big deal.  I still have the Ubuntu installation on a liveUSB, and I also have the Windows 8 installation disc, but I haven't been able to boot from it.  Before I ran boot repair for the first time, the only option I had when booting was Ubuntu and Advanted options for Ubuntu.  Only after running boot repair did the other options show up.  

I'm not able to directly boot Windows from UEFI (unless I'm doing it wrong, which is possible.)

---

### Post by oldfred on 2015-03-25
You probably had Ubuntu in BIOS boot mode on sdb, and that cannot boot Windows in UEFI mode on sda. UEFI and BIOS are not compatible, you have to totally reboot to switch modes, or you cannot use grub menu to dual boot. But should be able to use UEFI menu to dual boot.

When not installed in the same mode it is a bit of a hassle to use UEFI menu. Many will boot from one time boot key, but others require you to turn on/off UEFI or CSM settings to change boot modes.

Did you leave Windows hibernated or its fast boot on? That almost always causes issues. Grub cannot boot Windows even if Ubuntu is UEFI if fast boot is on. And if the NTFS partition was resized then it needs chkdsk and possibly other Windows repairs. Almost all Windows repairs require Windows repairCD or flash drive. Sometimes you can use f8 to directly get into its own internal repair console if it starts to boot at all. 

Never booted Windows from UEFI. My last Windows was XP installed in 2006. Finally got rid of last app that I needed XP for about 3 years ago.

You need to run Windows fixes, the change to sdb to gpt and reinstall Ubuntu in UEFI mode is really optional, but once you have added lots of data and used it a lot then it becomes more difficult to convert. I would convert as I recommend once you start using UEFI all drives should be gpt partitioned. Since I knew I was eventually going UEFI, I started changing all new drives to gpt back with 10.10. Then XP was on a MBR drive and Ubuntu on a gpt drive but still in BIOS boot mode. Now all new drives including my flash drives are gpt partitioned, and have both efi partition and a bios_grub partition, so I could boot either way. Windows only will boot from gpt with UEFI, but Ubuntu can be configured for either BIOS or UEFI from gpt partitioned drives.

I did install a second Ubuntu on sdb, and even though I specified sdb as location for grub2's efi boot files, it installed (and overwrote) my Ubuntu boot on sda. I just copied those files to sdb, and  reinstalled grub2's efi files to sda. Better to have backup of efi partition.  Efi files do not need an install, you can just restore them to an efi partition and they should work.

---

### Post by Sayre_Precure on 2015-03-25
Okaaaaaaaaay, finally starting to get things worked out.  I disabled everything but my Windows installation disk, then ran it and I'm back on Windows on a MBR partitioned disk in BIOS boot mode. From here, the best thing to do is install Ubuntu in a GPT partitioned disk in BIOS, correct?

---

### Post by oldfred on 2015-03-25
I would. There are some minor advantages to gpt over MBR. And if gpt partitioned you could later convert BIOS boot of Ubuntu to UEFI boot.

You do need to use Something Else and make sure to tell installer to install grub2's boot loader to the MBR of sdb. That is a combo box at bottom of partition screen. I like to partition in advance with gparted so I can include both an efi partition which UEFI says should be first or at least near beginning of drive and the bios_grub partition which is required for grub to install correctly to the protective MBR with gpt partitioning. Gpt just has a MBR so old tools do not think drive is blank and overwrite it. And that MBR is what grub can use for BIOS boot.

 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
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

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Sayre_Precure on 2015-03-25
Got it. Thanks again for all your help. Closing the thread now.

---

### Post by sisqonrw on 2015-12-18
Hi I am from Germany.
I have the same problem.can you tell  a stupid boy how he can fix the problemin a easy way.
I need urgent help. there are important files.

---

### Post by oldfred on 2015-12-18
@sisqonrw
Better to start your own thread. This is now older & Solved so few will look at it.
Put good title with issue and brand system. Include details of hardware and run the summary report from Boot-Repair and include that in your thread.

Did you review fixes suggested above and links posted above?

---

