---
title: "Can't install 18.04 on Lenovo laptop"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2018-11-06
Let me start by explaining I have zero experience with linux type OSs. When I try to install lubuntu 18.04, the install hangs at installing grub2 package. I've tried with secure boot on and off. I've try a new download, and always stall while installing the grub2 package. I have also tried to install 18.10, and it hangs at 80%, "start procedure and passes 'fw_type" to other process. I'm using a lenovo ideapad 320 with the following specs:
Windows 10 Home 64-bit
Intel Celeron N3350 @ 1.10GHz dual core
4.00GB @ 814MHz (?-11-11-28)
motherboard LENOVO LNVNB161216 (U3E1)
Graphics
    Generic PnP Monitor (1366x768@60Hz)
    E32 (1366x768@60Hz)
    Intel HD Graphics (Lenovo)
931GB Seagate ST1000LM035-1RK172 (SATA )    38 °C
298GB Seagate ST332031 0CS SCSI Disk Device (USB (SATA) )
PLDS DVD-RW DA8AESH

I would prefer to dual-boot, but have tried using entire 300GB external for single boot,and just put up with going in and telling computer to boot from usb.
ANY suggestions would be greatly appreciated.

---

### Post by ubfan1 on 2018-11-06
Check your UEFI settings (BIOS, invoked by some key at power-up) for a preference of boot mode -- legacy over UEFI or UEFI over legacy.  Assuming your Windows is in UEFI mode, on a GPT partitioned disk, you need to install Ubuntu in UEFI mode.  Since the install media contains both legacy and UEFI bootloaders, if the preference is legacy (and your hard disk only contains UEFI, so you'd never notice), the install is attempted in legacy mode, and a GPT disk simply has no space between the partitions for installing grub.  How much free space does your EFI partition have?  Usually there's plenty of room for grub, but ...

---

### Post by coley9225 on 2018-11-06
I have a 260MB efi partition, not sure how much is used. My uefi is set for uefi boot, and tried to install 18.04 as uefi. I wiped my external hdd and set parions for efi, root (/ mount point) and swap. My thinking was just boot from usb and leave internal drid with windows totally out. I would think this would be like running live, but with all setting, files, etc. being saved. It still hangs up at installing the grrub2 package. Also, what format should I use for boot partition on external, I used fat32.

---

### Post by ubfan1 on 2018-11-07
The installer will put grub onto the first EFI it finds, the one on sda, your internal disk, regardless of what you specify as the location of the bootlaoder (bug 1173457).  This means the disk on the USB never gets anything installed into its EFI partition (so of course cannot be booted). However, the internal disk should have gotten the /EFI/ubuntu directory added (if room, so check the space on the internal EFI).  Try the EFI boot menu(some key at power-up to select boot device or OD) and see if ubuntu is a choice (not the external disk).  The EFI partition is just a FAT filesystem, so FAT32 should be fine.  You can just copy the internal EFI to the external disk's EFI and then boot should work (copy everything, it's good to have a backup of the microsoft files). You should also be able to run the installer in "try" mode, and install grub directly to the external disk. Last I checked, the --removable works, but the --uefi-secure-boot does not use shim (so you need to copy/rename shimx64.efi  from EFI/ubuntu.to  EFI/Boot/bootx64.efi and ensure grub.efi is present in EFI/Boot too.  Not sure why you got an error unless you ran out of room or had a corrupt filesystem on the internal EFI.

---

### Post by r_widell on 2018-11-07
I suspect @ubfan1 is correct wrt partitioning scheme. What's the output of ```
$ sudo fdisk -l
```

A FAT32 partition on a drive with a "Disklabel type:dos" is just a FAT32 partition, not an ESP (EFI System Partition).

ron

---

### Post by coley9225 on 2018-11-07
Earlier today, I did  new download from lubuntu.me. I verified the md5sum and used rufus to make a bootable flashdrive. It runs in live mode fine. I wiped my external drive and tried to install, using erase and use entire drive, that way the installer partitions the drive. It still hangs when installing grub2 package. I waited an hour plus, and just aborted install again. It's trying to install grub on external drive, not internal, which is what I want it to do. At this point I'm at a loss as to what else I can do. Maybe my computer just doesn't like linux OS at all.

---

### Post by r_widell on 2018-11-07
Oops, an error here.
An MBR partitioned drive CAN have an ESP (just make sure it's formatted as FAT32 and has the correct GUID).

ron

---

### Post by r_widell on 2018-11-07
> **coley9225 said:**
> Earlier today, I did  new download from lubuntu.me. I verified the md5sum and used rufus to make a bootable flashdrive. It runs in live mode fine. I wiped my external drive and tried to install, using erase and use entire drive, that way the installer partitions the drive. It still hangs when installing grub2 package. I waited an hour plus, and just aborted install again. It's trying to install grub on external drive, not internal, which is what I want it to do. At this point I'm at a loss as to what else I can do. Maybe my computer just doesn't like linux OS at all.

What happens if you ```
$ sudo dd if=/dev/zero of=/dev/sd<desired drive> bs=1M count=1
``` before you start the install process?

---

### Post by coley9225 on 2018-11-09
OK... I tried yet another download of iso, burned to dvd. It seemed to run fine in live, so I tried to install(again). Again it hung up when installing grub2 package.After 2 hours I made a note of what it was saying below progress bar, ( I assume this is log entries). It continues to go back and forth between 2 lines, with minor exceptions. I'll refer to them as line A and line B.
Line A:
/usr/lib/ubiquity/ubiquity/frontend/gtk_componets/nmwidgets.py:17:warning:source id ***** was not found when attemting to remove it GLib.source_remove(timeout_id)
Line b:
/usr/lib/ubiquity/ubiquity/frontend/gtk_componets/nmwidgets.py:133:warning:source  id ***** was not found when attemting to remove it  GLib.source_remove(self_rows_changed_id)
 The ****** is a number that changes with every line, increasing in value, is the only difference.
A this point I'm thinking either A, something interna with my machine,(hardware or setting or something)is fouling up the install or B, I have really bad luck with downloading the iso image. I may just order a dvd from osdisc so I have a known clean set of files and try again, or order the 32GB usb w/persistence and run that until I can afford anther computer. I' continue to search for a solution and checking back to this thread in the meantime.
Thanks for the help so far and for any future advise or ideas. You guys are great.

---

### Post by MoebusNet on 2018-11-09
Just in case you didn't notice, the Live-DVD has an option to check the DVD for errors (corrupted files, etc.) You can use this to make sure that you have a good copy of the .iso file. It should appear in the menu when booting from the Live-DVD.

---

### Post by coley9225 on 2018-11-09
Thanks. I did notice. after downloading the iso file, I verified the md5sum using quickhash. Then when I booted in the live cd, I did perform the check disk, and it checked fine. I'm getting closer to thinking a Lenovo computer just doesn't play well with non-windows op systems. Also note from my original post that I have tried lubuntu 18.10, hang at 80%,"starts procedure and passes 'fw_type' to other routine. I have also tried zorin, which hang at configuring hardware. I tried lubuntu 16.04, but mose is really jumpy and I didn't care for it.

---

### Post by r_widell on 2018-11-09
Hmmm, I vaguely recall having problems installing grub2 to a partition instead of a drive. But I can't recall for sure if that was a gpt or mbr partitioned drive.
I don't think it was gpt but I can't say for sure.

I'd still like to see the output of ```
sudo fdisk -l
```

Those error messages appear to be related to network manager (nmwidget), so I doubt that they're related to your grub installation issues.

A possible solution is to try installing grub from the installed system.
Download a copy of Super Grub2 Disk. It's available from [https://www.supergrubdisk.org/](https://www.supergrubdisk.org/) and is also available on most of the rescue CD/DVDs out there.
It can boot a system that doesn't even have a grub.cfg file (although that will be the first option, if it finds one).
It will search all the filesystems on a disk for vmlinuz and initrd and give you the option of booting using those files. (It can boot other OS, as well-- anything grub2 can boot).

When your OS is up issue the command ```
sudo grub-install /dev/sd<whatever drive you need to boot from>
```

Especially with gpt, you need to install to a drive (e.g. sda), not a partition (e.g. sda3). Grub2 will place the grub and shim (for secure boot) files into /EFI/ubuntu in the ESP.

If that doesn't work, I can only speculate until I have more info.

Good luck,
ron

---

### Post by coley9225 on 2019-02-22
I'm not sure if this qualifies as solved, as I still have no idea what keeps preventing the grub2 package from installing. That said, I was able to get a working lubuntu os on my computer. I went on the assumption that the os was installed, but was having trouble with the grub. I confirmed this using super grub2 disc and booting to lubuntu that way. After using powershell as an admin, clearing all ubuntu related entries from my efi partition ( more than once), I tried reinstalling grub from live usb with no luck. I finally ran across grub2win. It's available for multiple os so I used the win10 version. I added lububtu to the list as per the online manual, and now when i boot my computer, I'm greeted by grub2win grub menu and can choose win10 or lubuntu. Not really solving the original issue, but an easy work around that helped me get up and running. I hope someone else can use this to get their machine humming. I really want to thank everyone for the tips and ideas. I think that alone my motivate me to learn lubuntu and dump windows all together some day.

---

