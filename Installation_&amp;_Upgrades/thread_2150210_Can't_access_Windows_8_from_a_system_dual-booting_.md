---
title: "Can't access Windows 8 from a system dual-booting with 13.04 64-bit"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by thevisualboy37 on 2013-05-31
My computer is, unfortunately, affected by bug #1024383 (e.g. The "Windows 8 (loader)" option in GRUB2 does not load Windows, but instead gives me an error message). I booted from my LiveUSB and ran boot-loader as described [here]("https://help.ubuntu.com/community/UEFI") (step 5 under "Installing Ubuntu Quickly and Easily via Trial and Error"), to no success. All of the options that it added gave me a different message from the "Windows 8 (loader)" option. My system info is [here]("http://paste.ubuntu.com/5719692/"). I would appreciate any help you may have.

Also, I am running 64-bit versions of both operating systems (Ubuntu 13.04 and Windows 8).

Thank you in advance.

---

### Post by fantab on 2013-05-31
Have you tried '**[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")**'?

---

### Post by thevisualboy37 on 2013-05-31
Oh, whoops. I meant Boot-Repair, not Boot-Loader. Still didn't help. The Windows EFI option gives me a different message; I will take a picture momentarily. Also, since my computer didn't come with any restore discs, just a restore partition (which I also can't access), I can't get into a Windows command prompt to repair the MBR. I do have a Windows 7 repair disc, but that fails since my computer is in EFI mode with Secure Boot. I don't want to disable either of those options because I am very worried that I would mess my computer up to the point where I wouldn't be able to use it at all anymore. Also, I ran Boot-Repair a second time and it still didn't work, it gave me this URL: [http://paste.ubuntu.com/5719766](http://paste.ubuntu.com/5719766) (the first attempt gave me [http://paste.ubuntu.com/5719692](http://paste.ubuntu.com/5719692)).

---

### Post by thevisualboy37 on 2013-05-31
Here's the error message that all of the options Boot-Repair created gives me:[IMG]http://i42.tinypic.com/59tw5g.jpg[/IMG]

---

### Post by ubfan1 on 2013-05-31
It looks like some of the Windows menu items were corrected to what they should be by "boot-loader" = boot-repair.  What errors do you see for those (bug 1091464 type errors like: /EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image
? 
Anyway, try skipping the grub part, and early in the boot, hit the Function key which brings up the boot device choices (varies by machine).  Select the hard disk Windows, or just the hard disk if that's the only choice, then a windows should pop up to allow you to select either Windows or Ubuntu, try Windows.  That may work for you (it's what I need to do on a Toshiba satelllite s855).

---

### Post by ubfan1 on 2013-05-31
Yup, that's the bug, do add yourself and your machine to the bug.  Another workaround I found was to have a usb  set up with just the EFI partition, copy of the existing one is good, but for the /EFI/Boot/bootx64.efi, make sure it's a copy of the ORIGINAL /EFI/Microsoft/Boot/bootmgfw.efi  (which boot-repair has probably renamed to bkpbootmgfw.efi.  Get directories with sizes of all your efi files and you can tell (hopefully) which are copies of shim.efi.

---

### Post by thevisualboy37 on 2013-05-31
Unfortunately, my UEFI doesn't let me press a key to select a boot device. I have to change the boot order by choosing the "System setup" option in GRUB2. Even by doing that, and putting my "SATA hard drive" and the two "Windows loaders" before "ubuntu", I still get to GRUB2 and the Windows options still give me errors.

---

### Post by ubfan1 on 2013-05-31
You can look at the efi boot possibilities with "sudo efibootmgr -v" also, and confirm that a Windows one points to /EFI/Microsoft/Boot/bootmgfw.efi
However, boot-repair had dumped a copy of shim there, so you are not really booting windows, but get to grub, as you have seen.  Either manually rename the bckbootmgfw.efi file to bootmgfw.efi, or maybe boot-repair's restore backup function will do the job.  Or as I mentioned, have the bckbootmfgw.efi on a usb stick with gpt partition table, with a 250M FAT32 EFI partition named /EFI/Boot/bootx64.efi (and probably need the files in /EFI/Microsoft... too.)

---

### Post by thevisualboy37 on 2013-05-31
Hmm... I actually don't see /EFI in the root directory. The files are located in /boot/efi/EFI/Microsoft/Boot, for some reason.

---

### Post by ubfan1 on 2013-05-31
Sorry, I was referring to the partition itself, which does get mounted at /boot/efi.  Those are your EFI booting files.  They are just files, so you can copy them to backup, rename them, etc.

---

### Post by thevisualboy37 on 2013-05-31
All of the files are there, and they are all correctly named. How would I go about setting up a partition on my flash drive or portable hard drive? Should I use something like GParted?

---

### Post by ubfan1 on 2013-05-31
The names are less meaningful after boot-repair runs, so do look at the sizes too.  Every .efi file the same size as /boot/efi/EFI/ubuntu/shimx64.efi is really shimx64.efi, not what it's name indicates.  The originals should still be around with a "bkp" suffix or prefix.   Use gparted and a small empty USB (only 250M needed for the EFI partition).  Nothing on the USB will be available after putting a gpt partition table on it, so remove any of your files.  I'd delete all the existing partitions, then put a new gpt partition table on it it.  then make a new partition 250M, FAT32, boot flag, and format it.  You can then just mount it if it does not automount, and copy all the directories and files from /boot/efi onto the mounted USB.  Now the removable media EFI works a little differently than the hard disk's EFI -- the first thing run is /EFI/Boot/bootx64.efi, so copy the Windows boot loader (/EFI/Microsoft/Boot/bootmgfw.efi)  to that name/location.  Have the USB first in boot order in your BIOS/UEFI settings, and you should be able to boot Windows when the stick is present.  I did things the reverse since my hard disk booted Windows.  I copied /EFI/ubuntu/shim.efi to the bootx64, also had the signed grubx64.efi in /EFI/Boot, and a copy of grub.cfg in /EFI/ubuntu.  You can set up another USB to boot ubuntu, since the hard disk's EFI files tend to be changed in bad ways when installs/updates are done from Windows.  Good to have a working boot USB 7for either system.

---

### Post by thevisualboy37 on 2013-06-01
It seems I can't mount it. What should I do with the unallocated space, if anything?

---

### Post by ubfan1 on 2013-06-01
If you're really short of storage, you could add another partition for data storage I guess, it shouldn't interfere with the boot.  
Did you put a filesystem (format the partition) on the partition? (sudo mkfs -tvfat /dev/sdb1 or your actual device)  It won't mount without a filesystem.  With a filesystem, I think it will mount automatically under /media/...  so then just copy everything (sudo cp -R /boot/efi  /media/whatever/sdb1).

---

### Post by thevisualboy37 on 2013-06-01
I did that, and it still didn't mount. I had to set up another partition, also in FAT32, but not bootable, for it to work. Unfortunately, only that particular partition was mounted. It seems a 250 MiB partition is too small to be mounted.
In the end, it still booted from my hard drive, not my flash drive.

---

### Post by ubfan1 on 2013-06-01
Odd, never heard of a partition beeing to small to be moutned.  Anyway, feel free to make it bigger -- the whole USB is used for the live media partition, which contains the /EFI directory and files.  Is the boot flag on the partition and the USB device before the hard disk in the boot order?

---

### Post by thevisualboy37 on 2013-06-01
Actually, it seems I was wrong. It was too small to be "checked", but it doesn't mount when the boot flag is set. I had forgotten to set the boot flag that time; should I put the files on there first, and then set a boot flag? As for the boot order, yes, my flash drive is listed first.

---

### Post by ubfan1 on 2013-06-01
The order doesn't matter, but I'd expect you to set  the boot flag when you created the partition.   With the USB first in boot order, the boot flag on the EFI partition, and its contents everything from EFI (inclusive) on down from /boot/efi/EFI, and the UEFI boot enabled, and secure boot enabled, it should boot to whatever you copied the /EFI/Boot/bootx64.efi file from (for Windows, that's /EFI/Microsoft/Boot/bootmgfw.efi).

---

### Post by thevisualboy37 on 2013-06-01
Well, for whatever reason, it didn't. I did everything exactly in that order, but for some reason, it just keeps going to the hard drive. I've even checked: my USB devices are at the very top of my boot order.

---

### Post by ubfan1 on 2013-06-02
Lets take a look, in a terminal, run the following and post the output here.

cd  to where ever the USB is mounted and 
cd EFI
ls -l  */* | grep -v "^d"
That should give the items of interest, skipping the language directories.

---

### Post by fantab on 2013-06-02
What is your Laptop/desktop model? What are its specs?

Have you disabled 'Fast Startup' in Windows8? 'Fast Startup' feature in Win8 'Hibernates' your computer rather than do a proper 'Shutdown'. So in order to dual-boot it is necessary that you shutdown your computer.
To disable 'Fast Startup':[ http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") . However, there are some OEM machines on which we need this to be able to boot Win8.

If you are on an Intel based machine, check if you have 'Intel Smart Response Technology' [Intel SRT] Enabled, if you are dual booting then 'Instel SRT' MUST be Disabled. 

Check your UEFI/BIOS settings for 'Fast Boot/Quick Boot', there are certain OEM machines that need this feature to be able to boot Winows8, others don't.

As of now, what exactly is your problem with Dual Boot?
Are you able to boot Windows8?
Are you able to boot Ubuntu from HDD?
Are you able to boot Ubuntu LiveDVD/USB?

If you are able to boot in any Ubuntu then post the output of:
```
sudo parted -l
```

Remove Ubuntu completely from the Machine and do Windows 8 recovery, if needed. We can install Ubuntu later.

---

### Post by thevisualboy37 on 2013-06-02
My laptop is a Samsung Series 3 NP300E5E-A20US, 2.5 GHz Intel Core i3, 4 GB (GiB) RAM, 750 GB (GiB) HDD. There is no SRT option in my Phoenix UEFI. Re-enabling "Fast BIOS Mode" did not help me, I still can't boot into Windows.
The output from parted:
```
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  524MB  523MB   ntfs            Basic data partition          hidden, diag
 2      524MB   839MB  315MB   fat32           EFI system partition          boot
 3      839MB   973MB  134MB                   Microsoft reserved partition  msftres
 4      973MB   562GB  561GB   ntfs            Basic data partition
 7      562GB   723GB  162GB   ext4
 8      723GB   727GB  3982MB  linux-swap(v1)
 5      727GB   749GB  21.6GB  ntfs            Basic data partition          hidden, diag
 6      749GB   750GB  1074MB  fat32           Basic data partition          hidden, diag


Model: Seagate Portable (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs         boot
```

How can I safely uninstall Ubuntu without ruining my OEM Windows install? My computer came with no recovery disks, just a recovery partition.

---

### Post by ubfan1 on 2013-06-02
Samsung!!!!! Oh Oh, google "samsung uefi brick"  Not sure your 300E5E is affected but the 300E5C is.  Apparently, Samsung skimped on the non-volitle memory, and adding things tends to brick the machine.  Do a bit of research, and if your machine is affected, MAYBE you can avoid problems by sticking to USB boots (since I think they do not make NVRAM changes, but I could be wrong).

---

### Post by thevisualboy37 on 2013-06-02
I am aware of this problem. My laptop does not appear to be affected, since it still boots into Ubuntu via the SATA hard drive; it's just booting into Windows that's the problem. I can't even do that through USB.

---

### Post by thevisualboy37 on 2013-06-02
It seems that after doing ubfan1's solution again, except formatting the entire flash drive instead of just creating a smaller partition, I was able to boot into Windows from my flash drive. Sorry, but with my current computer, dual-booting with Ubuntu was just too much of a hassle. I booted from a Windows Repair Disc and ran "bootrec /fixmbr" and "bootrec /fixboot", removed my Ubuntu partitions, and changed my UEFI settings so Ubuntu was the very last option. Now I can boot into Windows without having to insert my flash drive. I would like to thank ubfan1 once again for his help. My issue is officially solved.

---

