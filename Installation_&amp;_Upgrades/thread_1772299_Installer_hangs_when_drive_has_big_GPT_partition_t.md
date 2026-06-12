---
title: "Installer hangs when drive has big GPT partition table"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-05-31
I tried installing 11.04, 10.10, and 10.04.2 (desktop-amd64) on a machine that has an existing GPT partition table.  For 11.04 and 10.10, the installation just hangs right after the menu window that verifies enough disk space, power, internet connection, and asks if I want to upgrade while installing and if I want to add mp3 codecs.  When I click forward on that panel, the pointer becomes a rotor and it stays that way.  I let it go for 45 minutes.  For 10.04.2, the hang happens after it asks for my keyboard layout (defaulted to US so I just clicked forward).

I backed up the 67 sectors of the GPT partition table (34 at start, 33 at end), zeroed out those 67 sectors, and ran fdisk to make a legacy MBR partition, specifying just 4 partitions where I wanted Ubuntu to be installed (1=/, 2=swap, 3=/tmp, 4=/home), having the same exact sector numbers as the intended location under GPT.  This install worked and was bootable.  However, it wasn't usable because I needed to restore the GPT table to use the other systems already installed, and that would conflict with the way GRUB was installed (overlaying where the GPT table goes).  I did the MBR install just to verify it was not some hardware issue with the machine.

So it is clearly something related to GPT, since it worked with MBR.  Could it possibly be the large number of partitions, because I had 53 (GPT supports 128 or more, so why not use them).  I know people have installed Ubuntu on GPT partitions before.  I have done so myself with the server edition (9.10, 10.04, and 10.04.2) but that was with only about 8 partitions.  But this time was with the desktop edition (and a lot more partitions).  Is the desktop edition not able to do GPT (under the assumption no one uses more than 2TB of drive space)?  Or maybe the udev setup in the ISO based system can't handle the inode major number for the higher partition numbers?

Alternate question: Is there a way, when installing with MBR, to force the next GRUB stage to go to sector 34 or higher, instead of sector 1?  Or maybe I should just have it not even install GRUB at all?

Any ideas before I file a bug report?

---

### Post by srs5694 on 2011-05-31
My guess is it's the large number of partitions you've got that's triggering a bug. I've done installs of Ubuntu to GPT disks with fewer partitions before, although I don't think I've done an 11.04 installation to GPT using a BIOS-based computer. (I've done 11.04 on a UEFI system and 10.10 using BIOS, though.)

You might try redoing your experiment in which you created an MBR equivalent of part of your drive, but instead leave it as GPT and delete all but the bare minimum number of partitions. If you get it installed, you can then restore your original partitions a few at a time. If it fails after you've restored a certain number, you'll have a hard limit. If you can restore all your partitions and still boot, you'll know the bug is in the installer alone.

FWIW, I've successfully tested disks with in excess of 100 partitions; however, this was on a Gentoo system. IIRC, there was once a limit of something on the order of 16 partitions per disk built into the kernel, but that limit has been overcome by use of udev. It's possible that Ubuntu's udev configuration doesn't raise this old limit, or only raises it to some level that's lower than whatever Gentoo does.

BTW, you can use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to back up and restore your GPT data; use the "b" option on the main menu to back up and "l" on the recovery & transformation menu to restore. I recommend you use this feature if you decide to do further experiments; there's less chance of an error if you restore the table and then delete individual partitions on each round than if you try to re-create them by entering start and end sector numbers.

---

### Post by Skaperen on 2011-06-01
> **srs5694 said:**
> My guess is it's the large number of partitions you've got that's triggering a bug. I've done installs of Ubuntu to GPT disks with fewer partitions before, although I don't think I've done an 11.04 installation to GPT using a BIOS-based computer. (I've done 11.04 on a UEFI system and 10.10 using BIOS, though.)I'm curious how UEFI would be involved.  My BIOS based computer boots Slackware on this setup, OK.  It just loads the MBR.  As long as the bootloader can find its extra code and find the images to load (LILO has a table of blocks, GRUB needs to find a filesystem and thus needs to find a partition, first), you can get a kernel up.  UEFI might expedite this or something.  If it know how to load images itself maybe we can bypass bootloaders (I'm not a fan of either GRUB or LILO).

> **srs5694 said:**
> You might try redoing your experiment in which you created an MBR equivalent of part of your drive, but instead leave it as GPT and delete all but the bare minimum number of partitions. If you get it installed, you can then restore your original partitions a few at a time. If it fails after you've restored a certain number, you'll have a hard limit. If you can restore all your partitions and still boot, you'll know the bug is in the installer alone.That's a good idea.  I will give it a shot this weekend.  And just in case it is the partition numbers themselves, maybe I should make the partitions for Ubuntu be lower (should be OK since an Ubuntu system finds filesystems to mount by UUID instead of static device names).

> **srs5694 said:**
> FWIW, I've successfully tested disks with in excess of 100 partitions; however, this was on a Gentoo system. IIRC, there was once a limit of something on the order of 16 partitions per disk built into the kernel, but that limit has been overcome by use of udev. It's possible that Ubuntu's udev configuration doesn't raise this old limit, or only raises it to some level that's lower than whatever Gentoo does.And the kernel has a chunk of device major/minor numbers that it can dynamically map to devices specified somewhere else in some other way.

From one of my servers with 4TB:
```
brw-rw---- 1 root disk   8, 0 2011-05-27 11:06 /dev/sda
brw-rw---- 1 root disk   8, 1 2011-05-27 11:06 /dev/sda1
brw-rw---- 1 root disk 259, 2 2011-05-27 11:06 /dev/sda128
brw-rw---- 1 root disk   8, 2 2011-05-27 11:06 /dev/sda2
brw-rw---- 1 root disk   8, 3 2011-05-27 11:06 /dev/sda3
brw-rw---- 1 root disk   8, 5 2011-05-27 11:06 /dev/sda5
brw-rw---- 1 root disk   8, 6 2011-05-27 11:06 /dev/sda6
brw-rw---- 1 root disk   8, 7 2011-05-27 11:06 /dev/sda7
brw-rw---- 1 root disk   8, 8 2011-05-27 11:06 /dev/sda8
brw-rw---- 1 root disk   8, 9 2011-05-27 11:06 /dev/sda9
brw-rw---- 1 root disk 259, 0 2011-05-27 11:06 /dev/sda90
brw-rw---- 1 root disk 259, 1 2011-05-27 11:06 /dev/sda99
```Notice the device numbers are contiguous ( 259,0 ... 259,1 ... 259,2 ) while the partitions are not ( 90 ... 99 ... 128 ).  But the lower partitions have a fixed relation.  IMHO, it would have been better to use a major number for each drive and a minor number for the partitions, although this would limit the kernel to 255 partitions, or partitions up to number 255, depending on how it is done.  Still, somewhere deep inside, things have to be mapped down to actual physical device addresses.  So at this point we have multiple layers of mapping and it becomes hard to identify which is which.  Plug in two identical factory fresh USB memory sticks and then invite another Linux expert to "format this one" pointing to one of them.

> **srs5694 said:**
> BTW, you can use [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") to back up and restore your GPT data; use the "b" option on the main menu to back up and "l" on the recovery & transformation menu to restore. I recommend you use this feature if you decide to do further experiments; there's less chance of an error if you restore the table and then delete individual partitions on each round than if you try to re-create them by entering start and end sector numbers.
I use gdisk.  But I have no idea where it is backing things up to.  What I normally do is "dd" the important sectors over to specific partitions on a USB memory stick.  That's generally the first 34 and last 33 sectors.  If a bootloader is already installed, I try to save the first 2048 or 4096 or 8192 sectors (this machine has partition 1 starting at 8192).  Bootloaders are not using anywhere near that much, yet, but at least GRUB seems to be headed that way (e.g. I will be calling it a "bloatloader", soon).

---

### Post by srs5694 on 2011-06-01
> **Skaperen said:**
> I'm curious how UEFI would be involved.

UEFI includes its own boot loader, which loads a file (with a .efi extension, typically) from the EFI System Partition (ESP), which is a FAT-32 partition on the main hard disk. The .efi file is then responsible for loading the OS kernel and handing off control to it.

In Linux, it's possible to compile GRUB 2 as a .efi file to serve as the second-stage boot loader (after the UEFI itself); or you can use a boot loader called ELILO. Ubuntu uses GRUB 2 by default, although an ELILO package is available, and in my limited experience, ELILO is more reliable and easier to configure. OTOH, ELILO can't chainload to another .efi file (AFAIK), so if you want to dual-boot with some other OS, you'll need to rely on the UEFI, the other OS's second-stage boot loader, GRUB 2, or a boot loader called rEFIt (which just selects .efi files) to do the job.

Of course, this is all of merely theoretical interest to you right now, since it sounds like you've got a BIOS-based computer. (If you're planning on buying a new system soon, though, it could be of practical importance in the near future.)

> I use gdisk.  But I have no idea where it is backing things up to.

It backs up to the file you specify. That file includes the current in-memory representations of the MBR, the main GPT metadata, the backup GPT metadata, and the GPT partition definitions (in that order).

> What I normally do is "dd" the important sectors over to specific partitions on a USB memory stick.  That's generally the first 34 and last 33 sectors.

That will work, but of course if you err in specifying the sector numbers, you'll have problems recovering!

---

### Post by psusi on 2011-06-01
It sounds like a bug from having so many partitions.  What you want to do is restore the GPT, create a small ( 1mb is more than enough ) bios_grub partition, then install grub2.  It will put the core image in the bios_grub partition.

---

### Post by georgemc on 2011-06-01
This might help.  Within the last 2 months or so I installed a new HD and converted over to GPT and from 32Bit to 64Bit at the time. For all intend and propose it was a fresh install of U10.04.2LST 64BIT.

The GPT did cause some frustration, had to use my PLOP disk to boot for a few days till I got it sorted out.

In the end I found this write up and it helped me.

[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

What I had to do was create a hybrid MBR to make things work.  I also left a 8Meg chunk of space unallocated at the beginning of the HD.  I have only a root, a home, ad a data partition on the HD.

I think there may be a different way to make things work, but for now or until I fire up my spare machine and do some research (read -> fiddling around) hybrid MBR works.

Its a lot of reading and I hope it points you in a good direction.

George

---

### Post by Skaperen on 2011-06-01
> **georgemc said:**
> What I had to do was create a hybrid MBR to make things work.  I also left a 8Meg chunk of space unallocated at the beginning of the HD.  I have only a root, a home, ad a data partition on the HD.That makes it sound like GRUB can't find the partition with the filesystem with a file it needs to load.  But on my servers, GRUB works with GPT.  Maybe the config file is just goofed up for the desktop install (and maybe only when GPT is used).  I hope you can eventually find what the specific cause of failing to work without the hybrid hack is.

---

### Post by srs5694 on 2011-06-01
> **georgemc said:**
> In the end I found this write up and it helped me.

[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)


That's my Web page, FWIW.

> What I had to do was create a hybrid MBR to make things work.  I also left a 8Meg chunk of space unallocated at the beginning of the HD.  I have only a root, a home, ad a data partition on the HD.

Some BIOSes have problems with booting from GPT. (It's not really the BIOS's place to care, but some do.) [This page of mine](http://www.rodsbooks.com/gdisk/bios.html) describes the issue in detail -- or at least, in as much detail as I know. (There's not a lot of information out there.) If your problems were related to this, then a hybrid MBR is one possible solution, but there are probably better ones, since hybrid MBRs are klunky and dangerous. If you've got an Intel motherboard, then a better solution is to go back to a regular protective MBR and then use Linux's fdisk to mark the one 0xEE partition it contains as bootable. Some non-Intel boards might work well with that tweak, too, but Intel boards are almost notorious for this issue.

A non-BIOS issue that sometimes causes problems is a lack of a [BIOS Boot Partition,](http://en.wikipedia.org/wiki/BIOS_Boot_partition) which makes GRUB 2 much more reliable on GPT disks. Sometimes GRUB 2 won't even install to a disk that lacks a BIOS Boot Partition. Fortunately, they can be quite small (as small as about 32 KiB), so you should have no problems fitting it into the 8 MiB gap you placed at the start of the disk. Once this partition is in place, you'll need to re-install GRUB.

---

### Post by Skaperen on 2011-06-01
> **srs5694 said:**
> UEFI includes its own boot loader, which loads a file (with a .efi extension, typically) from the EFI System Partition (ESP), which is a FAT-32 partition on the main hard disk. The .efi file is then responsible for loading the OS kernel and handing off control to it.
Well enough as long as the standards don't mandate the use of any of the patent encumbered aspects of FAT-32 (e.g. long file names and extended object attributes).

IMHO, the standard should be updated to support a free filesystem or two.  If they would like, I'd be happy to design a very simple filesystem, with just enough features to be usable for a collection of bootloaders, kernel images, RAM disk images, and file archive images, while still supporting file sizes in excess of 4GB.  It would all be based on existing technology that as far as I know has no patent encumbrances.

> **srs5694 said:**
> In Linux, it's possible to compile GRUB 2 as a .efi file to serve as the second-stage boot loader (after the UEFI itself); or you can use a boot loader called ELILO. Ubuntu uses GRUB 2 by default, although an ELILO package is available, and in my limited experience, ELILO is more reliable and easier to configure. OTOH, ELILO can't chainload to another .efi file (AFAIK), so if you want to dual-boot with some other OS, you'll need to rely on the UEFI, the other OS's second-stage boot loader, GRUB 2, or a boot loader called rEFIt (which just selects .efi files) to do the job.
Not clear, yet, is whether UEFI allows a choice in which file to load.  Either it would have to, or the UEFI code would have to hard code one (hopefully a standard one if this is the case).  If it does have a choice, is it a pretty menu, or something ugly and deeply hidden.  If the latter case, then a fancy bootloader in the .efi file would be what people want.  Otherwise (if UEFI does a nice job of choosing what to boot) we don't need anything more in the .efi file than just something that can actually load the whole kernel image and run it.  Hopefully, for that, the UEFI exports an API to read FAT-32 for the bootloader to use.

Linux once had a bootloader attached in front of it, for self loading on floppies.  Maybe one for UEFI can be made like that, so the merged file, in .efi format, can be placed in the ESP.

> **srs5694 said:**
> Of course, this is all of merely theoretical interest to you right now, since it sounds like you've got a BIOS-based computer. (If you're planning on buying a new system soon, though, it could be of practical importance in the near future.)This is a newly bought computer.  Will computers be advertising "Includes UEFI" or would that just happen when the manufacturer is ready to do it?

> **srs5694 said:**
> It backs up to the file you specify. That file includes the current in-memory representations of the MBR, the main GPT metadata, the backup GPT metadata, and the GPT partition definitions (in that order).At the time I'm running gdisk, the only filesystem(s) are all in RAM.  There is no persistent storage unless I plug something in.  Oh, of course, there is that disk I am working on.  But if I put it in some other partition which already has a filesystem, and then zap the partition table to do the Ubuntu install with minimal visible partitions, I can't get back to that filesystem to restore the partition table from, without first restoring the partition table.

> **srs5694 said:**
> That will work, but of course if you err in specifying the sector numbers, you'll have problems recovering!I do have the entire partition table layout generated by a script, which generates two forms, one being a gdisk input stream, and the other a printable text file which I have printed a couple copies of.  So I have a fallback.  And I have a USB memory stick with a couple little partitions on it to essential sectors in (e.g. the first 34 and last 33 for GPT).

BTW, I've heard that Windows will, intentionally, not be able to boot from a disk with GPT, unless the BIOS is UEFI.  Does that mean UEFI would be exporting a GPT access API that their bootloader would use?

---

### Post by Skaperen on 2011-06-01
Here is the big layout as generated by my script:
```
  -             0000            0            0            1 reserved MBR
  -             0001            1           33           33 reserved GPT
100             0034           34         8191         8158 bootloader
101       0004M+0000         8192       524287       516096 unused
  1       0256M+0000       524288      1048575       524288 sys 1 /boot
  2       0512M+0000      1048576      1572863       524288 sys 2 /boot
  3       0768M+0000      1572864      2097151       524288 sys 3 /boot
  4    1G+0000M+0000      2097152      2621439       524288 sys 4 /boot
  5    1G+0256M+0000      2621440      3145727       524288 sys 5 /boot
  6    1G+0512M+0000      3145728      3670015       524288 sys 6 /boot
102    1G+0768M+0000      3670016      4194303       524288 unused
 10    2G+0000M+0000      4194304      6291455      2097152 sys 1 /
 11    3G+0000M+0000      6291456      8388607      2097152 sys 1 /var
 12    4G+0000M+0000      8388608     12582911      4194304 sys 1 /var/log
 13    6G+0000M+0000     12582912     31457279     18874368 sys 1 /usr
 14   15G+0000M+0000     31457280     33554431      2097152 sys 1 /usr/local
 20   16G+0000M+0000     33554432     35651583      2097152 sys 2 /
 21   17G+0000M+0000     35651584     37748735      2097152 sys 2 /var
 22   18G+0000M+0000     37748736     41943039      4194304 sys 2 /var/log
 23   20G+0000M+0000     41943040     60817407     18874368 sys 2 /usr
 24   29G+0000M+0000     60817408     62914559      2097152 sys 2 /usr/local
 30   30G+0000M+0000     62914560     65011711      2097152 sys 3 /
 31   31G+0000M+0000     65011712     67108863      2097152 sys 3 /var
 32   32G+0000M+0000     67108864     71303167      4194304 sys 3 /var/log
 33   34G+0000M+0000     71303168     90177535     18874368 sys 3 /usr
 34   43G+0000M+0000     90177536     92274687      2097152 sys 3 /usr/local
 40   44G+0000M+0000     92274688     94371839      2097152 sys 4 /
 41   45G+0000M+0000     94371840     96468991      2097152 sys 4 /var
 42   46G+0000M+0000     96468992    100663295      4194304 sys 4 /var/log
 43   48G+0000M+0000    100663296    119537663     18874368 sys 4 /usr
 44   57G+0000M+0000    119537664    121634815      2097152 sys 4 /usr/local
 50   58G+0000M+0000    121634816    123731967      2097152 sys 5 /
 51   59G+0000M+0000    123731968    125829119      2097152 sys 5 /var
 52   60G+0000M+0000    125829120    130023423      4194304 sys 5 /var/log
 53   62G+0000M+0000    130023424    148897791     18874368 sys 5 /usr
 54   71G+0000M+0000    148897792    150994943      2097152 sys 5 /usr/local
 60   72G+0000M+0000    150994944    153092095      2097152 sys 6 /
 61   73G+0000M+0000    153092096    155189247      2097152 sys 6 /var
 62   74G+0000M+0000    155189248    159383551      4194304 sys 6 /var/log
 63   76G+0000M+0000    159383552    178257919     18874368 sys 6 /usr
 64   85G+0000M+0000    178257920    180355071      2097152 sys 6 /usr/local
 70   86G+0000M+0000    180355072    209715199     29360128 /home/sys0
 71  100G+0000M+0000    209715200    239075327     29360128 /home/sys1
 72  114G+0000M+0000    239075328    268435455     29360128 /home/sys2
 73  128G+0000M+0000    268435456    297795583     29360128 /home/sys3
 74  142G+0000M+0000    297795584    327155711     29360128 /home/sys4
 75  156G+0000M+0000    327155712    356515839     29360128 /home/sys5
 76  170G+0000M+0000    356515840    385875967     29360128 /home/sys6
 77  184G+0000M+0000    385875968    415236095     29360128 /home/sys7
 78  198G+0000M+0000    415236096    444596223     29360128 /home/sys8
 79  212G+0000M+0000    444596224    473956351     29360128 /home/sys9
  7  226G+0000M+0000    473956352    503316479     29360128 swap
  8  240G+0000M+0000    503316480    536870911     33554432 /tmp
  9  256G+0000M+0000    536870912   1953497087   1416626176 /home
128  931G+0512M+0000   1953497088   1953525134        28047 unused
  -  931G+0525M+1423   1953525135   1953525167           33 reserved GPT
  -  931G+0525M+1456   1953525168            -            - end of disk
```

---

### Post by Skaperen on 2011-06-01
> **srs5694 said:**
> That's my Web page, FWIW.



Some BIOSes have problems with booting from GPT. (It's not really the BIOS's place to care, but some do.) [This page of mine]("http://www.rodsbooks.com/gdisk/bios.html") describes the issue in detail -- or at least, in as much detail as I know. (There's not a lot of information out there.) If your problems were related to this, then a hybrid MBR is one possible solution, but there are probably better ones, since hybrid MBRs are klunky and dangerous. If you've got an Intel motherboard, then a better solution is to go back to a regular protective MBR and then use Linux's fdisk to mark the one 0xEE partition it contains as bootable. Some non-Intel boards might work well with that tweak, too, but Intel boards are almost notorious for this issue.

A non-BIOS issue that sometimes causes problems is a lack of a [BIOS Boot Partition,]("http://en.wikipedia.org/wiki/BIOS_Boot_partition") which makes GRUB 2 much more reliable on GPT disks. Sometimes GRUB 2 won't even install to a disk that lacks a BIOS Boot Partition. Fortunately, they can be quite small (as small as about 32 KiB), so you should have no problems fitting it into the 8 MiB gap you placed at the start of the disk. Once this partition is in place, you'll need to re-install GRUB.
The first OS I put on the machine is Slackware64 13.37.  That went into partitions 1,10,11,12,13,14.  The 2nd is Slackware 13.37 (the 32 bit version).  It went into partitions 2,20,21,22,23,24.  Ubuntu was supposed to be next, with the plan being 11.04-amd64, 11.04-i386, 10.04.2LTS-amd64, and 10.04.2LTS-i386.  The machine is targeted to be a development box.  Anyway, Slackware works just fine.  It installed with no issue, and it boots and runs with no issue.  So this box (a cheap $300 e-Machines box from Walmart) does not have any inherent issues with GPT.

---

### Post by srs5694 on 2011-06-01
> **Skaperen said:**
> Well enough as long as the standards don't mandate the use of any of the patent encumbered aspects of FAT-32 (e.g. long file names and extended object attributes).

You can download the latest specification from [the UEFI Web site.](http://www.uefi.org/specs/) (You've got to click a link, give your name, and agree to not further distribute the PDF.)

> IMHO, the standard should be updated to support a free filesystem or two.  If they would like, I'd be happy to design a very simple filesystem, with just enough features to be usable for a collection of bootloaders, kernel images, RAM disk images, and file archive images, while still supporting file sizes in excess of 4GB.  It would all be based on existing technology that as far as I know has no patent encumbrances.

The spec says it's supposed to be FAT-32, but in practice it's whatever filesystems the (U)EFI developers want to support. AFAIK, this always includes FAT-32, FAT-16, and FAT-12. Apple includes HFS+ support in their version. It's at least theoretically possible to write drivers for still more and put them on the EFI System Partition, but of course that's not really a useful substitute for FAT-32, since the driver would need to be read from the disk first.

> Not clear, yet, is whether UEFI allows a choice in which file to load.  Either it would have to, or the UEFI code would have to hard code one (hopefully a standard one if this is the case).  If it does have a choice, is it a pretty menu, or something ugly and deeply hidden.

This varies depending on the implementation. The firmware stores information on available images, but the specification says little or nothing about how the user selects the image. I've seen four implementations:


[list]
[*]On an Apple Mac Mini, there's a default boot option that normally goes straight to OS X; however, if you hold down a specific key (I think it's the Option key, but maybe it's Command), you get a set of icons representing the boot options.
[*]On an Intel DG43NB, the user interface in the firmware is nearly useless; you can select between disks, but as far as I can tell the choice of which file is to be loaded from a given disk is made by firmware settings that must be adjusted via tools like Linux's efibootmgr -- and some of those seem to be ignored!
[*]On VirtualBox's UEFI, you can run a boot image using an EFI shell (a command prompt similar to a Linux shell or DOS command prompt). There's also a text-mode set of menus you can use to select the boot loader file or set one as a default. It's pretty klunky and user-unfriendly.
[*]UEFI DUET, which is an implementation that can be run on a BIOS-based computer via a boot floppy or USB flash drive, works much like VirtualBox's UEFI implementation. (I think the VirtualBox version is based on UEFI DUET.)
[/list]


Some new motherboards include UEFI implementations with flashy GUI front-ends. I don't know exactly how they enable OS selection, though. You could peruse the ASUS or ASRock Web sites for manuals for their motherboards for Sandy Bridge CPUs, though. I'm sure there's at least one other brand that's going for the flashy GUI implementation, but I don't recall what it is, offhand. Some others are releasing UEFI implementations that work much more like traditional BIOSes (apparently pretty similar to what my Intel board does).

> Hopefully, for that, the UEFI exports an API to read FAT-32 for the bootloader to use.

It does. The EFI is a lot like a simple OS, in fact. You can write drivers and applications for it.

> Linux once had a bootloader attached in front of it, for self loading on floppies.  Maybe one for UEFI can be made like that, so the merged file, in .efi format, can be placed in the ESP.

I've thought along similar lines. A relatively simple Linux-only boot loader that turns the kernel and initial RAM disk into a (rather large) .efi file, and that accepts kernel arguments in some form that a boot loader like rEFIt could be configured to deliver would probably work better than GRUB 2, which currently barely works on UEFI systems, in my experience.

> This is a newly bought computer.  Will computers be advertising "Includes UEFI" or would that just happen when the manufacturer is ready to do it?

Some already do. Unfortunately, Newegg's own search doesn't pick it up, but you can use Google to search Newegg for UEFI products:

[http://www.google.com/search?q=uefi+site%3Awww.newegg.com](http://www.google.com/search?q=uefi+site%3Awww.newegg.com)

This turns up products with "UEFI" on the main page, and a lot of new boards are so advertised. This search does *not* turn up some products that *do* use UEFI, though, since the manufacturers aren't always making a big deal about it.

My impression is that the products that are advertised as using UEFI are the ones with the flashy GUIs; the ones that look more like traditional BIOSes don't get advertised as being UEFI-based, even when they are. The result is that a lot of end users seem to think that UEFI is all about the flashy GUI, when in fact it's much deeper than that.

> BTW, I've heard that Windows will, intentionally, not be able to boot from a disk with GPT, unless the BIOS is UEFI.  Does that mean UEFI would be exporting a GPT access API that their bootloader would use?

You're right; Windows won't boot from a GPT disk on a BIOS-based computer; you need a UEFI-based computer for that. I don't know the technical details of how the Windows boot loader works, but any EFI application (including an OS boot loader) can use the EFI APIs to access partitions and filesystems. (I've not read most of the specification, though, so I don't know the details of what's in this API. My interest, as the author of GPT fdisk, has been in the GPT data structures.)

---

### Post by srs5694 on 2011-06-01
> **Skaperen said:**
> The first OS I put on the machine is Slackware64 13.37.  That went into partitions 1,10,11,12,13,14.  The 2nd is Slackware 13.37 (the 32 bit version).  It went into partitions 2,20,21,22,23,24.  Ubuntu was supposed to be next, with the plan being 11.04-amd64, 11.04-i386, 10.04.2LTS-amd64, and 10.04.2LTS-i386.  The machine is targeted to be a development box.  Anyway, Slackware works just fine.  It installed with no issue, and it boots and runs with no issue.  So this box (a cheap $300 e-Machines box from Walmart) does not have any inherent issues with GPT.

If Slackware can handle the drive but Ubuntu doesn't, then that supports my hypothesis that the issue is with Ubuntu's udev configuration -- or at least some configuration issue that's specific to Ubuntu.

FWIW, when I install several Linux distributions to a computer, I greatly prefer LVM to partitions. LVM is *much* more flexible when it comes time to adjust the filesystems because of OS upgrades, new OSes being added, etc. It's conceivable that LVM would work around your problem, too -- but it's also possible that the hypothesized limit on devices would apply to logical volumes as well as to partitions.

---

### Post by Skaperen on 2011-06-02
> **srs5694 said:**
> If Slackware can handle the drive but Ubuntu doesn't, then that supports my hypothesis that the issue is with Ubuntu's udev configuration -- or at least some configuration issue that's specific to Ubuntu.Slackware uses udev, too, so it's not udev design specific.  So yeah, that could then point at Ubuntu's configuration of udev.  I am able to Ctrl+Alt+F1 to a text console (text mode in 10.10, frame buffer with a nice crisp font in 11.04) and can access all partitions.  So udev did at least create the device nodes correctly and completely.  So maybe something else in the Ubuntu installer?  Maybe it assumes contiguous partition numbers after number 4 (as would be the case with logical partitions on an MBR based drive)?  I'm just guessing at this point as I have little knowledge of how things get installed from there (aside from knowing that Casper will successfully find the filesystem it looks for even if it's in ISO format on a hard drive, which makes my method of building bootable flash drives workable ... but I'm using a real DVD drive in this case).

> **srs5694 said:**
> FWIW, when I install several Linux distributions to a computer, I greatly prefer LVM to partitions. LVM is *much* more flexible when it comes time to adjust the filesystems because of OS upgrades, new OSes being added, etc. It's conceivable that LVM would work around your problem, too -- but it's also possible that the hypothesized limit on devices would apply to logical volumes as well as to partitions.Drive space is cheap.  I just make the partitions extra large and that will work for a year or so.  I'd be rebuilding from scratch by then.  That's one reason I've never done LVM.

---

### Post by psusi on 2011-06-02
+1 for LVM; it's fantastic.  It is especially nice if you have multiple disks, like a big TB storage disk and an SSD since if you find yourself switching distributions for a while, you can migrate the old one to the slower disk and the one you're running now to the SSD all on the fly while you continue to work.

---

### Post by Skaperen on 2011-06-02
> **psusi said:**
> +1 for LVM; it's fantastic.  It is especially nice if you have multiple disks, like a big TB storage disk and an SSD since if you find yourself switching distributions for a while, you can migrate the old one to the slower disk and the one you're running now to the SSD all on the fly while you continue to work.
Does LVM involve an added layer of disk sector/block location mapping?

---

### Post by srs5694 on 2011-06-02
> **Skaperen said:**
> Does LVM involve an added layer of disk sector/block location mapping?

It depends on what you mean. In LVM, partitions are used as *physical volumes*, which are building blocks for *volume groups*, out of which are carved *logical volumes*, which store filesystems and swap space. It's conceptually similar to creating a big file, using mkfs on that file, and mounting it on a loopback device. Thus, when you want sector x of filesystem A, the kernel will have to go through more redirection to figure it out; however, the disk device itself has unchanged sector mappings.

LVM adds complexity and creates a learning curve to learn all the tools required. (OTOH, Palimpsest and a few other GUI tools can help you get started pretty quickly.) The end result is more flexible and, in some respects, simpler than traditional partitions:


[list]
[*]Logical volumes can be discontiguous, which means you don't need to move partitions to consolidate small chunks of free space to make a new partition that's bigger than any one chunk.
[*]A volume group can span multiple physical volumes, even on separate disks, and its space is allocated as a single pool. Thus, you can create a logical volume (and hence a filesystem) that's bigger than any one disk.
[*]You can create a logical volume that spans multiple disks in an interleaved manner, similar to RAID 0, for speed improvement (at the cost of greater risk in case of a disk failure, the same as with RAID 0).
[*]You can take a *snapshot* of a logical volume, which gives you access to that volume at a single moment in time. This is useful for backups. You can also restore the snapshot to the original volume, which is great if you want to try something risky (like an in-place upgrade to a new OS version); if it doesn't work out, you can restore the snapshot rather quickly.
[/list]


I'm sure there are other features that I'm forgetting or that I don't even know about. I find that LVM helps a lot in managing my multi-distribution installations.

---

### Post by Skaperen on 2011-06-03
That sure sounds like LVM is an added layer of indirection at the drive sector/block level.  How else would it know where the various discontiguous pieces are located?  That would tell me there is a performance penalty involved, though not much where the sectors/blocks that need to be accessed are now cached in RAM.  But the initial reading of not-yet-cached data would be slower in a manner similar to how reading a file is slower than reading a partition in the raw sequentially.  And I've had to set up every system with LVM if that's how the drives are "partitioned".  Can BSD do this, too?

---

### Post by psusi on 2011-06-03
I don't know about bsd.

Partitions themselves are a "layer of indirection".  They have essentially no overhead though because the adjustment to the sector offsets is just a simple add/subtract, which is almost nothing.  LVM adjustments can be just as simple, or they can be more complex.  LVM uses the device mapper driver which allows it to specify a table of how to translate sectors from the logical volume to one or more physical volumes.  If that table only has one linear mapping, then it is no different than a conventional partition.  It can however, contain multiple mappings so that a logical volume can be split between two disks for instance, or in two chunks of one disk, with a gap in the middle ( possibly used by another volume ).  Either way, the overhead is so small it can't be measured.

---

### Post by srs5694 on 2011-06-03
> **Skaperen said:**
>  And I've had to set up every system with LVM if that's how the drives are "partitioned".  Can BSD do this, too?

Psusi has addressed the speed issue. Because the basis of LVM is what it calls "physical volumes," and because these are normally ordinary partitions, it's possible to have some OSes in and some out of the LVM configuration. I've got several multi-boot systems that use LVM for Linux but not for another OS (or two or three).

---

### Post by Skaperen on 2011-06-03
> **psusi said:**
> I don't know about bsd.

Partitions themselves are a "layer of indirection".  They have essentially no overhead though because the adjustment to the sector offsets is just a simple add/subtract, which is almost nothing.  LVM adjustments can be just as simple, or they can be more complex.  LVM uses the device mapper driver which allows it to specify a table of how to translate sectors from the logical volume to one or more physical volumes.  If that table only has one linear mapping, then it is no different than a conventional partition.  It can however, contain multiple mappings so that a logical volume can be split between two disks for instance, or in two chunks of one disk, with a gap in the middle ( possibly used by another volume ).  Either way, the overhead is so small it can't be measured.
What I worry about LVM is that there is extra disk I/O to get the map blocks/pages/sectors to find the real data with.  But maybe if it has a finite set of range extents, it can end up holding those in RAM and the lookup can still be fast (a few CPU instructions to find the right map offset).

---

### Post by psusi on 2011-06-03
> **Skaperen said:**
> What I worry about LVM is that there is extra disk I/O to get the map blocks/pages/sectors to find the real data with.  But maybe if it has a finite set of range extents, it can end up holding those in RAM and the lookup can still be fast (a few CPU instructions to find the right map offset).

It is a very small table that is read at boot time and loaded into the kernel, just like the partition table.  Unlike the partition table though, it can easily be modified while the volumes are in active use.

---

### Post by Skaperen on 2011-06-06
> **psusi said:**
> It is a very small table that is read at boot time and loaded into the kernel, just like the partition table.  Unlike the partition table though, it can easily be modified while the volumes are in active use.
Contrary to popular myth and how Linux has implemented it, partitions can be modified while in active use, too.  I'll need to understand the underlying details about how LVM works to be comfortable using it.  A table of range offsets I can readily understand.  But what data is being moved?  Does it wedge in a temporary block pointer layer to allow the move to function while working?  Or does it block the I/O?

---

### Post by psusi on 2011-06-06
> **Skaperen said:**
> Contrary to popular myth and how Linux has implemented it, partitions can be modified while in active use, too.

You mean in some hypothetical OS other than Linux?  Anything is possible in theory, how about we stick to the practical?

> **Skaperen said:**
> I'll need to understand the underlying details about how LVM works to be comfortable using it.  A table of range offsets I can readily understand.  But what data is being moved?  Does it wedge in a temporary block pointer layer to allow the move to function while working?  Or does it block the I/O?

LVM moves volumes by changing the table to insert a mirror for part of the disk.  Once the kernel syncs up the mirror, it changes that part of the table to point to the new location, and sets up a mirror for the next part, and so on.  I/O is blocked only for as long as it takes to switch the table.

---

### Post by Skaperen on 2011-06-06
> **psusi said:**
> You mean in some hypothetical OS other than Linux?  Anything is possible in theory, how about we stick to the practical?
Or did you mean stick to how it is done in Linux?

> **psusi said:**
> LVM moves volumes by changing the table to insert a mirror for part of the disk.  Once the kernel syncs up the mirror, it changes that part of the table to point to the new location, and sets up a mirror for the next part, and so on.  I/O is blocked only for as long as it takes to switch the table.
That "sync up" part is where interest would be.  I don't want to think of it as "magic under the hood".  Sectors would have to be copied, and if it is also working, that has to be tracked, either by switching usage to the target copies that are done (but not the ones that are not yet done), or by tracking changes in the source to re-copy them.  During the copy done while active, changes for some can be stored in the original source because those are not copied, yet, while changes can be stored in the new target because those have been copied.  In the simplest case, the copy is done linearly so the state can be stored by a number indicating the copy progress.  Power down the machine ... how is it kept from uncorrectable corruption?

---

### Post by psusi on 2011-06-06
The LVM metadata keeps track of the current area that is being mirrored.  If you shut down during that process, then the area currently being mirrored has to be restarted on the next boot and continues from there.

---

### Post by Skaperen on 2011-06-08
> **srs5694 said:**
> My guess is it's the large number of partitions you've got that's triggering a bug. I've done installs of Ubuntu to GPT disks with fewer partitions before, although I don't think I've done an 11.04 installation to GPT using a BIOS-based computer. (I've done 11.04 on a UEFI system and 10.10 using BIOS, though.)

You might try redoing your experiment in which you created an MBR equivalent of part of your drive, but instead leave it as GPT and delete all but the bare minimum number of partitions. If you get it installed, you can then restore your original partitions a few at a time. If it fails after you've restored a certain number, you'll have a hard limit. If you can restore all your partitions and still boot, you'll know the bug is in the installer alone.
I finally got around to doing this test last night.  I put in only the partitions needed for the install (including the common ones for all systems being installed).  They were all at exactly the same sector positions and sizes as the big scheme.   That got past the original problem.  Now there is a new problem regarding manual installed.  For that I started a new thread at:  [http://ubuntuforums.org/showthread.php?t=1777918](http://ubuntuforums.org/showthread.php?t=1777918)

> **srs5694 said:**
> FWIW, I've successfully tested disks with in excess of 100 partitions; however, this was on a Gentoo system. IIRC, there was once a limit of something on the order of 16 partitions per disk built into the kernel, but that limit has been overcome by use of udev. It's possible that Ubuntu's udev configuration doesn't raise this old limit, or only raises it to some level that's lower than whatever Gentoo does.While in the 11.04 LiveCD I was able to access all of the partitions I had.  So I don't think it is udev, per se.  I suspect it is the installer overflowing the number it can handle.  FYI (to whoever maintains that), GPT can even go more than 256.  I also tried the Ubuntu based Linuxmint-11 which had exactly the same hang issue (haven't yet tried it with the above minimal partitions).

---

### Post by srs5694 on 2011-06-08
> **Skaperen said:**
> FYI (to whoever maintains that), GPT can even go more than 256.

Yup. The default is 128 partitions, but the spec places no upper limit on the number of partitions. The data structures do need to be allocated in such a way that they don't overlap with current partitions, though, which means it's not always possible to increase the maximum number of partitions on a disk that's already been partitioned.

FWIW, the last I checked (with version 2.3), libparted had a bug that caused it to flake out on GPT disks with partition tables that supported anything but 128 partitions. GPT fdisk (gdisk) and the Linux kernel both handle such disks fine, as do other OSes I've tested.

---

### Post by Skaperen on 2011-06-08
> **srs5694 said:**
> Yup. The default is 128 partitions, but the spec places no upper limit on the number of partitions. The data structures do need to be allocated in such a way that they don't overlap with current partitions, though, which means it's not always possible to increase the maximum number of partitions on a disk that's already been partitioned.  Bootloaders do seem to put stuff on disk starting at sector 34.  I wonder if they start higher if GPT is set up for more than 128 partitions.

FWIW, the last I checked (with version 2.3), libparted had a bug that caused it to flake out on GPT disks with partition tables that supported anything but 128 partitions. GPT fdisk (gdisk) and the Linux kernel both handle such disks fine, as do other OSes I've tested.
I recall a bug in the past with the Ubuntu installer that hung when the geometry had 256 heads per cylinder.  That is a valid number.  The number isn't literally stored in the MBR, but is calculated.  Some code may have calculated it or stored it with 8 bits since that many bits is used to select the head in older CHS based I/O code.  And I've seen some docs that say 255 is the maximum, but it really can go to 256.  But really, nothing should ever care about CHS anymore.

---

