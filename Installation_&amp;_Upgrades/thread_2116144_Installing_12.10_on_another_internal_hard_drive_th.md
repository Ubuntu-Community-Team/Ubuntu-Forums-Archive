---
title: "Installing 12.10 on another internal hard drive that is not the main drive"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by shalviy on 2013-02-15
I am am trying to install 12.10 on my computer. I currently have Windows 7 on it on a 60gb SSD and I have the rest of my Program Files on my larger, 750gb HDD. I would like to install to the HDD since I require more than 70gb of space for the things I do on Linux. I tried installing 12.10 using the built in installer but it would not work. It did install but it did not get to the screen where I can choose the OS. It automatically defaults to the Windows 7 OS. I have no way to get to Ubuntu. I then deleted the partition and merged it back with the main partition as was in the beginning. Is there any way to install 12.10 on the HDD since it is not the main drive for my primary OS? Google isn't being helpful with this...

EDIT: Anything that can do this would be appreciated; CMD commands, 3rd party programs, etc...

---

### Post by ahallubuntu on 2013-02-15
~

---

### Post by shalviy on 2013-02-15
This is a custom computer that I put together myself.
I did change the boot priority in the BIOS (I have an ASRock Experimental4 Gene3 Motherboard and for some odd reason it auto boots to BIOS). That did not work. It just skips the HDD and goes straight to the SSD. If I set the SSD last in priority, it skips the 1st priority (HDD) to go to the next available option (USB or Disc Drive). I took out the USB I used to install 12.10 and removed the discs in the CD Drives and tried again. It skipped the HDD and then booted from the SSD. Should I just remove the SSD physically and try to boot to see what happens?

---

### Post by carl4926 on 2013-02-15
You shouldn't need to change the boot order
Simply partition your additional HD as required
I would suggest

swap
ext4 for /
ext4 for /home

I use Parted Magic to setup partitions prior to a install.

Then start the Ubuntu installer and choose Something Else here: [https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Then set the mount points and reformat options here:
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
(Thats just an example of mine, your partitions are different)

Set grub to the first HD mbr
usually SDA

---

### Post by oldfred on 2013-02-15
Some have reported this as an issue with Asrock.

> So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
    Are you booting in BIOS/AHCI or UEFI mode?

       AsRock calls BIOS mode AHCI.
Another quote:
> "Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

---

### Post by shalviy on 2013-02-15
I am booting from a flashdrive with Ubuntu 12.10 on it instead of a CD. I do not have a Asrock Z77 motherboard. I have the Asrock Experimental4 Gene3 motherboard. Whenever I start my computer if it shutdown, it starts at the UEFI Setup Utility and does not exit it automatically and go to the OS unless I manually click "Discard Changes and Exit." If I click the "Launch EFI Shell from filesystem device" I get a "Not found message."(EDIT/NOTE: I just fixed this by Clearing the CMOS, loading the UEFI defaults, and then setting boot priority to the HDD first over the SSD. The HDD does not have the Windows loader. The SSD has the Windows loader so after checking for a loader in the HDD, it moves to the SSD and then boots.) My Marvell SATA3 Operation Mode is set to IDE (out of the choices of Disabled, IDE Mode, and AHCI Mode). My SATA mode is set to IDE Mode (out of the choices of Disabled, IDE Mode, AHCI Mode, and RAID Mode).

My main drive with Windows 7 loader is the 60gb SSD which is /dev/sda. Should I use /dev/sdb which is the 750gb HDD for the grub/bootloader?

---

### Post by darkod on 2013-02-15
When installing from usb sometimes the installer can put grub2 on the stick, since that is the first device you booted from to install.

I suggest using the manual install (Something Else) which gives you best control of partition sizes, location and most important, bootloader destination.

Even if grub2 doesn't end up where you wanted it or doesn't install at all, don't delete the ubuntu partitions right away. It's easy to add only grub2 later.

As for whether to put grub2 on /dev/sda or /dev/sdb, your choice. Just remember to try and boot from the same disk. And that grub2 might fail to install.

Boot-repair run from live mode can help you see tons of important data, including the bootloaders on each disk, partitions, OS on them, etc.
It's called bootinfo summary:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It can also help install grub2, but I prefer doing it manually. I think boot-repair installs it on all MBRs and maybe you want to keep windows bootloader on /dev/sda. So don't run the recommended repair even though it might sound tempting. :)

What oldfred asked about win7 being in legacy mode or UEFI mode is important, since you need to install ubuntu in the same mode for dual boot to work.

---

### Post by oldfred on 2013-02-15
Is Windows in BIOS mode or UEFI mode? You want Ubuntu in the same mode. 

If BIOS you can set to boot Ubuntu drive & I think it will see that as sda, but still best to use Something Else or manual install and specify which drive's MBR to install grub boot loader into.

If UEFI you want an efi partition on each drive. And if ever thinking you might want UEFI in future best to allocate 200 or 300MB at beginning of hard drive for a future efi partition. But drive has to be gpt to use UEFI.

If in gpt you also will need the bios_grub partition if booting in BIOS mode.

---

### Post by shalviy on 2013-02-15
> **oldfred said:**
> Is Windows in BIOS mode or UEFI mode? You want Ubuntu in the same mode. 


I'm not sure if Windows is in BIOS mode or UEFI mode. How can I check?

---

### Post by darkod on 2013-02-15
Easiest might be booting into ubuntu live mode and checking the sda details:
sudo parted /dev/sda print

If the partition table is gpt then win7 is in uefi because it can only work on gpt with uefi.
Vice versa, if the table is msdos you have win7 in legacy mode since it can't work in uefi on msdos table.

If win7 is in legacy mode, I suggest going into bios and disabling uefi boot. If this is a newer board it will have uefi support so you need to find the setting to disable it to avoid any future confusion and booting in uefi mode since win7 is in legacy. Depending on the board, the setting might say like Boot Mode: Legacy Only, or UEFI boot: Disable, etc.

---

### Post by shalviy on 2013-02-17
I won't be able to check for a while (about a week). I'll post new replies when I can.

---

