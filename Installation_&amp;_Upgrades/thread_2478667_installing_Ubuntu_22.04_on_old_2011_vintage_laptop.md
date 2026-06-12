---
title: "installing Ubuntu 22.04 on old 2011 vintage laptop"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by bjh1 on 2022-09-01
Hello,  
    I'm trying to install Ubuntu 22.04 on an old laptop that originally had Windows 7 and became unusably slow.   I'm having a lot of problems.  I tried posting a question askubuntu.com and just received a series of insults rather than any real answer.  Please be kind.  I am a total novice at this stuff.   Here are the specifics

 The laptop is a Toshiba model A665-S5170 (2011 vintage I think)
I used Rufus to create the bootable USB.   I played around with this quite a bit before I could even create a USB that my laptop would even recognize at all.  the ONLY configuration I found that would result in a bootable USB was to use  MBR mode and also add the flag that says "add fixes for old BIOSes"    This lead me to believe that I have legacy BIOS with no UEFI support although people on that other forum said that's not possible in 2011.   In my BIOS itself I see no option anywhere that mentions EFI or UEFI.   The only option in the BIOS under the boot menu is fast boot or not fast boot.

The installation completes just fine.  However, when I restart after removing USB, boot fails completely and it just kicks be back into the BIOS
If I re insert USB again and just do "try ubuntu" I can see that is has removed windows, and reformatted my hard drive.   Doing sudo parted -l  seems to indicate that my hard drive is set up for a UEFI which I think is not what I want.  I say this because it says partition type is GPT and I also see /dev/sda2 formatted as EFI. 

Can anyone help?  It would be greatly appreciated.

---

### Post by ubfan1 on 2022-09-01
Pretty sure your BIOS settings are the clue -- without UEFI options, it isn't UEFI capable.  I have a Lenovo, 2011 that came with Win7, MSDOS partition type, but the UEFI options were present, and I eventually switched Windows to GPT/UEFI.  I'd prepartition the disk with a MSDOS partitioning table, not GPT -- on older machines, sometimes GPT can cause problems too.

---

### Post by oldfred on 2022-09-01
I had used Ubuntu on my 2006 Toshiba laptop BIOS only with 1.5GB of RAM. Last really used with Ubuntu 12.04. 
Tried to install 20.04 Ubuntu as a test, and it would not install at all. Was able to install server and fallback (lightweight gui).
I normally use Kubuntu  on my desktop, which is more of a mid-weight but full featured flavor and was surprised it installed to laptop and worked reasonable well.

Older systems often work better with a light weight flavor. Its just they only get 3 years, not the 5 years standard support that Ubuntu has. But I update every 2 years anyway.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by Dennis N on 2022-09-01
> Doing sudo parted -l seems to indicate that my hard drive is set up for a UEFI which I think is not what I want. I say this because it says partition type is GPT and I also see /dev/sda2 formatted as EFI. 
 
When installing in BIOS mode, the Ubuntu installer now uses GPT partitioning. It also creates an unnecessary empty EFI system partition in the process. 

For comparison to yours, this is an actual partitioning scheme in a bios mode install of Ubuntu 22.04 (using entire disk):

```
Disk /dev/vda: 26.8GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   26.8GB  26.3GB  ext4

```
I built a computer in May 2011 that uses a BIOS motherboard, so they were still available then.

---

### Post by grahammechanical on 2022-09-01
> Doing sudo parted -l  seems to indicate that my hard drive is set up for  a UEFI which I think is not what I want.  I say this because it says  partition type is GPT and I also see /dev/sda2 formatted as EFI. 

Please see the second post in this thread. I do not want to repeat myself so soon after writing that post. Thinking makes me tired. :)

[https://ubuntuforums.org/showthread.php?t=2478491](https://ubuntuforums.org/showthread.php?t=2478491)

Your hard drive partition table might well be GPT but that does not mean that the motherboard is UEFI based and not BIOS based.

If my memory serves me well, and at the age of 74 it often fails me, it was not unknown for Windows 7 to be installed in BIOS/Legacy mode even on UEFI motherboards. This is a link that we on this forum often pointed to when UEFI systems began to be standard.

> **Case when Ubuntu must be installed in UEFI mode**
Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

By the way, I stopped posting replies on AskUbuntu years ago. It is not a forum. They are trying to provided once-only definitive answers. If a question has already been asked you are supposed to find it and read the answer already given. On Ubuntu Forums will treat people as individuals and we have no problem helping people with the same problems that other have already asked about.

Regards

---

### Post by Impavidus on 2022-09-01
Right now, I'm using Xubuntu 22.04 on a laptop from 2011. I use Xubuntu instead of Ubuntu mostly because I prefer the user interface, but it's also lighter and performs better on older hardware.

The web tells me that your laptop has 4 GiB of memory, upgradable to 8 GiB, and a 640 GB 5400 rpm harddrive. You could consider replacing that hard drive by a slightly faster 7200 rpm harddrive or an even faster SSD. Startup of the laptop and applications should become faster. Mine came with a 7200 rpm harddrive, which I still use. Increasing the memory to the maximum of 8 GiB could be an improvement, although not as significant as replacing the harddrive. In my computer, I upgraded memory from 3 GiB to 8 GiB. But if you don't want to invest any more money in this old computer, that's fine too. Ubuntu (or at least Xubuntu, or another light flavour) should run fine and in particular those light flavours should be faster than Windows 7. Not in the least because you don't have to run antivirus in the background all the time. Anyway, Windows 7 is no longer supported.

Computers of around 2011 typically support UEFI, but not necessarily and even if they claim to support it, those early UEFIs aren't always standards-conforming, in which case legacy mode may work easier. My computer is known non-conforming, so I kept it at legacy mode (which was the default and back then I didn't really know). Even in legacy mode, you can install Ubuntu to a GPT partitioned hard drive. That will create a bios_grub partition. It should all be handled automatically by the installer. An empty, unused EFI partition may be created too.

If you want to stay with Ubuntu, or if you switch to Xubuntu or some other light flavour and the same problem still occurs, maybe you can try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and create a boot info summary. It may tell us more. It looks like something went wrong with the installation of the boot loader.

---

### Post by ajgreeny on 2022-09-01
You tell us that you have seen the partition **/dev/sda2 formatted as EFI** but do not mention any others such as the needed **bios-grub** partition.

If installing in MBR/BIOS mode and not UEFI you also need a very small (1MB) unformatted partition with the ***bios-grub*** flag but you didn't mention that. 
If there is no such partition you will not be able to install as MBR/BIOS successfully using GPT partitions.

---

### Post by bjh1 on 2022-09-01
Tried repartitioning with an MS DOS type partition.  Now on bootup it just says
Missing Operation system 
and locks up

---

### Post by ajgreeny on 2022-09-01
After you repartioned I assume you reinstalled; yes?

---

### Post by bjh1 on 2022-09-02
I also tried installing Kubuntu.  Same issue.  Boot failed and kicks back to the BIOS

---

### Post by bjh1 on 2022-09-02
here is the listing from parted after installing kubuntu.  Its identical to what I saw from ubuntu install before

Model: ATA TOSHIBA MK6465GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   640GB   640GB   ext4

---

### Post by bjh1 on 2022-09-02
I'll make a correction to what I just said.  The partitions look exactly the same as they did when I tried to install ubuntu, but ubuntu installer partioned the drive as gpt and I see Kubuntu partitioned it as ms-dos

---

### Post by cigtoxdoc on 2022-09-02
Ubuntu Unity 22.04 works very well on my Dell Vostro 3500.  It is so old that it came with Win XP Pro SP3 installed.

John

---

