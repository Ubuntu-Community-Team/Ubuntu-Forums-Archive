---
title: "Adding Windows 7 to an Ubuntu Laptop"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by nitroguy on 2012-07-05
Hey there.

I got a fancy new Lenovo S205 that I have up and running with Ubuntu 12.04, but to make it successfully run Ubuntu, I had to completely strip out my Windows OS that shipped with it. No big deal, I spend 95% of my time in Ubuntu anyways.

Here's the problem: The other 5%. I need Windows.

Is there any way to add Windows 7 to my Ubuntu system to create a dual-boot machine? I google'd it, and came up with this, from askubuntu.com:

> Delete a partition from your current setup that refers to swap area, or linux swap. You'll be able to re-create and tune it later. Create a logical partition in place of the removed one. From now on, you'll be able to create more logical partitions. Fill the created partition with you Win-7 backup (if you don't have enough space for it, resize other partitions to free some space beforehand). Then boot Linux and do update-grub, that will detect your Win-7 partition and will put a line for booting to it in the boot menu. Then reboot into your system of choice - you're dual-booter now!

Seems simple enough, but I'm a bit new (or at least, inexperienced), so I'll need it broken down a bit more.

I've shrunk my Ubuntu partition down using gparted, and I formatted the extra space as NTFS, but when I go to install Windows, it says I'm formatted all wrong, and it can't install unless it wipes everything (not an option at this point).

Can anyone help me?

Thanks!

---

### Post by Bucky Ball on 2012-07-06
That's Windows for ya. Wants drive1, partition1. Easiest would be to move everything and leave the free space at the start of the disk, but could take an age. You might find these of interest:

[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

... although there is software to take the pain out of this (Super Grub Disk and Boot Rescue come to mind), and this link will tell you everything you need to know ...

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Problematic installing Win second but doable. One other point: You can only have four primary partitions on one physical drive. Generally I go three primary and an extended partition, inside which you can put as many logical drives/partitions as your machine can handle). If you were attempting to install Win inside an extended partition, that could cause problems. It won't live there. ;)

---

### Post by oldfred on 2012-07-06
Is the NTFS partition a primary partition? or one of  sda1 thru sda4? And did you put a boot flag on the partition. 

With Windows 7 it will probably need to reformat it again anyway as gparted's NTFS works for XP or data, but Windows 7 has a slightly different partition boot sector (specifies bootmgr, not ntldr for XP) which it should create as part of the install. Some have had to use the Windows console to reformat first.

---

### Post by nitroguy on 2012-07-06
> **oldfred said:**
> Is the NTFS partition a primary partition? or one of  sda1 thru sda4? And did you put a boot flag on the partition. 


Thanks for the advice. I've attached my gparted view, so we're all on the same page:

[IMG]https://dl.dropbox.com/u/34549309/Screenshot%20from%202012-07-06%2008%3A38%3A05.png[/IMG]

It looks like it's sda3, and no, I don't believe I put a boot flag on it. I'm pretty sure I know how to put a boot flag on it (liveCD, edit, check the boot box), but not sure how to turn it from sda3 to anything else. Is this what you mean when you say I need to turn it from a Primary to an Extended? Could you give me a heads up on how that's done?

Thanks!

---

### Post by oldfred on 2012-07-06
You are showing an efi partition. gparted does not show it but is drive gpt? If so Windows will only install in UEFI mode. Also if gpt all partitions are primary.

Also your efi partition is FAT16, which was (is) a bug in the Ubuntu UEFI installer. Copy files from sda1 and reformat to FAT32 if installing Windows in UEFI mode. Then copy grub/Ubuntu efi files back into the FAT32 partition.

FAT16 is ok for removeable devices per UEFI spec so it works, but fixed devices are supposed to be FAT32.

IF UEFI do not move boot flag from efi partition to Windows.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by nitroguy on 2012-07-06
> **oldfred said:**
> You are showing an efi partition. gparted does not show it but is drive gpt? If so Windows will only install in UEFI mode. Also if gpt all partitions are primary.

Also your efi partition is FAT16, which was (is) a bug in the Ubuntu UEFI installer. Copy files from sda1 and reformat to FAT32 if installing Windows in UEFI mode. Then copy grub/Ubuntu efi files back into the FAT32 partition.

FAT16 is ok for removeable devices per UEFI spec so it works, but fixed devices are supposed to be FAT32.

IF UEFI do not move boot flag from efi partition to Windows.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Oh man, I'm in this deep. Let's see if I can navigate some answers to decipher what I need to do...

Is drive gpt? - gpt= Gnu Partition Table, right? (if so, I'm incredibly proud of myself). How do I determine this? I wiped the hdd clean, and installed Ubuntu, so if that's a default, I'm sure it is.

Copying files, reformatting to FAT32 - Is that literally as simple as copy/paste? Seems like there'd be hidden files or something that I'd miss, and then be screwed. Could you give me some more direction on how to make this happen?

Have to install windows in UEFI mode - isn't that a default? I thought I read somewhere that Windows went to that standard a while ago. My laptop has UEFI BIOS issues (took me FOREVER to get Ubuntu installed) so I'm a little gun-shy to make wholesale changes lest something goes terribly wrong.

> In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!
I don't actually have any idea what this means. Could you help translate it for me?

Sorry for the ignorance. But, as they say, you don't learn 'till your fingers get dirty. Thanks to all for helping my fingers to get a bit dirty. ;-)

---

### Post by oldfred on 2012-07-06
You can see gpt partition by downloading gdisk or using parted. fdisk does not work.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

All the discussion on boot flag is not to change it from sda1, the efi partition.

I thought Ubuntu would install to large drives (over 1TB) as gpt, but still could be BIOS or UEFI. But if installed as UEFI then you should install Windows to UEFI.

I think both Window and Ubuntu will offer both a UEFI/efi or BIOS/MBR option when using the UEFI menu to boot from liveCD/USB to install. I know with Ubuntu it is best to format in advance, not sure about Windows. 

I do not know that Windows has to be first, but it may want space for several partitions. Since they are all primary it should not matter.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

More info on UEFI:
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

Someone posted this, which is not very many files in the efi partition:
find /boot/efi -name "*efi"
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

Some also had this, which I think works with UEFI/BIOS:
/boot/efi/EFI/BOOT/bootx64.efi

---

### Post by nitroguy on 2012-07-12
Well, I made two steps forward, let's just hope that it's not three steps back.

Firstly, oldfred, I apologize. I'm apparently rather new at this still, and most of your information helped point me in a general direction, but I'm not competent enough to follow your instructions to the T.

To recap: 
Here's what I've done. I partitioned my hdd to have an NTFS partition, and I added the boot flag to that partition. So, I do:  ```
sudo gparted
``` and I get:

[IMG]https://dl.dropbox.com/u/34549309/Screenshot%20from%202012-07-12%2018%3A56%3A28.png[/IMG]

But when trying to install Windows, it doesn't work, as Windows gave me an error saying it couldn't install to a GPT formatted drive. I did some digging, and found a utility often used by Mac users. So, from a LiveCD, I did ```
sudo gptsync /dev/sda
``` and it asked if it could make changes. I said "Sure!" and rebooted into my Windows 7 USB installer. **It worked!** I successfully installed Windows!

Reboot, goes straight to Ubuntu, no Grub option. Hmmm.

Go back to my Windows 7 installer, and I chose "Fix startup issues", and it proudly declared there was nothing wrong with my system. Hmmm.

Luckily, I still have a working Ubuntu partition, so I'm good to keep researching stuff, not having to resort to my phone. From here, more research, and I then do a ```
sudo update-grub
``` and reboot. When I do this, I actually get a Windows 7 option on grub! (Grub is version 1.99, for what it's worth, so it's not grub2. Not sure what that affects).
But, when I click it, it says "Invalid EFI Path, choose another option". Hmmm.

To summarize, Ubuntu 12.04 works. I have a complete installation of Windows 7 on an NTFS partition, grub even says so, but won't go into it, even after updating grub.

For reference, here's the result of a "gdisk":
```
$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

```

I'm sure there's an issue somewhere in my GPT/MBR/EFI/BIOS/Boot Flag mess. But to be perfectly honest, I'm only skin deep in my knowledge of this stuff. I've gotten this far by "stabbing in the dark, and seeing what screams". 

Can anyone help?! PLEASE?!!

---

### Post by nitroguy on 2012-07-12
A bit more pictures to help further clarify things. (Apology: Not sure how to take screenshots before the OS is booted, so I resorted to my phone. Ghetto, but it works).

GRUB screen:
[IMG]https://dl.dropbox.com/u/34549309/20120712_193804.jpg[/IMG]

When I try to click on Windows 7:
[IMG]https://dl.dropbox.com/u/34549309/20120712_193813.jpg[/IMG]

Before I click "Startup Repair" in the Windows 7 Installer: (note the "Location Unknown" part - is that part of my problem?)
[IMG]https://dl.dropbox.com/u/34549309/20120712_193535.jpg[/IMG]

---

### Post by oldfred on 2012-07-12
Sorry, Boot flag on NTFS is only for BIOS/MBR type systems. 

The "boot flag" in UEFI/gpt systems is not really a boot flag (even though gparted shows it the same) but is the gpt partition code ef00 which specifies the efi partition Since the efi partition is the boot partition I guess having the boot flag there is correct.

Move the boot flag back to the efi or sda1 partition if in gparted. 

You also do not want the hybrid MBR/gpt like Macs use. That is prone to many errors. Best to have "boot" flag on sda and both systems installed in UEFI mode.

Since Ubuntu created the FAT16 you will have to back up the boot files in that partition. Change/reformat to FAT32 and then Windows should install in UEFI mode. Copy Ubuntu boot files back. 

You also have to remove the hybrid partition mode.
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I think I have posted links to what I can on UEFI. The help.ubuntu and arch sites have good info on UEFI.

---

### Post by nitroguy on 2012-07-13
Thanks for your help. Either you said something more clear, or my head is just so far in this, that it's actually starting to make sense! :-)

Just to be clear, these are the steps I will take:

1) copy my files off my FAT16 partition, reformat to FAT32, and copy files back. This will all be done in a live session, I'm guessing?

2) Move "boot" flag back to my efi partition (where it was before)

3) Remove my hybrid partition mode, as described in your link.

Once I do these, will I have to reinstall Windows, or will it start working? Was the reason it didn't install the first time because of that FAT16 issue?

---

### Post by oldfred on 2012-07-13
I think Windows did not install as the efi partition was not FAT32, but the NTFS partition. So not sure if just not the efi or ef00 or format also was an issue.

The explanation of the FAT16 but by grub was the UEFI spec says FAT16 is ok. But fine print says that is only for removeable devices and it should be FAT32. Windows expects FAT32. Grub did have the bug where it just rewrites the efi partition, so if you have Windows installed first it ignored that and overwrote the correct FAT32 and Windows efi files with its own FAT16 efi partition.

this is now older & some have been fixed in the newest versions of grub.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

