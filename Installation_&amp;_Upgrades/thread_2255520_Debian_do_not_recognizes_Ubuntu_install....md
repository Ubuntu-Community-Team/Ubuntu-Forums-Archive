---
title: "Debian do not recognizes Ubuntu install..."
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by fel3 on 2014-12-05
Hi there!

I have Debian,Arch and brand new install of Buntus on **_GPT_**  table and grub managed by Debian on 64 bit...

I'm installed Ubuntu with GRUB  on sda5(buntus partition) instead sda ... is that correct ? debian ```
update-grub
``` and ```
os-prober
``` IS NOT recognizin the Buntus new install...

or...

how to skip grub install on UBUNTU INSTALLATION ???

tia!

Do I[COLOR=#000000][FONT=verdana] had to mount Buntu partition before updating grub ???[/FONT][/COLOR]

---

### Post by yancek on 2014-12-05
I don't use Debian but their wiki site at the link below seems to indicate you need the command:   update-grub2

[https://wiki.debian.org/Grub](https://wiki.debian.org/Grub)

---

### Post by grahammechanical on 2014-12-05
If Ubuntu was installed after Debian then it is Ubuntu that is in change of the Grub boot menu. And that maybe why any changes to grub configuration files in Debian are not having an effect. Can you load into Debian? If so, then you need to do more than run

```
sudo update-grub
```

or also need to run

```
sudo grub-install /dev/sda
```

Assuming that you only have one hard disk with the 3 Linux distributions on the same hard disk.

In Ubuntu update-grub and update-grub2 are scripts that do the same thing. They run grub-mkconfig. It is that utility that creates the main Grub configuration file and not os-prober.

Regards.

---

### Post by yancek on 2014-12-05
> If Ubuntu was installed after Debian then it is Ubuntu that is in change of the Grub boot menu

If he installed Grub to the mbr which he specifically stated he did not but installed to the Ubuntu partition.

> I'm installed Ubuntu with GRUB  on sda5(buntus partition) instead sda

---

### Post by fel3 on 2014-12-06
horrrayyy...

I tried to do a new install and this time I get this: 

```
Unable to install GRUB in /dev/sda



Executing 'grub-install /dev/sda' FAILED



This is a fatal error
```

I like to install on **_[COLOR=#ff0000]Btrfs[/COLOR]_**   perhaps that's the inconvenient?

what's wrong? what I'm doin wrong??

WHERE do I need to place the BOOT LOADER ??? in sda, sda1,sda2,sda3,sda4...

tia!

some way to skip bootloader on install?

---

### Post by nerdtron on 2014-12-07
Boot loader needs to be installed on the drive itself /dev/sda. and I don't think you can skip it.

---

### Post by oldfred on 2014-12-07
If you have gpt and are booting with BIOS, you must have a bios_grub partition for grub to correctly install to the gpt's protective MBR. Normally the bios_grub partition is 1 or 2MB. But with BIOS we have seen where btrfs makes core.img extremely large for some reason, so perhaps your bios_grub partition needs to be larger?

Or are you booting with UEFI?

You normally do not install grub to a partition. And grub2 does not like to install to partitions as it does not fit and has to convert to blocklists or hard coded addresses. Any change that moves a file on drive then requires a reinstall of grub.

---

### Post by fel3 on 2014-12-07
> **oldfred said:**
> If you have gpt and are booting with BIOS, you must have a bios_grub partition for grub to correctly install to the gpt's protective MBR. Normally the bios_grub partition is 1 or 2MB. But with BIOS we have seen where btrfs makes core.img extremely large for some reason, so perhaps your bios_grub partition needs to be larger?

Or are you booting with UEFI?

You normally do not install grub to a partition. And grub2 does not like to install to partitions as it does not fit and has to convert to blocklists or hard coded addresses. Any change that moves a file on drive then requires a reinstall of grub.

THX for reply dude!

yep I'm bootin with** UEFI **! and let the Bootloader manage to Debian:

```
fdisk -l

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 


Device        Start       End  Sectors  Size Type
/dev/sda1      2048     43007    40960   20M Microsoft basic data
/dev/sda2     43008    555007   512000  250M Microsoft basic data
/dev/sda3    555008  22059007 21504000 10.3G EFI System
/dev/sda4  22059008  63019007 40960000 19.5G Microsoft basic data
/dev/sda5  63019008 115447807 52428800   25G Linux filesystem



```

sda1 >>> **[COLOR=#ff0000]20 [/COLOR]**M (I dunno)

sda2 >>> **[COLOR=#0000cd]250 [/COLOR]**M (idem)

sda3 >>> **[COLOR=#006400]10 [/COLOR]**G  ( DEBIAN )

sda4 >>> **20 **G (arch)

sda5 >>> 25 G  ([COLOR=#212121][FONT=inherit]supposedly Ubuntu[SIZE=2])

tia![/SIZE][/FONT][/COLOR]

> **nerdtron said:**
>  /dev/sda

```
[COLOR=#000000][FONT=Ubuntu Mono]Unable to install GRUB in /dev/sda[/FONT][/COLOR]


Executing 'grub-install /dev/sda' FAILED


 [COLOR=#000000][FONT=Ubuntu Mono]This is a fatal error[/FONT][/COLOR]
```

```
#  gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.10


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier 
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 509696621 sectors (243.0 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048           43007   20.0 MiB    0700  
   2           43008          555007   250.0 MiB   0700  
   3          555008        22059007   10.3 GiB    EF00  sda3
   4        22059008        63019007   19.5 GiB    0700  
   5        63019008       115447807   25.0 GiB    8300  



```

:emoHELP:

---

### Post by oldfred on 2014-12-07
Did you boot Ubuntu in BIOS mode?
How you boot installer is how it installs and in BIOS mode it has to have the bios_grub partition.
But if other installs are UEFI, much better to also have Ubuntu in UEFI boot mode also.

The two boot modes UEFI and BIOS are not compatible and you can only switch from UEFI/BIOS menu and may have to turn on/off UEFI or CSM settings to boot in correct mode. Some auto switch and you can use f12 or one time boot key. But grub will only let you boot systems installed in the same mode.

Best to see details.
Post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See link below for more info on UEFI.

---

### Post by fel3 on 2014-12-07
> **oldfred said:**
> Did you boot Ubuntu in BIOS mode?
How you boot installer is how it installs and in BIOS mode it has to have the bios_grub partition.
But if other installs are UEFI, much better to also have Ubuntu in UEFI boot mode also.

The two boot modes UEFI and BIOS are not compatible and you can only switch from UEFI/BIOS menu and may have to turn on/off UEFI or CSM settings to boot in correct mode. Some auto switch and you can use f12 or one time boot key. But grub will only let you boot systems installed in the same mode.

Best to see details.
Post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See link below for more info on UEFI.[http://ubuntuforums.org/showthread.php?t=2255520&page=2&p=13182663#post13182663](http://ubuntuforums.org/showthread.php?t=2255520&page=2&p=13182663#post13182663)

WHY Debian recognizes Arch with just **update-grub **???

How to do that?

> [COLOR=#ff0000][/COLOR][COLOR=#000000]*But if other installs are UEFI, much better to also have Ubuntu in UEFI boot mode also*[/COLOR]

---

### Post by oldfred on 2014-12-07
> Did you boot Ubuntu in BIOS mode?
How you boot installer is how it installs and in BIOS mode it has to have the bios_grub partition.

UEFI systems give you two ways to boot the installer. Usually one clearly says UEFI and the other just the name/label of flash drive. Like UEFI - Kingston or Kingston.

Best to see details, post link from Boot-Repairs summary report.

This is first link in all the links to more info in my signature.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by fel3 on 2014-12-08
> **fel3 said:**
> ```
[COLOR=#000000][FONT=Ubuntu Mono]Unable to install GRUB in /dev/sda[/FONT][/COLOR]


Executing 'grub-install /dev/sda' FAILED


 [COLOR=#000000][FONT=Ubuntu Mono]This is a fatal error[/FONT][/COLOR]
```

? ? ? ? ? ?

no help?

---

### Post by QIII on 2014-12-08
You have been receiving help.  Have you visited and reviewed the link in oldfred's signature?

---

