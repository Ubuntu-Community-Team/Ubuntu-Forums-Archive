---
title: "boots straight to Win, boot-repair complains about EFI"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by CaptainPants on 2012-05-17
Hi,

I got a laptop that came with Windows 7 installed and already had 4 primary partitions taken up, so I deleted one (so far Windows was still working fine without it) so I could dual boot it.

Then I created an extended partition and used the manual option in the Kubuntu installer (the guided option only offered to format the whole disk) using /sda for the grub install. It seemed to go okay, but when I rebooted it went straight to Windows.

I ran boot-repair from the live CD, got this error "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, >200Mo, start of the disk}, EFI flag). Do you want to continue?" I started off just saying continue as per [this suggestion](https://answers.launchpad.net/boot-repair/+question/186958).

Now it won't boot anything from the hard drive and I get this message when I turn it on:

> Initializing and establishing link...
Media test failure, check cable
Exiting Intel Boot Agent.

This is the pastebin boot-repair uploaded: [http://paste.ubuntu.com/991780/](http://paste.ubuntu.com/991780/)

I guess from the error message and launchpad link the next thing to try is making an EFI partition, however I'm unsure how to do this at the "start of the disk" without wrecking Windows (as it is currently at the beginning).

Any help would be great. Thanks!

---

### Post by darkod on 2012-05-17
And did you check in bios whether the boot is really in EFI mode? See if there is a setting to disable EFI.

The first partition, sda1, might actually have been an EFI system partition, I can't say.

---

### Post by CaptainPants on 2012-05-17
> **darkod said:**
> And did you check in bios whether the boot is really in EFI mode? See if there is a setting to disable EFI.
Thanks for the reply. Didn't see anything about it in the BIOS.

> **darkod said:**
> The first partition, sda1, might actually have been an EFI system partition, I can't say.
Does that mean I should be trying to install grub there instead of sda?

---

### Post by darkod on 2012-05-17
No, right now you shouldn't install grub2 there because the partition is now reported as ntfs, not as EFI system.

From live mode, can you open sda1 with the file browser and see which files are there? Does it have some files/folders with 'efi' in the name?

---

### Post by CaptainPants on 2012-05-17
Didn't see anything, output is the second code snippet below.

Partially out of curiousity and also in case I need Windows in the meantime (for now I don't), would I be able to change the boot flag from sda7 to one of these other partitions and probably boot into windows?

```

kubuntu@kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x585dad4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   443664383   221626368    7  HPFS/NTFS/exFAT
/dev/sda3       946051072   976361471    15155200   12  Compaq diagnostics
/dev/sda4       443666430   946051071   251192321    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       443666432   443858943       96256   83  Linux
/dev/sda6       443860992   447764479     1951744   82  Linux swap / Solaris
/dev/sda7   *   447766528   479014911    15624192   83  Linux
/dev/sda8       479016960   946051071   233517056   83  Linux

Partition table entries are not in disk order

```

```

kubuntu@kubuntu:~$ mkdir mnt
kubuntu@kubuntu:~$ mount /dev/sda1 mnt/ -t ntfs
mount: only root can do that
kubuntu@kubuntu:~$ sudo mount /dev/sda1 mnt/ -t ntfs
kubuntu@kubuntu:/mnt$ cd ~/mnt/
kubuntu@kubuntu:~/mnt$ ls -R | grep efi
kubuntu@kubuntu:~/mnt$ ls -R
.:
Boot  bootmgr  boot-sav  MFGSTAT  sdrive  System Volume Information

./Boot:
BCD       boot.sdi      de-DE  fi-FI  it-IT        nb-NO  pt-PT  zh-CN
BCD.LOG   BOOTSTAT.DAT  el-GR  Fonts  ja-JP        nl-NL  ru-RU  zh-HK
BCD.LOG1  cs-CZ         en-US  fr-FR  ko-KR        pl-PL  sv-SE  zh-TW
BCD.LOG2  da-DK         es-ES  hu-HU  memtest.exe  pt-BR  tr-TR

./Boot/cs-CZ:
bootmgr.exe.mui

./Boot/da-DK:
bootmgr.exe.mui

./Boot/de-DE:
bootmgr.exe.mui

./Boot/el-GR:
bootmgr.exe.mui

./Boot/en-US:
bootmgr.exe.mui  memtest.exe.mui

./Boot/es-ES:
bootmgr.exe.mui

./Boot/fi-FI:
bootmgr.exe.mui

./Boot/Fonts:
chs_boot.ttf  cht_boot.ttf  jpn_boot.ttf  kor_boot.ttf  wgl4_boot.ttf

./Boot/fr-FR:
bootmgr.exe.mui

./Boot/hu-HU:
bootmgr.exe.mui

./Boot/it-IT:
bootmgr.exe.mui

./Boot/ja-JP:
bootmgr.exe.mui

./Boot/ko-KR:
bootmgr.exe.mui

./Boot/nb-NO:
bootmgr.exe.mui

./Boot/nl-NL:
bootmgr.exe.mui

./Boot/pl-PL:
bootmgr.exe.mui

./Boot/pt-BR:
bootmgr.exe.mui

./Boot/pt-PT:
bootmgr.exe.mui

./Boot/ru-RU:
bootmgr.exe.mui

./Boot/sv-SE:
bootmgr.exe.mui

./Boot/tr-TR:
bootmgr.exe.mui

./Boot/zh-CN:
bootmgr.exe.mui

./Boot/zh-HK:
bootmgr.exe.mui

./Boot/zh-TW:
bootmgr.exe.mui

./boot-sav:
log  mbr_backups

./boot-sav/log:
2012-05-17__04h17boot-repair18  boot-repair

./boot-sav/log/2012-05-17__04h17boot-repair18:
2012-05-17__04h17.boot-repair.log.paste  sda   sda3  sda8
2012-05-17__04h17.boot-repair.log.tee    sda1  sda5  sources.list
RESULTS.txt                              sda2  sda7  sources.list_after

./boot-sav/log/2012-05-17__04h17boot-repair18/sda:
current_mbr.img  partition_table.dmp

./boot-sav/log/2012-05-17__04h17boot-repair18/sda1:

./boot-sav/log/2012-05-17__04h17boot-repair18/sda2:

./boot-sav/log/2012-05-17__04h17boot-repair18/sda3:

./boot-sav/log/2012-05-17__04h17boot-repair18/sda5:
grubenv

./boot-sav/log/2012-05-17__04h17boot-repair18/sda7:
etc_fstab_new  etc_fstab_old  grub_before_purge

./boot-sav/log/2012-05-17__04h17boot-repair18/sda8:

./boot-sav/mbr_backups:

./MFGSTAT:
ACTIVE.SCP    CPART.SCP  drive_clean_0.scp   removec.scp  SPART.SCP
aod.dat       cri.mop    drive_rescan_0.scp  removed.scp  tester.log
boottype.dat  DPART.SCP  filter.mop          removeS.scp

./System Volume Information:
tracking.log
kubuntu@kubuntu:~/mnt$ 

```

Thanks.

---

### Post by darkod on 2012-05-17
Yeah, looks like no efi at sight.

Yes, you can change the boot flag easily with Gparted (if you prefer GUI), or parted in terminal.

In Gparted you need right-click on the partition, Manage Flags, then deselect it on sda7, and select it on sda1.

In parted the command is (use the partition number instead of X, only the number, 1,2,3, etc):
parted> set X boot on (or off)

Of course, to enter parted you do:
sudo parted /dev/sda

And you can print the table to confirm partition numbers and flags with:
parted> print

Note that just changing the boot flag can't boot windows. You need windows bootloader (or at least lilo mbr) on /dev/sda too.

---

### Post by CaptainPants on 2012-05-19
Does Ubuntu have a different installer than Kubuntu? (The Kubuntu one didn't really seem familiar.) 
 
I'm tempted to just install Ubuntu and then KDE on top of it because other distros have installed grub just fine on this same laptop with the same partitioning scheme. (But so far this is the only distro the wifi has worked with... Linux problems haha, this is almost always how I end up choosing a distro.)

---

### Post by darkod on 2012-05-20
I haven't installed kubuntu so I can't really say about differences in the installer.

I wouldn't blame only linux here. Something weird happened but I can't know when or how. The sda1 partition does seems as if it was EFI and you were using EFI boot. But now the partition type doesn't say EFI.

I say this because of the label on the partition. In standard BIOS boot, the 100MB win7 partition is usually only 100MB, and the label is "System Reserved".

In your case, sda1 is more than 200MB (but not exactly 200MB), and the label is "SYSTEM_DRV".

Sometimes manufacturers make UEFI so that it can boot UEFI if it finds it, and continue to boot BIOS mode if it doesn't find UEFI files. But I have no idea how this process would work on windows and linux. Since unfortunately manufacturers pay much more attention when developing for windows, maybe they developed that process having windows in mind and not caring muhc how linux would react.

It clearly shows you a message you are in UEFI boot, which means it detects it somewhere. And not on the hdd.

---

### Post by CaptainPants on 2012-05-20
Oh I wasn't blaming Linux. ;) On the contrary, that was intended as a bit of a stab at the Windows-centric state of things making it difficult to find a distro that works out-of-the-box for a given PC.

Thanks for your help.

---

### Post by darkod on 2012-05-20
Even linux tools show that you have standard msdos table disk. Even if sda1 was EFI System type, that's long gone.

However, linux does show you the message that you are in EFI boot mode with no EFI system partition.

I wonder if it would help you to double check again there is no option to disable EFI boot in the bios, and also to google your exact model and something like "how to disable uefi(efi) boot".

---

### Post by YannBuntu on 2012-05-21
Hello

> **CaptainPants said:**
> This is the pastebin boot-repair uploaded: [http://paste.ubuntu.com/991780/](http://paste.ubuntu.com/991780/)

The "EFI detected" message of Boot-Repair comes because some elements of your session are EFI (in your dmesg). However, as Windows seems to boot without EFI, you may be able to boot Ubuntu without EFI too, so ignore this warning for the moment. (but please check if you can disable EFI in your BIOS as suggested by darkod).

Your /boot partition is far (>100Go) from the beginning of the disk, that is sometimes a problem. If i were you, i would try the "out-of-disk" option (run Boot-Repair, update it, click "Advanced options", go to the "GRUB options" tab, tick the "out-of-disk" option, apply, indicate the new URL that will appear). 
If that does not work, i would reduce the sda2 partition (via Windows tools) then create a /boot partition closer from the beginning of the disk. Don't forget to backup your documents on external disks (or DVDs) before any operation.

---

### Post by CaptainPants on 2012-05-25
Thanks for the replies. I have double checked in the BIOS and tried googling this laptop model, but can't find anything about disabling EFI/UEFI.

The out-of-disk option didn't fix it. I'm unable to get Windows to boot so I think before attempting to resize its partition I'll first see if I can get one of the distros that did get grub working to detect Ubuntu (and hopefully Windows too).

Oh, and I have since tried installing Ubuntu (rather than Kubuntu). Although the installer is very similar, the Ubuntu one gives the option of installing alongside existing OSes (including Windows) where the Kubuntu one only offered to format the whole drive. So unless it was related to something I tried between those installs, it seems like there are some differences between the installers.

---

