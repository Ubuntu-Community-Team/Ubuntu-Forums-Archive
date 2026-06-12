---
title: "Dual boot 16.04/17.10 - Merged 17.10 to 16.04 &amp; Now Boots to Grub Only"
date: 2017-07-27
forum: Installation &amp; Upgrades
---

### Post by skanger on 2017-07-27
I have a laptop where I installed 16.04 but wanted to try out the new desktop in 17.10 so I created a partition from free space on the drive using gparted and installed 17.10 there. After giving 17.10 a good workout I decided to remove it and stay with 16.04.

The operation is no problem for me but I should have asked here first since grub and its menus and commands are still a haze to me.

The re-merge of the 17.10 partition was easy but upon re-boot the laptop was no longer seeing the 16.04 partition - or if it was it could only boot to a grub command line.

I used the disk utility to mount the main partition and found that all the files are intact. I tried messing with partition flags and looked at the EFI boot partition and its few files but decided to leave these alone rather than likely make things worse.

The odd thing is the installation of 16.04 did not set up grub and its menu but 17.10 did. Since I'm going to stay with 16.04 only I'd prefer to remove grub and boot directly to it. 

Help with this would be greatly appreciated!

Thank you
Skanger


ps - I just looked into removing grub and see that its better to keep it, so I'm interested in setting it up for single boot to 16.04.

---

### Post by Bucky Ball on 2017-07-27
Actually, if 16.04 was booting fine, it did install and setup grub. The control of grub was then taken over when you installed 17.10 and it installed and setup its grub, meaning 17.10 took control. Unless you manually instruct otherwise, the last installed OS is the grub you're using. Consequently, removing 17.10 killed grub. 

Grub is still fine in 16.04 no doubt, just have to set it up again. Easy way is to use Boot Repair, but DON'T use the 'Recommended Repair' option, go to 'Advanced' and reinstall the grub to sda (not sda1 or sda*).

[See here for further details]("https://help.ubuntu.com/community/Grub2/Installing#via_Boot-Repair_Graphical_Tool-1") and let us know of brickwalls and progress.

---

### Post by oldfred on 2017-07-27
Boot-Repair is the easy way as Bucky Ball recommends.

In /EFI/ubuntu is a three line grub.cfg that refers to the partition with the full grub.cfg. It uses both UUID & partition.

This is normally a three line file, but I edited it to have my main working install. Temporary install was in sdb9 (hd1,gpt9) and that partitions UUID. Main install is in sda6.

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by skanger on 2017-07-28
Thanks for your replies Fred & Bucky.

I first tried system rescue but admit I could not decipher it.

Then I tried the boot repair iso and ran it but sda was not available. The drive in the laptop is an emmc, so the device was listed as mmcblk1 (pt1, pt2).

Ubuntu 16.04.2 was identified as functional however I received and ESP locked error. The extremely long text file mentions something about the EFI partition not available.

It seems like its just one step away from working, but maybe when I played with the partition flags I changed something or possibly when I merged the 17.10 partition something was changed.

At this point I'm lost with all of the acronyms (esp, efi, uefi, etc).

Skanger

---

### Post by oldfred on 2017-07-28
I have list of acronyms, description and link to longer descriptions at end of my link in my signature.

You must have boot flag (if using parted or gparted) only on the ESP - efi system partition which is the FAT32 partition.

If trying to look at ESP from inside your install, it is hidden.

Sometimes from other systems the locked means it needs repairs.
       Must be unmounted, example is /dev/sda1, but if your is a mmc check exact partition and use that.
See partitions:
sudo parted -l
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

    
       man dosfsck

---

### Post by skanger on 2017-07-28
before i try anything further i want to check with you about the flags and mounting options:

1) i have 3 partitions on the mmcblk1 emmc drive - the efi partition mmcblk1pt1, the linux partition mmcblk1pt2, and a swap partition mmhe mmcblk1pt3

2) i checked in the disk utility and set pt1 and pt2 to mount at startup and to be visible in the UI

3) in gparted, i set the pt1 boot flags to 'boot' and 'esp' and the pt2 to 'bios_grub'
 
are these the correct settings to get back to normal functioning?

---

### Post by oldfred on 2017-07-28
The ESP is for UEFI boot (FAT32). And a bios_grub partition is totally unformatted space and normally 1 or 2MB.
If you put a bios_grub on the / (root) partition I am not sure what it does.

---

### Post by skanger on 2017-07-28
What should I set them to then? I tried setting the EFI partition to boot, but the ESP flag was also set. The two are linked and the boot flag cannot be stet without ESP being checked as well.

The same applies to the ext4 Ubuntu partition. Setting it to boot checks the ESP flag. 

There was no change with the Ubuntu partition set to bios_grub. The laptop booted to the grub command line as before, so right now I have no flag set for the Ubuntu partition but there is no change.

Whatt to do?

---

### Post by oldfred on 2017-07-28
Keep boot flag on ESP, FAT32 partition.
With UEFI, boot flag is just the convention that parted/gparted use to assign the very long GUID that UEFI reads from a gpt partitioned drive to know where to look for the efi boot files.

You still need to reinstall grub, to get correct grub.cfg entry in the ESP to link to the full grub.cfg in your install.

Have you run Boot-Repair?

---

### Post by skanger on 2017-07-29
Yes, I ran boot-repair. It seemed to go well and it identified the Ubuntu partition as good. 

However it always ended with an error: ESP locked. The text file for the operation was very long. I can post it here. Other than the locked ESP message it seemed to me that the ESP/EFI and Ubuntu partitions were showing an empty entry. 

Apparently grub didn't re-install because of these errors and nothing has changed.

 At this point I might just quit and start over with 16.04 again. I had set up a number of customizations, shortcut keys, WINE, and installed most of the programs I need. I thought that 17.10 might make better use of the hardware but it didn't. I wanted to try an installed version to see if it would be faster but that was my mistake. I don't want to throw away all the time and care to set this laptop up, but I don't see myself understanding grub quickly. All of the files I created are easily available through a live Ubuntu session after mounting the Ubuntu partition on the drive so at least I won't lose them.

I will try any further suggestions you have. Probably you could fix it easily if it was in your hands as its very close to working but very far from working for me.

---

### Post by skanger on 2017-07-29
I read somewhere that the 1st partition should be reformatted as FAT32 and set to boot, so I did that and it went well. Then I ran boot-repair and it also seemed to be going well but I received a message that GPT is involved and a >1MB partition needs to be created, left unformatted and flagged as boot_grub. I went into gparted to do this and once again things seemed to be going well but the partition was not created and I could not set the proper flag. It appears that this is where the problem lies, and I received another error about lib-something. Apparently its at the disk level since I can't get this partition to go through and set its flag to boot-grub. Right now it boots into the shell.

---

### Post by oldfred on 2017-07-29
If your install is UEFI and your first partition is FAT32 with boot flag, then you have to boot flash drive in UEFI mode to repair in UEFI mode.

If it is asking for a bios_grub partition, then you have booted flash drive in BIOS/CSM/Legacy boot mode and are trying to convert/repair in BIOS boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
You should have two choices in UEFI boot selection of flash drive. But you can also tell which way you have booted by looking at first screen.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

