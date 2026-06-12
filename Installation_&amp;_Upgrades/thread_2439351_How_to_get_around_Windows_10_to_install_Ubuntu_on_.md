---
title: "How to get around Windows 10 to install Ubuntu on my laptop"
date: 2020-03-26
forum: Installation &amp; Upgrades
---

### Post by redaxe90 on 2020-03-26
Hey guys

I reckon you're my last hope in this problematic issue. The thing is, I bought this HP Notebook last year, the model type is 17-ca0861no.
It has some weird low level binding between the BIOS and Windows 10 and I just can't get rid of the irritating thing. No matter which distro of Linux I try, none of them can see either the internal harddrive or optical drive. I got around this by installing Ubuntu to an external drive, but now I can't do a distro upgrade, because the computer hangs on the spot. Has anybody ever come across this issue before? If so, how in the world did you manage to get around it?

BTW I managed to set up Ubuntu 18.04, but anything after that hangs during boot, even when I try to boot to a liveCD session.

---

### Post by yancek on 2020-03-26
Not seeing the internal drive from a Linux system on a drive which has windows installed is usually because windows has been left hibernated.  Make sure you have fastboot and anything related to hibernation off before beginning the install.
If windows 10 was installed when you got the computer, it is almost certainly in UEFI mode so Ubuntu would need to be installed in UEFI mode also.  In that case, you should be able to boot both Ubuntu and windows from the Grub boot menu.
Check to see if you have UEFI which you can do from the the Ubuntu install DVD/USB by opening a terminal and running the command:  sudo fdisk -l (lower case letter L in the command).  Post the output here. 

>  because the computer hangs on the spot. 

You will need to clarify what that means.

---

### Post by redaxe90 on 2020-03-27
> **yancek said:**
> Not seeing the internal drive from a Linux system on a drive which has windows installed is usually because windows has been left hibernated.  Make sure you have fastboot and anything related to hibernation off before beginning the install.
If windows 10 was installed when you got the computer, it is almost certainly in UEFI mode so Ubuntu would need to be installed in UEFI mode also.  In that case, you should be able to boot both Ubuntu and windows from the Grub boot menu.
Check to see if you have UEFI which you can do from the the Ubuntu install DVD/USB by opening a terminal and running the command:  sudo fdisk -l (lower case letter L in the command).  Post the output here. 



You will need to clarify what that means.

No hibernation going on. I shut down the computer, start a boot by frequently hammering the F9 button to choose the boot order and boot from the exterbal drive that's hosting Ubuntu. The problem is that there is some weird kind of low level tie between bios and win10 so no linux distro has the capability to see the internal drives. I was trying to install in UEFI mode but when I bring in a newer distro than the one I managed to install on my external drive, the computer freezes before I get to any screen that has selectable options (hence my hangs on the spot comment) and trying to do a distro upgrade from within Ubuntu the same thing happens, everything freezes. I'm wondering if I'm staring at having to live with this annoying virus that is Windows on my machine.

I can't run a liveCD or liveUSB stick, because the computer hangs now before it gets anywhere. I can boot into Ubuntu 18.04, running on an external hdd, but no internal things are visible, other than graphics, usb and hdmi. I can't even use the CD drive within Ubuntu. It's just not seen.

As for the sudo fdisk -l command:
```
Disk /dev/loop0: 91,3 MiB, 95748096 bytes, 187008 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 173,5 MiB, 181915648 bytes, 355304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 91,4 MiB, 95805440 bytes, 187120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 202,9 MiB, 212758528 bytes, 415544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 174,8 MiB, 183242752 bytes, 357896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








Disk /dev/sda: 931,5 GiB, 1000204884992 bytes, 1953525166 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BD7C2ACC-C85B-41DF-8A42-BC9537E2C472


Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux LVM




Disk /dev/mapper/ubuntu--studio--vg-root: 930,1 GiB, 998638616576 bytes, 1950466048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/ubuntu--studio--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



```

---

### Post by yancek on 2020-03-27
I don't know what the problem is but you might review the link below on turning off fastboot and or hibernation.  Windows updates will turn it back on even after you have turned it off.  You will not be asked if you want this nor will you be informed that it  is happening.  The 2nd link below is the microsoft site which explains disabling/enabling hibernation.

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

[https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

Some of the other problems you mention see to be not related to this.  Do you vefify the download of Ubuntu and any other OS you try before burning to a DVD or usb?

---

### Post by oldfred on 2020-03-27
Have you updated UEFI and if SSD, the SSD firmware?
Many with HP have said resetting boot order with efibootmgr does not work. And grub uses efibootmgr to reset to make grub first. That works once, then Windows or UEFI reset to make Windows first.
Those that updated UEFI have said they then could change boot order in UEFI and that did work. 
I think UEFI & Windows BCD do some sort of sync.

Issues often common across multiple models by brand. Bigger difference if AMD or Intel based.
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)
HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)
HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)

---

