---
title: "Attempting to dual boot Ubuntu 14.04 with Windows 7"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by neil-andrews89 on 2014-08-16
I've decided I want to dual boot my Windows 7 computer with Ubuntu, the installation has gone smoothly but I am unable to properly use Boot-repair to allow for me to choose between Windows or Ubuntu.
I'm enough of an understanding to make any head way with the pastebin provided; [http://paste.ubuntu.com/8065921/](http://paste.ubuntu.com/8065921/).

Links to information that could help me or any assistance given would be most appreciated.

---

### Post by yancek on 2014-08-16
Your boot repair output shows you have two instances of windows 7 installed on sda3 and sdb2 and also windows 2000 on sdd.  You have a uefi partition with files on sda1 as expected.  What happens if you select the second drive with windows (1TB drive) in the BIOS as first boot priority?  You haven't actually indicated what the problem is or what happens when you try to boot either Ubuntu or windows and that information will be necessary.

---

### Post by oldfred on 2014-08-16
I do not think Linux is seeing the external drive correctly. Probably some vendor unique version with the 4K sectors to work with older systems. Not how most are configured as they use gpt partitioning and 512K sectors. But any changes may erase lots of data, so I would not attempt anything for now on it.

---

### Post by neil-andrews89 on 2014-08-16
Not much happens when I try to boot, it just loads windows immediately.

For hard drives I have a 128 SSD, a 1 TB drive and two external drives a 2 TB for backups and a 500 gig one (it was a random gift).
I've partitioned off 20 gigs from my SSD for Ubuntu, and the rest for Windows. I won't be needing much space for Ubuntu.
My 1 TB drive is used to save my larger files for windows, my games, media and any other programs that I do not want clogging up my SSD.
I don't know why I have a version of Windows 2000/xp on my computer, but I have my suspicions.

I'm contemplating just reformatting my computer and re-installing windows then Ubuntu from scratch. Obviously after backing everything up.
I'd rather do the solution that is best, I don't want to take the easy way out. I know too well what can come of that.

---

### Post by fantab on 2014-08-16
```

=================== parted -l:

Model: ATA M4-CT128M4SSD2 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
1      1049kB  106MB  105MB   fat32        EFI system partition          boot
2      106MB   240MB  134MB                Microsoft reserved partition  msftres
3      240MB   108GB  107GB   ntfs         Basic data partition          msftdata
**4      108GB   128GB  20.4GB  ext4 **                                      ***msftdata***


Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata

```

If ubuntu had installed correctly then you don't see '**msftdata**' flag next to an ext4 partition.
Also I don't see a SWAP partition. I recommend at least a 2-4gb SWAP partition, (put it on your HDD).
Unplug your backup drive. 
Using gparted remove that 'msftdata' flag from ext4 partition and Reinstall Ubuntu.
When you set up your root partition use following parameters:
USE AS = Ext4
Mountpoint = /
Format = yes

20Gb on SSD for Ubuntu system files is an excellent idea, however, keeping your personal data on a separate '/home' partition will avoid any 'space crunch' in future.
You can make about 50gb /home partition on your internal HDD.

You don't have different Windows. You don't seem to have installed ubuntu properly.

---

### Post by neil-andrews89 on 2014-08-17
Okay I have done what you have suggested save for the home partition on the HDD.
I hope that was a non-critical step to resolving this, if it was, I'm sorry and I will try again.

Though as you've probably guessed it did not work, here is the new pastebin: [http://paste.ubuntu.com/8068943/](http://paste.ubuntu.com/8068943/).
I'm going to continue researching on this, and if I find a solution will post as much as I can for others in the future.

---

### Post by oldfred on 2014-08-17
Usually Windows 7 UEFI system work pretty good as they do not have secure boot or fast boot issues.

What hardware is this, vendor, model, video card/chip?

Can you see ubuntu entry if you use one time boot key, often f12 but varies by vendor.

---

### Post by fantab on 2014-08-17
Have you changed the setting in UEFI menu to boot 'Ubuntu' first?

> Can you see ubuntu entry if you use one time boot key, often f12 but varies by vendor.

Share more details about your machine... tell us what hardware its got.

---

### Post by neil-andrews89 on 2014-08-17
I did build this computer, this is the first one I've ever built so I'm quite new to all of this.
I'd gladly share my computer specs, I don't know what you need entirely so here is the entire thing:

*Please note I am not advertising NCIX, it's just where I got the parts so it has the full details*

**Motherboard:** MSI Big Bang Xpower X58 ATX LGA1366 DDR3 6PCI-E16 1PCI-E1 SLI CrossFireX SATA3 USB3.0 Motherboard. [Here is the parts site entry]("http://secure1.ncix.com/products/index.php?sku=66111"). 
**CPU**: Intel Core i7 960 Quad Core Processor LGA1366 3.2GHZ Bloomfield 8MB LGA1366 4.8GT/S Retail Box. [Here is the parts site entry]("http://secure1.ncix.com/products/index.php?sku=66111"). 
**Ram**: Patriot Viper Xtreme 8GB 2X4GB DDR3 1866MHZ PC3-15000 9-10-9-27 1.65V XMP Ready Desktop Memory Kit. [Here is the parts site entry]("http://pc.ncix.com/products/productdetail2.cfm?sku=62704&promoid=1377"). 
**Graphics Card**: EVGA GeForce GTX 560 Ti 448 Cores FTW 797MHZ 1280MB DVI Mini-HDMI Display Port PCI-E Video Card. [Here is the parts site entry]("http://forums.ncix.com/products/?sku=65860&vpn=012-P3-2066-KR&manufacture=eVGA&promoid=1067"). 
**Power Supply**: OCZ Z Series 1000W Modular 80PLUS Gold High Performance Power Supply compatible with Intel Haswell Core i3/i5/i7 and AMD Phenom. [Couldn't find on NCIX anymore here's Newegg]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16817341028").
**SSD**: Crucial M4 CT128M4SSD2 2.5IN 128GB SATA III MLC Internal Solid State Drive (SSD). [Here is the site entry]("http://www.ncix.com/detail/crucial-m4-ct128m4ssd2-2-5in-128gb-b7-60445.htm"). 
**Other Hard-drive**: Seagate Barracuda ST1000DM003 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive Bare Drive. [Coulnd't find on NCIX anymore here's Newegg]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16822148840").

I will try your suggestions now, and I hope the format I've given you for my specs are to your liking.

MY UEFI bootable is controlled by 2.2 TB Infinity, I have a feeling that has to do with my issue.
When it pops up and I'm given bootable options, they are my 128 SSD, CD/DVD, or USB (which I have Ubuntu install on).
I don't have an option between Windows or Ubuntu.

---

### Post by oldfred on 2014-08-17
With the nVidia card you are going to need nomodeset. I have to use it to boot live installer or first boot by editing grub. Or until I install proprietary driver from repository using system settings or command line.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Some UEFI/BIOS show hardware boot choices separate from software boot choices, maybe different page or a sub-menu that is not obvious. And settings to turn on or off UEFI or BIOS may also be on another UEFI page.

---

### Post by neil-andrews89 on 2014-08-17
Alright I have tried your suggestion of NOMODESET but unfortunately it did not solve the issue.
My own bit of research suggested that you did not need to replace quiet and splash, so I tried both methods.
[http://paste.ubuntu.com/8075107/](http://paste.ubuntu.com/8075107/)
In this one I had the option I had replaced both quiet and splash.
[http://paste.ubuntu.com/8075167/](http://paste.ubuntu.com/8075167/)
I ran boot-repair in both setups twice, once doing only recommended. The second setting it so that it should include NOMODESET in the GRUB repair.
Now that I look into the paste, it appears that did not happen.

As for going further into the boot, I did find something. I found the windows powered boot option, where I only had the option of loading Windows (surprise).
I did not find an option to load ubuntu.

I don't think boot-repair is doing anything with the Grub and as such it's only going to stay as Windows.

---

### Post by oldfred on 2014-08-17
Boot-Repair does not update UEFI settings, but some of the Linux scripts to install grub may try to make Ubuntu as the first entry in UEFI's NVRAM.

But your UEFI/BIOS should show both Windows and Ubuntu entries.

This is an extract in BootInfo showing UEFI entries. I do not even see the Windows entry:

 BootOrder: 0003,0000,0001,0002
Boot0000* HDD    : M4-CT128M4SSD2 (128.0 GB)
Boot0001* CD/DVD : TSSTcorp CDDVDW SH-222AL
Boot0002* USB
Boot0003* ubuntu,BootCurrent: 0002

From live USB post this when booted in UEFI mode:

      
 # from liveDVD or flash and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by neil-andrews89 on 2014-08-17
Here is what I get back:
[FONT=arial]ubuntu@ubuntu:~$ sudo efibootmgr -v[/FONT]
[FONT=arial]BootCurrent: 0002[/FONT]
[FONT=arial]Timeout: 5 seconds[/FONT]
[FONT=arial]BootOrder: 0000,0001,0002[/FONT]
[FONT=arial]Boot0000* HDD    : M4-CT128M4SSD2 (128.0 GB)    ACPI(a0841d0,0)PCI(2,0)PCI(0,[/FONT][FONT=arial]0)ATAPI(0,0,0)[/FONT]
[FONT=arial]Boot0001* CD/DVD : TSSTcorp CDDVDW SH-222AL    ACPI(a0841d0,0)PCI(1f,2)ATAPI([/FONT][FONT=arial]0,1,0)[/FONT]
[FONT=arial]Boot0002* USB    ACPI(a0841d0,0)PCI(1d,7)USB(5,[/FONT][FONT=arial]0)

I've tried deleting boot0000 and running boot-repair to see if that would work, but nothing.

I'm pondering the idea of slash and burning, just wipe the drives re-install windows properly.
Then seeing if things change. I backed up well before starting this.[/FONT]

---

### Post by oldfred on 2014-08-18
Does the one time boot key, often f12 show boot options?

---

### Post by neil-andrews89 on 2014-08-18
I've attempted from a previous post to show boot options, however 2.2TB Infinity controls the boot options.
It loads after the motherboard load screen where I can get into Bios, I hit any key to load the hardware boot.
Choosing between my SSD, CD/DVD and USB. After that, I press the F12 key when I choose SSD and it comes to another boot screen run by Windows that only shows windows.

I'll see if I'm pressing the wrong key, and double check.

---

### Post by oldfred on 2014-08-18
I had not heard of this, but it is some proprietary thing that may not have support in Linux?

[http://www.tomshardware.com/forum/id-1786675/2tb-infinity.html](http://www.tomshardware.com/forum/id-1786675/2tb-infinity.html)

---

### Post by neil-andrews89 on 2014-09-07
Sorry for the long delay in replying, I don't want to leave this thread with out a conclusion.

I have successfully dual booted windows and Ubuntu on my computer. However, it did require me to do a complete reformat of my system. All of  your advice aided in the proper installation, and I do thank you all for your time and effort. The hurdle that I could not over come was the 2.2 TB Infinity start up. I researched into the issue, and all I could find were others that were also stumped by it. I may have missed how to do it, but I do believe the clean installation was actually for the best. Sometimes you just need to do it that way.

Also a small piece of advice for anyone that is attempting something similar to my setup. Unplug your second drive while doing the installation of the OS's, that way they both will be on your SSD.

Once again thank you all, I've learned a lot.

---

