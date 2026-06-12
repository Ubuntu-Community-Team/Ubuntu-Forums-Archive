---
title: "How do I install encrypted Ubuntu 22.04 onto an external SDD if...."
date: 2024-04-25
forum: Installation &amp; Upgrades
---

### Post by nickysubone on 2024-04-25
What I'm looking to do is to have Ubuntu 22.04 encrypted on an external SDD. 

 I'd prefer for this encrypted 22.04 to be able to **run on multiple PCs** but I'll settle for it to only be able to run on the one I'm setting it up on if absolutely necessary.   If the additional info helps, the computer I'm using has Windows on it and I'd like to keep that OS. Id rather not have two operating systems on the internal HD either, I just want to use the new encrypted Ubuntu when I have the external SSD plugged in.   

Thanks ahead of time for any help or tips...

---

### Post by tea for one on 2024-04-25
Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that only the target drive is accessible
Boot into a “Try Ubuntu” live session and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
If you cannot isolate your Windows 10/11 drive, you can hide the existing EFI partition.
Gparted > Right click Windows EFI Partition > Manage Flags > Uncheck boot & esp and check hidden (msfdata will be checked automatically – not a problem)
Don’t forget to reset the flags to original settings after installing Ubuntu to 2nd disk
Installation type – Something else will allow advanced partition choices
The installer should create an EFI partition automagically
If not, create an EFI partition and System / partition (or double check that they will be created)
Boot loader on target disk 
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have an EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)
If you choose encryption, then ensure that you have regular data backups

> **nickysubone said:**
> I just want to use the new encrypted Ubuntu when I have the external SSD plugged in
In your UEFI settings, you will have to set external devices to be the first boot priority.

---

### Post by nickysubone on 2024-04-26
Thanks, I think this will help although I will say it's been years since I installed Ubuntu or fooled around with partitions for it.  I remember some things but will probably get stuck somewhere if it's not clear where to find a setting or program.  With that said, I'll probably be back on here as I try to work this out if you're okay to giving some more tips.

---

### Post by tea for one on 2024-04-26
> **nickysubone said:**
>  I think this will help although I will say it's been years since I installed Ubuntu
Probably worth creating a bootable usb first and exploring Ubuntu in a "Try Ubuntu" (live) session
> **nickysubone said:**
> I'll probably be back on here as I try to work this out if you're okay to giving some more tips.
Of course, happy to help.
Plus, there are many other forum members who are also keen to offer useful tips

---

### Post by nickysubone on 2024-04-27
Thanks!

I did run into a snag last night.  Or more like I need verification on some things.  

The bios doesn't have an option to turn off the internal HD or isolate it though other means and opening the laptop on this model would be risky. Hard to explain but on this model even with all the screws loose when I try to separate the bottom and top, something on the inside has always resisted and I'm afraid if I force it apart, something important will snap.

I did verify that I'm in UEFI mode and did what you said in Gparted to hide the existing EFI partition.  With that said, the Windows partitions are visible in the installer.

SDA is the internal Windows drive with it's partitions.
SDB is the flash drive with the Ubuntu installer.
SDC is the external SSD drive that I want to install encrypted Ubuntu onto.

**So given that the internal drive is still visible to the installer, I just wanted to verify that it will only install to or modify the drive that I highlight in orange.**  I selected for the bootloader to go onto the external as well so that shouldn't be a problem.

Other than that... 

When I used Gparted to make the gpt on the external drive it appears to have made the whole drive unallocated space, I'm assuming that's normal.

**Most importantly** **I'm unclear about how to partition the external drive for the Ubuntu install... **

> [COLOR=#000000]The installer should create an EFI partition automagically[/COLOR]
[COLOR=#000000]If not, create an EFI partition and System / partition (or double check that they will be created)[/COLOR]

On this, I'm not seeing that the installer created an EFI partition automatically unless you mean it should do that during the install process after I start it.  I'd assume thats the case but what about other partitions?  If I remember right from last night, the installer wouldn't let me continue without creating partitions.  Does Ubuntu still need boot, home, and swap partitions?

**If you don't mind. I'd feel more confident if you can tell me which partitions to make, and the settings and sizes for each since there will likely only be two or three of them.**   If it helps, the external drive is 256Gigs and I have 6 gigs of ram if that's still relevant to swap.   I understand that partition sizes can be chosen by the user based on personal preference, especially in the case of something like the partition that we save our files to, I just basically need an example of something that'd work well.  I'm unsure of normal swap partition sizes if needed and certainly the settings to choose for each partition.  Like the correct file format for example, I only remember ext4.

---

### Post by tea for one on 2024-04-27
After you have removed esp and boot flags from your Windows internal drive, open Disks and check that the partition is not mounted. Unmount other partitions as you see fit.

During the installation process:-
Erase disk and install Ubuntu – Select sdc
Bootloader to sdc

The installer will automatically create the essential partitions
You will also see a window with [COLOR="#0000FF"]Review your choices [/COLOR]– as attachment
Double check that the destination disk is correct.

A swap file is now used instead of a swap partition

Two more points:-
Have you backed up your Windows data?
Do you have a Windows repair usb (for emergencies)?

---

### Post by MAFoElffen on 2024-04-27
You are making things more complex than they really need to be. There is an easier way, which 'tea for one' hinted at in his first reply...

If you want something to install to USB as a portable system, that will be able to boot to other systems, and not affect what is on the original computer... Then disconnect all drives from the original computer except the Target USB external drive, and the Installer LiveUSB in another USB drive.

It should boot from the Installer Live USB, and only see itself and the target USB drive... That makes things more simple and fool-proof.

To boot it after the install, during the boot, you just hit the Boot Menu Hot-Key of that computer (Usually F10 or F11), and select the USB drive of the portable OS to boot from. Remember to keep the OS_PROBER in Grub2 disabled during upgrades.

---

### Post by nickysubone on 2024-04-27
Yes, thankfully I have a Macrium reflect full disk backup that should work if something goes wrong, it's just a pain to mess with. :) 

I'll give it a go again tonight and try what you said with the flags and unmounting.  

In the meantime, as far as what you said here about selecting...

> [COLOR=#000000]"Erase disk and install Ubuntu"[/COLOR]

Is that an installation type you're mentioning?    Before you had mentioned perhaps doing this...

> [COLOR=#000000]"Installation type &#8211; Something else will allow advanced partition choices"[/COLOR]

 I'm not where I can boot Ubuntu at the moment to verify but don't I have to pick one or the other? 

Sorry if that's a dumb question.  I don't need advanced partition choices as long as the option to encrypt is available under the erase entire disk install option. I'll be able to check again later I just wanted to put this out there now in case you can respond back before later tonight.  Starting tomorrow I'm going on vacation unfortunately so for a few weeks I won't be able to fiddle with this.  If there's anything else you can think of just let me know.  This doesn't seem overly complicated, I just like to make sure I'm doing everything just right if its an OS installation I haven't messed with in ages.

---

### Post by tea for one on 2024-04-28
I made these choices during the installation process (Ubuntu 24.04):-

Erase Disk and install Ubuntu
Use LVM and encryption
NB: Remember to choose the [COLOR="#0000FF"]external[/COLOR] disk

New screenshot of [COLOR="#0000FF"]Review your choices[/COLOR] attached

Having booted the encrypted, external disk, here is the partition info (created automatically)
Two outputs - lsblk and parted
```
test@test:~$ lsblk -e7
NAME                        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
sda                           8:0    0  74.5G  0 disk  
&#9500;&#9472;sda1                        8:1    0     1G  0 part  /boot/efi
&#9500;&#9472;sda2                        8:2    0     2G  0 part  /boot
&#9492;&#9472;sda3                        8:3    0  71.5G  0 part  
  &#9492;&#9472;dm_crypt-0              252:0    0  71.5G  0 crypt 
    &#9492;&#9472;ubuntu--vg-ubuntu--lv 252:1    0  71.5G  0 lvm   /var/snap/firefox/common/host-hunspell
                                                       /
```
```
test@test:~$ sudo parted -l
Model: Hitachi HTS541680J9SA00 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  3276MB  2147MB  ext4
 3      3276MB  80.0GB  76.7GB
```

---

### Post by nickysubone on 2024-04-28
It appears to have installed without any impact to the Windows OS that I can see, both OSs boot and run.  I still have some tests to do to see how well Ubuntu will run externally on a laptop this old though and need to test the external on other computers but so far things look good.

Also, perhaps hiding and unmourning the partitions ultimately helped to keep activity off of the internal HD during the install process but those partitions were still showing up in the installer menu somehow. Just in case that info helps you when assisting others.  It turned out to be a non issue for me though.

Anyway, thanks for the help!  I'll probably do a follow-up here once I have a chance to test things more thoroughly but that wont be for another three weeks roughly speaking.  If there are any replies here in the meantime, it might not be until then that I see them.  ):P

---

