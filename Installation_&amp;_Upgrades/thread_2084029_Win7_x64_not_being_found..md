---
title: "Win7 x64 not being found."
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by xirrin on 2012-11-14
So I went to install Ubuntu 12.04.1 alongside my Win7 x64 installation but every time I boot in to the installer it says that there are no other operating systems detected and gives me the standard "Use the entire disk" option or the "Something else" option instead of offering the "Install along with Windows 7" option.

I've run every boot/MBR fix on Hiren's Boot CD.

I've run Windows FIXMBR and Windows BIXBOOT commands in the recovery console.

I've run Boot Repair from Ubuntu.

I verified both Ubuntu and Windows disks by downloading a fresh copy, verifying MD5 hashes, and verifying the written image. In fact, I've done this twice and have had the same result with both Ubuntu and Windows disks. This is a legal copy of Windows 7 Pro x64 that I have used in the past with Ubuntu but had to reformat a couple of months ago and now just really really miss having Ubuntu. I would MUCH rather have it run native than virtualized.

Boot Repair: [http://paste.ubuntu.com/1356991/](http://paste.ubuntu.com/1356991/)

Does anyone have any suggestions to offer? I see that Boot Repair even seems to recognize that there is a Windows 7 setup on the disk, but I'm not sure what seems to be going wrong. I'm sure I could look up the appropriate partition sizes and install it manually, but then my fear is again of if GRUB will recognize Windows 7, or if I could even manually configure it to work properly. I'm much more comfortable with the automatic installation and would prefer to avoid doing it all manually at this time if that is possible.

Does anyone have any thoughts or suggestions?

---

### Post by arpanaut on 2012-11-14
Win is installed with UEFI, you will need to investigate:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I am Not experienced in this new technology but a few here are, hopefully they will appear...

---

### Post by oldfred on 2012-11-14
Since you have UEFI, did you download the 64 bit version? The 32 bit version does not support UEFI boot.

And then from the UEFI menu, you have to boot the installer flash drive in UEFI mode. If you have Windows 8, Ubuntu 12.10 should work with either UEFI secure bit on or off.

Other reasons why Ubuntu may not see Windows are RAID or needing chkdsk in Windows. Do you have Intel SRT which uses RAID?

---

### Post by xirrin on 2012-11-14
Fantastic. I forgot that I swapped motherboard/CPU a couple months ago before I went on a bunch of work trips and haven't tried since the swap. Yes - UEFI is on there and something that I am not familiar with at all. I'll have to see if I can disable that at all.

What I am confused about is that all the documentation keeps pointing to the x64 mode as support UEFI, but these are x64 disks of 12.04.1 so I'm unsure why it isn't detecting problem since it seems it should be. I'll have to follow the documentation a bit when I get home and see what I can do.

---

### Post by oldfred on 2012-11-14
If hard drive is older, it probably is still MBR(msdos) and you have the 4 primary partition limit. 

With gpt partitiong used with UEFI there is no primary partition limit.

post this for every drive if more than one:
sudo parted /dev/sda unit s print

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by xirrin on 2013-02-12
[http://paste.ubuntu.com/1641116/](http://paste.ubuntu.com/1641116/)

I had Win7 installed, but Ubuntu couldn't detect the partitions when I would try to install it. Some research said that I needed to use gdisk and convert to MBR, so I did. Now I have Ubuntu and Win7 installed side-by-side but when I go to boot into Windows I get the "no EFI file" error message and right back to the grub menu. Any ideas? 

Also - as requested:

```
ethan@RODGERS:~$ sudo parted /dev/sda unit s print
[sudo] password for ethan: 
Model: ATA WDC WD7502AAEX-0 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start        End          Size        File system     Name                  Flags
 1      2048s        206847s      204800s     ntfs            Microsoft basic data
 2      206848s      512002047s   511795200s  ntfs            Microsoft basic data
 3      512002048s   512196607s   194560s     fat32                                 boot
 4      512196608s   1431670783s  919474176s  ext4
 5      1431670784s  1465147391s  33476608s   linux-swap(v1)

ethan@RODGERS:~$ 

```

---

### Post by oldfred on 2013-02-15
You are showing gpt partition table. Windows only boots from gpt with UEFI. Ubuntu will boot from gpt with either BIOS or UEFI.

Your efi partition only has grub in it not any Windows boot files.

Both Ubuntu & Windows install in UEFI mode if installer is booted  from UEFI in UEFI mode. Or in if booted in BIOS mode will install in BIOS. And if you want to easily dual boot both must be in same mode.

Since you also do not have the system reserved, you must have installed Windows in BIOS mode?
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you convert back to MBR, you will have to totally reinstall grub. It is using grub-efi and you will need grub-pc for BIOS boot.

---

