---
title: "Ubuntu 22.04 installation on new laptop"
date: 2022-06-04
forum: Installation &amp; Upgrades
---

### Post by Mylorharbour on 2022-06-04
Hi Guys,
I've been using Ubuntu since Gutsy Gibbon but always on older Windows PCs using dual boot. Just trying to install Ubuntu on a new laptop bought with no OS installed. I'm able to boot from my USB stick and get as far as Installation Type where I chose 'Something else' as I wanted to partition the 1TB SSD drive. The install window says 'Your installation medium is on /dev/sda1. You will not be able to create, delete or resize partitions on this diskbut you may be able to install to existing partitions there'

The devices listed are:

/dev/nvme0n1
/dev/sda
/dev/sda1                  (Size)3650MB      (Used)unknown
/dev/sda2                  (Size)4MB           (Used)unknown
/dev/sda3                  (Size)0MB           (Used)unknown
free space                 (Size)0MB 
/dev/sda4      ext4      (Size)11816MB      (Used)294MB 

Where should I go from here?

I could just go back to Installation Type and choose 'Erase disk and install Ubuntu' then partition the disk using Gparted later assuming Gparted is stiil current. Would that be best or is there another way?

Cheers

---

### Post by tea for one on 2022-06-04
I assume that you wish to install on the internal nvme drive?
This disk doesn't have any partitions yet but the installer can create them automatically if required.
If there were partitions, you would see nvme0n1p1 nvme0n1p2 etc.
                                   
By the way, have you booted in UEFI mode?
In a live session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```
Also, use gparted in advance to create GPT on your chosen disk.

---

### Post by Mylorharbour on 2022-06-04
Hi Tea,
This is the only computer I've bought in the last 10 years so I know little about UEFI & GPT. I just put the installation stick into a USB port and kept pressing F12 as it booted up. Could I use Gparted in 'Try Ubuntu' mode?

---

### Post by sudodus on 2022-06-04
Yes

---

### Post by oldfred on 2022-06-04
Many, even new systems, need UEFI firmware update & SSD firmware update. Best to check you have latest firmware.

You should use gpt partitioning if creating partitions in advance with gparted.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

At bottom of link in my signature are Acronyms sub section with links to many definitions like gpt & UEFI. You can skip most of info in middle as those are all special cases, but good to review first part of link if not familiar with UEFI.

---

### Post by Mylorharbour on 2022-06-05
**Many, even new systems, need UEFI firmware update & SSD firmware update. Best to check you have latest firmware.**
This is a new laptop which has no operating system so where would I start to find its UEFI and SSD firmware status?

Thanks Oldfred but much of the info in your link is either not relevant (dual boot or system specific) or way over my head. My laptop is made by Novatech, a long standing small UK manufacturer. As this machine will be Ubuntu only, could you point me in the direction of a link for newbies which would help me simply install 22.04 on a clean machine? Seems Ubuntu, through no fault of it's own, may have now become too complex for mere mortals to install.

Cheers

---

### Post by tea for one on 2022-06-05
As you have a new laptop, it will be suitable for UEFI installations.
Boot your USB installer in UEFI mode.
Screenshot showing UEFI boot mode attached.
Double check that you are booted in UEFI mode with the terminal command
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Open gparted and create GPT on your nvme drive.
Allow the Ubuntu installer to organise your partitions.

---

### Post by zebra2 on 2022-06-05
It doesn't matter if it is a new computer or a five year old computer.  Grub has been updated to 1. fix some security problems and 2. to properly boot modern hardware and dual boot Windows 10.  A computer formally partitioned with an older layout to run bios or efi on 20.04 will not boot upgrading to 22.04. The ISO may install but the system will not boot with the older partition table.  You must use the updated partition scheme to get a boot of 22.04 regardless of whether it is a legacy or efi boot that is being attempted. 
The fact that you don't understand this just won't do.  The older partition schemes won't work starting with 22.04 so forget the old way and learn the new way. This is being pushed on us by the hardware changes and has nothing to do with Ubuntu other than the fact that Grub has been updated to support the changes. 
You and everyone else with boot problems in this section are in the same boat. 
Follow the directions and give up trying to get your old ideas to work. All of the instructions have been repeated repetitively in this section of the forum but they are not compatible with the older partition format. The fact that you system was working with an older Ubuntu means nothing.

---

### Post by oldfred on 2022-06-05
Have not saved any issues relating to Novatech. I try to keep a list of unique issues by brand.
Review the first page on installing in my link.

Its not Ubuntu as I remember the install process is essentially the same.
The issue now is UEFI and CSM/BIOS options and all the exta settings in UEFI over old limited BIOS.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
And of course each vendor implements the UEFI standard slightly different.
And Microsoft required UEFI/gpt and Secure Boot in UEFI (since 2012). So almost all systems are UEFI.
Very new systems may now be UEFI only which actually simplifies things.

So what settings your system may need will have to be reviewed by you. Best to read manual as explanation in UEFI is limited.

Another users suggestions to review settings:
 UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)
[https://ubuntuforums.org/showthread.php?t=2461231](https://ubuntuforums.org/showthread.php?t=2461231)

---

### Post by Mylorharbour on 2022-06-05
Thanks Tea,
My USB installer is in UEFI mode. I've opened Gparted, selected the unallocated 'partition' (nvme0n1), then I select Device, Create Partition Table, choose table type 'gpt', Apply but I dont get any indication that GPT has been applied. Am I missing something?

---

### Post by sudodus on 2022-06-05
I suggest that you

- boot a live session from your Ubuntu USB drive

- check that you boot in UEFI mode

```
test -d /sys/firmware/efi && echo efi || echo bios
```

- if it says 'bios', please boot into the UEFI/BIOS menus and set the computer to boot into UEFI mode

[hr][/hr]
- boot a live session from your Ubuntu USB drive

- start the installer and try with 'Erase disk and install Ubuntu' 

- if the installed system boots and works correctly, fine

[hr][/hr]
- otherwise, boot a live session from your Ubuntu USB drive again

- start gparted and create a GUID partition table, GPT, via the pulldown menu 'Device' select  'Create partition table' ...

- click the tick icon to finish the operation(s) and exit from gparted

- start the installer and try with 'Erase disk and install Ubuntu' (this time it is more likely to work correctly)

[hr][/hr]
- if you still have problems, maybe it is because of the graphics card/chip. If nvidia, you may need the boot option 'nomodeset'. 

- later on, when booted with 'nomodeset' into the installed system, you can try to install a proprietary graphics driver, and maybe also a proprietary wifi driver, if there are problems with wifi.

[hr][/hr]
Edit: You can test what partition table you have on the internal drive with the command

```

sudo parted -ls

```

or restart gparted, pull down the menu 'View' and select 'Device information' (and make the window wider)

---

### Post by tea for one on 2022-06-05
> **Mylorharbour said:**
> I've opened Gparted, selected the unallocated 'partition' (nvme0n1), then I select Device, Create Partition Table, choose table type 'gpt', Apply but I dont get any indication that GPT has been applied. Am I missing something?

You can check via Gparted > View > Device Information

---

### Post by Mylorharbour on 2022-06-05
Very nearly there Tea. Seems I just need to add an EFI Sytem Partition.

I have:- 
nvme0n1p1 ext4 / 75GB
nvmeon1p2 ntfs [the rest of my SSD]

How would I set this up?

---

### Post by tea for one on 2022-06-05
As you previously mentioned that you only want to install Ubuntu, you do not need a Microsoft ntfs partition.
Boot into the USB installation medium again (in UEFI mode) and allow the installer to create the necessary partitions.
The installer will automatically create an EFI system partition (ESP).

You can adjust the partitions later if desired.

---

### Post by Mylorharbour on 2022-06-05
Very nearly there Tea. Seems I just need to add an EFI Sytem Partition.

I have:- 
nvme0n1p1 ext4 / 75GB
nvmeon1p2 ntfs [the rest of my SSD]

How would I set this up?

---

### Post by Mylorharbour on 2022-06-05
Tried that Tea, I now have:-

nvme0n1p1 ext4 / 75GB
nvme0n1p2 ext4 [the rest of my SSD]

Then I choose Install now and get 'No EFI system partition was fouind'..........
Please go back and add an EFI system partition....

Seems I'm being asked to add it manually, but where?

---

### Post by ubfan1 on 2022-06-05
Usually just make the EFI partition the first one, a 300-500 MB FAT partition. Select the EFI partition type when you make it.  But it really can be anywhere.

---

### Post by Mylorharbour on 2022-06-06
Thank you all, especially Tea for One.
I gave up trying to create the EFI partition manually, just let Ubuntu install work on the whole SSD with no partitions and it created one for me so I'm now up and running.

Cheers

---

