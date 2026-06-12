---
title: "Ubuntu installer does not recognize presence of Windows 10"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by caerolle on 2018-08-15
Sorry, I know this has been posted like 1000X. I think I have read 1001 of those, some multiple times, and am still stumped. I have read wikis, various tutorials, all kinds of things, and am stuck-stuck...

I am trying to dual-boot Kubuntu with Windows 10, and the installer consistently ignores that Windows 10 is there.

I am trying to install on an older HP computer with a second-gen i3 that came with Windows 7, which I replaced with 10 via a new copy and clean install a couple of years ago. In spite of this, the system still uses UEFI. Which shouldn't be a big deal, I have done all the things I found that should work with that: disabled fast boot, disabled hibernation, made sure that Secure Boot was off (which I would think I couldn't even boot from my USB is Secure Boot was installed...), and when I boot, it is seeing the USB as a UEFI drive. I even tried mounting the partition corresponding to the 'C' drive to see if that gave the installer a clue.

I am just going in circles reading google results, nothing new that helps. I even tried searching for a way to set up the dual boot manually, and didn't find anything of use. Any help would be appreciated.

Thanks so much!

Carol :)

---

### Post by oldfred on 2018-08-15
Is Windows installed in UEFI mode, your original Windows 7 may not have been UEFI/gpt?

Post this:
sudo parted -l
sudo gdisk -l /dev/sda

Have you turned off Windows 10 fast start up? Windows will keep turning it back on with updates.

---

### Post by caerolle on 2018-08-16
I have no idea whether or not the computer originally had UEFI, it wasn't something I had to worry about when installed Windows 10. Seems to only be an issue with linux.~

Fast start-up is off, and hibernation is never used on this system, so not shutdown under hibernation (plus, I have rebooted like 20 times trying to do this install, lol).

Wrt the disk commands, see below. I have a 24 GB block that is currently unformatted that I plan to use for the linux partition.

Thanks for your help!

Carol :)


parted -l:

kubuntu@kubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  316MB  315MB  ntfs         Basic data partition          hidden, diag
 2      316MB   420MB  105MB  fat32        EFI system partition          boot, esp
 3      420MB   555MB  134MB               Microsoft reserved partition  msftres
 4      555MB   101GB  101GB  ntfs         Basic data partition          msftdata
 5      128GB   128GB  472MB  ntfs                                       hidden, diag


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdd: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8020MB  8018MB  primary  fat32        boot, lba


sudo gdisk -l /dev/sda:

kubuntu@kubuntu:~$ sudo gdisk -l /dev/sda                                                                     
GPT fdisk (gdisk) version 1.0.3                                                                                        
                                                                                                                           
The protective MBR's 0xEE partition is oversized! Auto-repairing.                                                             
                                                                                                                               
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Model: SAMSUNG SSD 830 
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 702E82F8-0CC1-4068-B4DB-E39D82853DD0
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 51204717 sectors (24.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   2700  Basic data partition
   2          616448          821247   100.0 MiB   EF00  EFI system partition
   3          821248         1083391   128.0 MiB   0C01  Microsoft reserved ...
   4         1083392       197945343   93.9 GiB    0700  Basic data partition
   5       249145344       250066943   450.0 MiB   2700

---

### Post by oldfred on 2018-08-16
How you boot install media UEFI or BIOS is then how it installs. That is for both Windows & Ubuntu. Your UEFI should give two boot options for booting USB installer.
Since drive is gpt and you have an ESP - efi system partition, your Windows is installed in UEFI boot mode. You need to be sure to boot Ubuntu installer in UEFI boot mode. More info in link in my signature below.

Many have had to update UEFI from vendor. And some have had to update firmware for SSD.
What model system? HP has not been good about dual boot. It outright violates UEFI spec that says NOT to use description as part of boot. But multiple work arounds, depending on configuration.

If both UEFI and SSD firmware are newest versions, then Windows fast start up is often the major issue why Ubuntu cannot see NTFS partition(s).  Note that Windows turns fast start up back on with updates and updates may be in back ground. So if issues check that first.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html


[/URL]

---

### Post by caerolle on 2018-08-16
fred, thanks for your help! However, I am replying from my new installation of Kubuntu, lol. Just finishing setting things up, such as creating an account for my wife, and customizing things. I was going to post back here in a few minutes, sorry I did not get that done before you wrote another reply.

So, how did I get it work? I read a lot more about UEFI, and about people's troubles with getting a dual boot to work, and in the end it seemed that either it was going to work if I went through Manual even though it didn't seem to mention Windows, or if it didn't, I likely could fix the boot stuff one way or another. So I tried it. I was not too worried, as I made a system image and a recovery disk for Windows before I even started at all (plus copied all her files elsewhere in case recovery did not work and I had to do a full install of Windows from scratch). And it actually worked fine, booted up with options for Kubuntu and Windows both, and both work from the boot menu. Very smooth and easy, all the agonizing was really for nothing, but I guess I did learn yet a bit more about linux, lol.

Thanks so much for your help! Now to figure out how to mark this thread solved, lol.

Carol :)

---

