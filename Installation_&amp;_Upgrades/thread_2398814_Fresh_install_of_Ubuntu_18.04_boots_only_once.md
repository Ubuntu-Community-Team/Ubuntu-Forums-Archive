---
title: "Fresh install of Ubuntu 18.04 boots only once"
date: 2018-08-17
forum: Installation &amp; Upgrades
---

### Post by elkanguro2 on 2018-08-17
Hi Guys!
After 6 years of using Ubuntu 12.10 I decided to install a new SSD drive and install new Ubuntu 18.04. Live USB works great, installing was fast, and first boot was successful. But after shutting down the machine it does not boot any more. I installed Ubuntu twice with the same effect. First time I have made partition by my own: efi (forced by installer), root, home and swap. Second time I have chosen default installation with disk encryption. The result was the same. When booting it stops with only black screen with underscore in top left corner and CPU working. How can I check what's wrong with the installation?
Regards,
Kamil

---

### Post by oldfred on 2018-08-17
What brand/model system?
Have you updated UEFI from Vendor?
What video card/chip?

---

### Post by elkanguro2 on 2018-08-17
Lenovo G580 with Intel HD3000. I did nothing with UEFI.

---

### Post by oldfred on 2018-08-17
That would be an UEFI system, unless you un-installed Windows.

I would first update UEFI from Lenovo for your system.

If only installing Ubuntu, you may need a work around. 
Some systems violate UEFI spec that says NOT to use description as part of UEFI boot. And of course only valid description is "Windows Boot Manager".  If only booting Ubuntu one work around is to make description Windows but actual boot file is still Ubuntu's shimx64.efi for UEFI boot.

Issues often common across multiple models by brand. Not sure if these are similar or not.
       Lenovo rename files
[URL="http://ubuntuforums.org/showthread.php?t=2302170"]http://ubuntuforums.org/showthread.php?t=2302170
      [/URL]
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 
    [URL="http://ubuntuforums.org/showthread.php?t=2302170"]
[/URL]        
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by elkanguro2 on 2018-08-17
I have never installed Windows on that machine. All above looks quite complicated and I am not sure if I understood correctly.

I used boot-info bu didn't get the url, only report in txt file. Link here: [https://www.dropbox.com/s/7xs879e8r5tkqgv/Boot-Info_20180817_2201.txt?dl=0](https://www.dropbox.com/s/7xs879e8r5tkqgv/Boot-Info_20180817_2201.txt?dl=0)

Is it helpful?

---

### Post by oldfred on 2018-08-17
You have what looks like a standard UEFI install, but using LVM with encryption.
I do not know LVM nor full drive encryption. 

LVM is an advanced volume management system used a lot by servers, and if you must have full drive encryption. Not really for beginners as you have to use LVM tools and do extra mounts to see the LVM when you need repairs.

It looks like it should boot. Are you letting it automatically try to boot or using the UEFI boot menu.
You will not get grub menu with only one system installed unless you press escape key right after UEFI/BIOS screen, but before grub  loads. may have to press more than once.

Your system may need boot parameters and you would have to get grub menu to add them.
Or you may need a work around.

Have you tried booting the internal hard drive entry in UEFI boot menu?
Or add a new Windows entry that really boots Ubuntu. And see if that boots.
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by elkanguro2 on 2018-08-17
Just made it and will try to boot:
> ubuntu@ubuntu:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
BootCurrent: 0003
BootOrder: 0006,0003,0005,0001,0002,0004,0000
Boot0000* Network Boot: Atheros Boot Agent
Boot0001* Internal HDD: ADATA SP920SS                   
Boot0002* SATA ODD    : PLDS DVD-RW DS8A8SH             
Boot0003* EFI USB Device
Boot0004* USB HDD     : SCSI    DISK            
Boot0005* Ubuntu
Boot0006* Windows Boot Manager

---

### Post by elkanguro2 on 2018-08-17
After above a new line in Boot Manager has been added: Windows Boot Manager - but the result is the same while trying booting it.

When pressing ESC Grub does not appear.

I pressed F12 and in Boot Manager I choosed Internal HDD, and then I got below message:

> Intel UNDI, PXE-2.0 (build 083)
Copyright (C) 1997-2000 Intel Corporation
For Atheros PCIE Ethernet Controller v2.1.1.1(12/13/11)
Check cable connection!
PXE-M0F: Exiting Intel PXE ROM.
No bootable device -- insert boot disk and press any key 

Regarding the encryption - I don't need it at all. After the boot failed when I manually created partitions I decided to install system once again with default option and I ticked encryption then. But without it the result was the same.

---

### Post by oldfred on 2018-08-17
If you re-installed, you updated UUID & GUID, so old entries to boot would be invalid and only the new entry.
And if then it only boots Windows desription, you have to reinstall that.

UEFI has a boot order, shown by the efibootmgr -v, but some systems will change boot order internally and only changing boot order inside UEFI works.

UEFI also boots things in order, you must have network boot as next if boot fails. PXE is a network boot. I normally turn that off in UEFI, so it does not even try that.

---

### Post by elkanguro2 on 2018-08-17
What should I reinstall now? I'm a bit confused right now.

---

### Post by oldfred on 2018-08-17
Post these:
sudo efibootmgr -v
       lsblk -f -o +PARTUUID /dev/sda 
    
The partuuid is the same as the GUID. And efibootmgr will show guid for each UEFI boot. Want to see if GUIDs match. And any that are not correct we then can also remove.

---

### Post by elkanguro2 on 2018-08-20
```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0004
BootOrder: 0003,0004,0001,0002,0000
Boot0000* USB HDD     : SCSI    DISK                BBS(HD,&#65533;,0x500).......................................................................
Boot0001* Internal HDD: ADATA SP920SS                       BBS(HD,m&#65533;,0x500)................-...........A..........................................
Boot0002* SATA ODD    : PLDS DVD-RW DS8A8SH                 BBS(CDROM,m&#65533;,0x500)................-.!.......!.A.!....#...................................
Boot0003* Ubuntu    HD(1,GPT,5c01c916-12ba-4e49-b5c0-15cd822f3c5b,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0004* EFI USB Device    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(3,0)/HD(1,MBR,0x419e5,0x40,0x784420)RC

```

```
ubuntu@ubuntu:~$ lsblk -f -o +PARTUUID /dev/sda
NAME FSTYPE LABEL UUID                                 MOUNTPOINT PARTUUID
sda                                                               
&#9500;&#9472;sda1
&#9474;    vfat         657A-3783                                       5c01c916-12ba-4e49-b5c0-15cd822f3c5b
&#9500;&#9472;sda2
&#9474;    ext4         b002af58-4433-4718-b87c-506dfa784d7c            8a3871b2-df0b-4fe9-a989-bbfd09980a74
&#9492;&#9472;sda3
     crypto       a659b607-6630-4c6f-839e-532f2afb948b            097144fc-687a-432b-982f-a12f2807d9fb

```

---

### Post by oldfred on 2018-08-20
GUID's match so that is ok.

But not now seeing the Windows boot entry, I thought we added.
Try adding it again.

I think you really need to update UEFI from Lenovo.

Does selecting the ubuntu entry work if you manually select it from UEFI boot menu each time?

---

### Post by elkanguro2 on 2018-08-20
It's really strange, I don't understand it at all.

I have added Windows entry again, rebooted computer, chose Windows in Boot Manager and... I'm logged in :)

```

kangur@Lenovo-G580:~$ sudo efibootmgr -v
[sudo] password for kangur: 
BootCurrent: 0005
BootOrder: 0005,0003,0004,0001,0002,0000
Boot0000* USB HDD     : SCSI    DISK                BBS(HD,&#65533;,0x500).......................................................................
Boot0001* Internal HDD: ADATA SP920SS                       BBS(HD,m&#65533;,0x500)................-...........A..........................................
Boot0002* SATA ODD    : PLDS DVD-RW DS8A8SH                 BBS(CDROM,m&#65533;,0x500)................-.!.......!.A.!....#...................................
Boot0003* Ubuntu    HD(1,GPT,5c01c916-12ba-4e49-b5c0-15cd822f3c5b,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0004* EFI USB Device    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(3,0)/HD(1,MBR,0x419e5,0x40,0x784420)RC
Boot0005* Windows Boot Manager    HD(1,GPT,5c01c916-12ba-4e49-b5c0-15cd822f3c5b,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)

```

Now I'm afraid to shut down the system...

---

### Post by oldfred on 2018-08-20
I do not know if Lenovo or some other brand, but some have posted that using efibootmgr to change boot order does not stick, but going directly into UEFI and changing order there does work. 

So if issues I might try looking at boot order in UEFI boot menu.

---

### Post by elkanguro2 on 2018-08-20
It happened again. No boot no matter if I choose Windows, Ubuntu or Internal HDD in Boot Manager. The only difference is that when choosing Internal HDD additional information are being displayed (different than before):
```

Missing parameter in configuration file. Keyword: path
gfxboot.c32: not a COM32E image
boot: 

```

In BIOS menu, Boot Tab, It looks like this:
```

UEFI Boot   [Enabled]

EFI
Windows Boot Manager
Ubuntu
EFI USB Device

Boot Device Priority
Internal HDD: ADATA SP920SS
SATA ODD: PLDS DVD-RW DS8A8SH
USB HDD: SCSI DISK

```

I don't understand it. Do you think updating UEFI/BIOS can help? Can I do it with USB bootable FreeDOS? Should I download all updates? [https://pcsupport.lenovo.com/pl/en/products/laptops-and-netbooks/lenovo-g-series-laptops/lenovo-g580-notebook/downloads](https://pcsupport.lenovo.com/pl/en/products/laptops-and-netbooks/lenovo-g-series-laptops/lenovo-g580-notebook/downloads) Is it risky?

---

### Post by oldfred on 2018-08-20
It looks like they only offer the .exe version.
You need Windows or some flash drive that can extract the .exe, Linux does not use .exe.

Generally it is safe to update UEFI/BIOS. But if you interrupt update then that can cause major issues.
Make sure system has power, some with laptops do not check if plugged in and have low battery. And do not do in middle of thunderstorm where you might lose power.

All my systems have latest updates of UEFI and I never have had an issue.

---

### Post by elkanguro2 on 2018-08-23
I wanted to update BIOS using FreeDOS bootable USB but it told me that the files can not be executed in DOS mode.

Any other ideas? Maybe I can install a GRBU manually? Maybe in Legacy BIOS mode? Why Ubuntu 12.10 worked fine all the time? Where is the problem? Is it a distro/kernel/grub problem?

---

### Post by oldfred on 2018-08-23
IF an older system, you can use legacy.
You do not even have to totally reinstall.
But UEFI uses newer gpt partitioning and to boot in BIOS boot mode with gpt, you need a tiny 1 or 2MB unformatted partition with the bios_grub flag (must be in first 2GB of a drive). Use gparted & shrink some partition by several MB and create new bios_grub.
Then use Boot-Repair's advanced options to un-install  grub-efi-amd and install grub-pc(BIOS version of grub). Install to drive, not to a partition.
Then make sure UEFI is set for BIOS/CSM/Legacy or whatever your UEFI calls it.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by elkanguro2 on 2018-08-24
You wrote an older system in the first system. I'm still thinking about Ubuntu 18.04.

Before I start the operation I want to ask about Boot-Repair. When I run it in Advance Option most options were not active? How to activate them?

---

### Post by oldfred on 2018-08-24
Are you using Boot-Repair in BIOS or UEFI boot mode.
If you want to convert to BIOS, you have to use gparted first to create bios_grub partition.

Many options may not apply to your system, so they would not be shown?

---

### Post by elkanguro2 on 2018-09-02
Hi, I decided to turn off UEFI and then install Ubuntu once again. Now it works fine. Thanks for your help **oldfred**.

---

