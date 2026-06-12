---
title: "Does my laptop have BIOS or EFI?"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by jasonwyz98 on 2012-05-13
I have a Sony VAIO S Series Laptop ( Model: VPCSE190X )

[http://store.sony.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644768015#/s15specificationTabContent](http://store.sony.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644768015#/s15specificationTabContent)

Is there a command or method I could use to find out if my laptop has BIOS or EFI?

---

### Post by Enigmapond on 2012-05-13
No command that I know but if you press, (I think it's F2 on Sony), at the boot you will get into the BIOS....you have a BIOS...BTW. :)

---

### Post by jasonwyz98 on 2012-05-13
> **Enigmapond said:**
> No command that I know but if you press, (I think it's F2 on Sony), at the boot you will get into the BIOS....you have a BIOS...BTW. :)
Thanks for the quick reply, but if that's the case, how to configure stuff in an EFI based system ( without the BIOS menu items )?

---

### Post by darkod on 2012-05-13
Systems with EFI boot have BIOS also. :) Or something similar to it anyway.

You can boot the machine with the ubuntu cd in live mode, and check the partitions with:
sudo fdisk -l

If there is a EFI System Partition, 99% you are using EFI boot. Otherwise, it should be BIOS boot.

I guess you could check that way.

---

### Post by jasonwyz98 on 2012-05-13
> **darkod said:**
> Systems with EFI boot have BIOS also. :) Or something similar to it anyway.

You can boot the machine with the ubuntu cd in live mode, and check the partitions with:
sudo fdisk -l

If there is a EFI System Partition, 99% you are using EFI boot. Otherwise, it should be BIOS boot.

I guess you could check that way.
The problem is that I have just replaced the system hard disk with an Intel 510 SSD, so there's nothing on it.

How should I proceed? Thanks

---

### Post by darkod on 2012-05-13
Well, in that case you can enter the BIOS and look around. Is there something like UEFI boot options? Can you enable/disable it as a setting?

And why are you asking, would you prefer EFI or BIOS boot?

If you would prefer BIOS boot, lets assume it's using bios boot, so you simply start installing and see if it works.

---

### Post by jasonwyz98 on 2012-05-13
> **darkod said:**
> Well, in that case you can enter the BIOS and look around. Is there something like UEFI boot options? Can you enable/disable it as a setting?

And why are you asking, would you prefer EFI or BIOS boot?

If you would prefer BIOS boot, lets assume it's using bios boot, so you simply start installing and see if it works.
Here's what I'm trying to do: I want to create GPT instead of MBR partitions for a fresh installation of Ubuntu 12.04 64bit on an Intel 510 SSD.

So if I have EFI then I don't need to create the bios_grub partition, if not then I believe it required to have a bios_grub partition in order for GPT to work.

And I just want to know how to check.

Thanks

---

### Post by oldfred on 2012-05-14
I plan on a new system in the near future, so on my new SSD I just put both the efi & bios_grub partitions. I use the bios_grub with BIOS now and if I move to a new UEFI system, I will have the efi partition. The efi partition has to be first. 

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

I also put two / (root) partitions on my 60GB SSD so I can alternative new installs. 

My layout:
```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229567   27.8 GiB    0700  Quantal
fred@fred-Precise:~$ 


```

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by YannBuntu on 2012-05-14
Hello
Please indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"), it will tell if you boot in EFI mode or not.

---

### Post by darkod on 2012-05-14
Also, what I have seen on google says that if the bios has mouse support, if there is the pointer and you can move it with the mouse, it most cases it would mean bios with UEFI support.

---

### Post by jasonwyz98 on 2012-05-14
> **oldfred said:**
> I plan on a new system in the near future, so on my new SSD I just put both the efi & bios_grub partitions. I use the bios_grub with BIOS now and if I move to a new UEFI system, I will have the efi partition. The efi partition has to be first. 

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

I also put two / (root) partitions on my 60GB SSD so I can alternative new installs. 

My layout:
```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229567   27.8 GiB    0700  Quantal
fred@fred-Precise:~$ 


```

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Thanks for the detailed response, very helpful :P

So here's what I've found out from reading this forum and other sites:

1. To find out if UEFI is being used:
sudo dmesg | grep EFI

If you see a bunch of lines, then EFI is being used, otherwise if you see ( 1 or 2 lines ) BIOS is probably being used. Also read it somewhere if there's a menu option "UEFI/EFI" in the BIOS menu, then you have UEFI, I couldn't find any so can't be sure.

Read it on another site some system have UEFI with a BIOS compatibility layer and the system may default to use BIOS.

Anyways, I deleted all the partitions on the HDD that came with the laptop ( Sony Vaio VPCSE190X ) and replaced it with an Intel 510 SSD 120GB, so even if the original HDD had the UEFI system partition, it's gone now.

I'll just use BIOS for now.

I'm gonna use GParted to create a GPT partition table with the following partitions:

1 => 1 MiB bios_grub
2 => 200 MiB /boot
3 => 20 GB /
4 => XXX GB /home
5 => 2 GB Swap ( probably not going to need, since I have 8GB ram, but just in case )

Let me know what you guys think.

---

### Post by oldfred on 2012-05-14
I do not think you need the separate /boot.

If you only have the SSD then that is fine. I prefer to have system on SSD and data on rotating drive where there is more space and speed is less important.

Herman now has swap file, not even a swap partition.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

---

