---
title: "Installing Ubuntu - SSD not detected"
date: 2019-10-07
forum: Installation &amp; Upgrades
---

### Post by robt800 on 2019-10-07
Hi,

I'm trying to install ubuntu on a thinkcentre M93p Tiny.  I've swapped out the old HDD for a SSD drive.  When I boot from the Ubuntu USB it does not detect the SSD...

Things I've tried:
1. gone into the BIOS and disabled secure boot (was already disabled)
2. took out the SSD - and reformatted it from windows to Ext3.
3. made sure the SATA is using AHCI in BIOS.

I've also downloaded rescatux and created a bootable USB, but I ain't too confident with it tbh as I'm still very new to Linux.

Help would be much appreciated!

Thanks

---

### Post by oldfred on 2019-10-07
Windows cannot format to ext3????
And you want ext4 for / in  most cases.

Did you update firmware for SSD, even if new?
And is UEFI for system the latest available?

If UEFI install, see link in my signature for general install instructions.
How you boot install media, UEFI or BIOS is then how it installs.
And UEFI will use gpt partitioning.

---

### Post by GhX6GZMB on 2019-10-07
For booting from a USB or DVD drive, either device needs to be set as boot device #1 in BIOS/UEFI. The installer will take care of the SSD afterwards.

---

### Post by robt800 on 2019-10-08
Thanks for the replies:

I used EaseUS to format the SSD to ext3.  unfortunatley I didn't have the option within EaseUS to format to Ext4.  If we think this could be compounding the issue I can come up with other ways to sort...

I didn't do the firmware - I'll get it done now.

UEFI is a bit new to me - never heard of it before, though been around BIOS for years.  I have set the SSD as the 1st boot device.  

I've also disabled CSM in the bios which appears to make the ubuntu USB boot up in UEFI mode as per here: [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://help.ubuntu.com/community/UEFI

Thanks
[/FONT]

---

### Post by robt800 on 2019-10-08
Further updates:
I've ran the boot repair disk from here: [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://sourceforge.net/projects/boot-repair-cd/

That detected the SSD - so I formated it to Ext 4 and ran its repair tool.  Said everything worked good.  However when I reboot using the ubuntu USB - that still doesn't detect the SSD...

Also I don't know if this is relevant or not - but when I do run ubuntu from the USB (obviously without installing) and go to files - other locations - it lists the internal flash memory in the thinkcentre.  Theres only 2GB of it and it doesn't have anything installed, but thought I'd mention it in case of its relevant,

Thanks
[/FONT]

---

### Post by oldfred on 2019-10-08
Just about everyone needs UEFI update & SSD firmware update.
I wonder if related to this:
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Microsoft & Linux have updated kernel & drivers, but UEFI also needs to be updated. May be related to something out of sync between the changes.

The Boot-Repair ISO is older, we normally suggest running it from inside the Ubuntu live installer.

For UEFI install the default is an ESP - efi system partition (FAT32 with boot flag & / (root) as ext4. Many like to have a smaller / & then large /home, but that  can only be done with the Something Else install option.
If you only have one ext4 partition it will not install the UEFI version of grub and you will not be able to boot. 

Having Legacy/BIOS/CSM mode off generally does not change the options on booting flash drive. You get two options, one UEFI and one that is not UEFI. 
How you boot install media is then how it installs and then settings in UEFI control which way install will boot. 
But if settings do not match the way you installed system will not boot.

---

### Post by robt800 on 2019-10-08
Thanks for the response - this is getting frustrating unfortunately!

So I've now tried:
1. Running Boot-repair from within the ubuntu live installer - however it couldn't detect the SSD...
2. I re-ran the boot-repair from the USB as from here I can run gparted and it finds the SSD.  I created a 500 mb partition to the left (shown graphically) - formatted it to FAT 32 and added the boot flag.  I left the remaining as an ext4 formatted drive.  I then re-tried the ubuntu installer and running ubuntu just from the USB.  Both wouldn't detect the SSD...

I can't understand how the boot-repair USB can see the SSD in gparted, but if I run Ubuntu from USB it cannot see the SSD from gparted??

Thanks

---

### Post by oldfred on 2019-10-08
Since the Boot-Repair ISO is older, it may not have all the latest updates.
And since UEFI is not updated it does not have all the latest updates and works.

While not your system, same issue resolved with UEFI & SSD firmware updates.
Lenovo Gamer Legion Y530
[https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675](https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675)

Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)

---

### Post by TheFu on 2019-10-08
boot-repair has trouble with all the complexities of possible boot configurations.  Also, if you don't have any Linux installed, there's no reason for it.  

For the last few years, the sole good purpose for boot-repair has been the "gather information" button.  Nothing else. Don't ask it to fix anything, unless the computer is BIOS/legacy, doesn't have UEFI or any GPT disks.

Linux installers are perfectly capable of putting an OS onto a completely empty disk/ssd or wiping a disk/ssd and putting the installation onto it.  That does require that the devices are working. Some really, really, new motherboards might not be completely compatible with Linux. OTOH, if the motherboard is over a year old and you've updated the motherboard firmware, then that shouldn't be an issue.

Exactly which SSD are you using?  Is it a Samsung or something else? Is is an NVMe or SATA?  Is the motherboard setup to use the interface-type that the SSD supports?  My motherboard has 6 SATA ports and 2 NVMe slots.  The NVMe is an M.2 form factor.  If either NVMe slot is enabled, then SATA ports 5 and 6 are disabled.  None of this is documented in the firmware, just in the motherboard manual.  Even then, it isn't clear in the manual.  I had to get clarification on the ROG support forums.

IBM is known for following standards.  If the machine has SecureBoot, then it is UEFI.

I don't see any mention of the specific version and release of Ubuntu being used.  If you are new, 18.04 is probably the release you need. Depending on the CPU, RAM, and GPU, you might want to avoid the default Ubuntu which uses Gnome3 and pick a lighter environment like XFCE, LXDE, or Mate instead. Any of those need fewer resources and less GPU than Gnome3.  I like the Mate GUI over the others these days - sorta like Mint- but I haven't looked at either recently.  I did run XFCE and LXDE for a few years and they are fine, light, DEs too.

None of this is probably all that helpful. Sorry.

---

### Post by rbmorse on 2019-10-08
I have a question. Is the target device for the Linux installation (your SSD) set up with a GPT partition table?  Isn't that a prerequsite for a UEFI installation?

---

### Post by TheFu on 2019-10-08
> **rbmorse said:**
> I have a question. Is the target device for the Linux installation (your SSD) set up with a GPT partition table?  Isn't that a prerequsite for a UEFI installation?

Only Windows requires GPT with UEFI.  Linux does not.  However, some UEFI BIOS will only work properly with GPT boot setups.  That is a bug in the implementation.

---

### Post by robt800 on 2019-10-08
> **TheFu said:**
> boot-repair has trouble with all the complexities of possible boot configurations.  Also, if you don't have any Linux installed, there's no reason for it.  

For the last few years, the sole good purpose for boot-repair has been the "gather information" button.  Nothing else. Don't ask it to fix anything, unless the computer is BIOS/legacy, doesn't have UEFI or any GPT disks.

Linux installers are perfectly capable of putting an OS onto a completely empty disk/ssd or wiping a disk/ssd and putting the installation onto it.  That does require that the devices are working. Some really, really, new motherboards might not be completely compatible with Linux. OTOH, if the motherboard is over a year old and you've updated the motherboard firmware, then that shouldn't be an issue.

Exactly which SSD are you using?  Is it a Samsung or something else? Is is an NVMe or SATA?  Is the motherboard setup to use the interface-type that the SSD supports?  My motherboard has 6 SATA ports and 2 NVMe slots.  The NVMe is an M.2 form factor.  If either NVMe slot is enabled, then SATA ports 5 and 6 are disabled.  None of this is documented in the firmware, just in the motherboard manual.  Even then, it isn't clear in the manual.  I had to get clarification on the ROG support forums.

IBM is known for following standards.  If the machine has SecureBoot, then it is UEFI.

I don't see any mention of the specific version and release of Ubuntu being used.  If you are new, 18.04 is probably the release you need. Depending on the CPU, RAM, and GPU, you might want to avoid the default Ubuntu which uses Gnome3 and pick a lighter environment like XFCE, LXDE, or Mate instead. Any of those need fewer resources and less GPU than Gnome3.  I like the Mate GUI over the others these days - sorta like Mint- but I haven't looked at either recently.  I did run XFCE and LXDE for a few years and they are fine, light, DEs too.

None of this is probably all that helpful. Sorry.

The SSD is a patriot one I had spare - 120GB.  I looked on their website to upgrade firmware on it, but couldn't see anything.

I have tried to update the BIOS/ UEFI - but the download for the CD ISO will not 'burn' to the USB using rufus or etcher - they both say the image isn't bootable...

not having much luck!

---

### Post by oldfred on 2019-10-08
Usually with UEFI there are 3 ways to install UEFI updates.
1. From Windows
2. Directly from UEFI using update file on a FAT32 partition.
3. DOS bootable (FAT32) flash drive with an executeable to upload update file.

I normally use 2 with my Linux systems.

Boot-Repair can do some repairs on UEFI systems, but all it really is doing is re-installing grub. And with UEFI you need to know if flash drive and then Boot-Repair is in UEFI or BIOS boot mode. It may default to installing or trying to install wrong version of grub.b There is grub-pc for BIOS and grub0efi-amd64 for 64 bit UEFI PC systems.

---

### Post by robt800 on 2019-10-08
Well - how frustrating!!!

BUT - got there in the end...

I created a DOS bootable USB with the UEFI update - but the system would not boot it!!! so I changed a setting in the BIOS - CSM (Compatibility support module) - enabled it.  This allowed me to boot from the USB, but interestingly the SSD drive were listed in the boot options!  I ran the UEFI update, but I already had the latest version.

So rebooted tried the ubuntu again and IT INSTALLED!!!

thanks for the pointers - glad to get there eventually!

---

