---
title: "Won't boot from hard drive"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by ericks on 2013-02-15
This is on an ASUS N56VZ (-RB71). I can boot from a live CD (tried Ubuntu 32-bit, Ubuntu 64-bit, Mint 64-bit, Fedora 64-bit, all work) and edit the hard drive with tools like gparted. I was able to install Ubuntu in the past, but since trying to install Mint in place of Ubuntu I cannot boot.

When I had grub installed in the past, booting from a Windows install disc would not allow me to do system repair (to fix the computer so that it would boot only to Windows), saying I had the "wrong" version of Windows. I fixed this by deleting the MBR and trying again. This only worked the first time I tried it--now it says I have the "wrong" version of Windows again.

My BIOS only provides the option to boot from CD/DVD and USB. The "add boot option" item that used to be in the BIOS is no longer there. I have tried flashing the BIOS with the latest version (216) of the BIOS found on ASUS's [support page for my laptop]("http://www.asus.com/Notebooks_Ultrabooks/N56VZ/#support_Download_30") to no avail.

I also tried taking out my laptop's battery for an hour or so as I read somewhere that this might have an effect on the issue. It didn't.

I have tried booting with UEFI on and off (according to BIOS settings) with no differences.

I have not tried formatting the hard drive entirely (as I'd like to preserve my files--I suppose I could move them to an external hard drive), but judging from the other information I've gathered I'm not sure this would have an effect. If no other options are presented I will try it.

Any advice on booting my laptop would be greatly appreciated.

**TL;DR: I can boot only from peripheral drives (USB, CD/DVD) [screenshot attached] and reinstalling Linux distros has no effect on booting. How do I fix my boot?**

---

### Post by oldfred on 2013-02-15
Post this to get some idea of your system.

       sudo parted /dev/sda unit s print

---

### Post by ericks on 2013-02-15
> **oldfred said:**
> Post this to get some idea of your system.

       sudo parted /dev/sda unit s print

Thanks for your response. Here is the output:
```
Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size        File system  Name                  Flags
 3      673792s      527793703s   527119912s  ntfs         Basic data partition
 5      1412718592s  1465147391s  52428800s   ntfs         Basic data partition  hidden, diag

```

---

### Post by oldfred on 2013-02-15
You only are showing partitions 3 & 5 in a gpt partitioned drive.

Windows only boots from gpt drives with UEFI. Ubuntu will boot from gpt with either UEFI or BIOS. Both Windows & Ubuntu need an efi partition usually first partition for booting with UEFI. If not using Windows you can add a bios_grub partition for Ubuntu to boot with gpt & BIOS.

Did you delete a bunch of partition that Windows was using?

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
Are the two remaining partitions just data or parts of installs?

---

