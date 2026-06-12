---
title: "Boot issue installing from another Mac"
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by modica-anto on 2018-05-24
I'm in a bit of a complicated situation regarding an installation of Ubuntu on a Dell laptop. I managed creating a bootable live USB for Ubuntu 18.04, but for some reason the USB ports on the Dell bootloader won't show up (they are listed in the BIOS's settings, but not in the boot device selection screen). The live USB works (I tested it on my Mac), so I decided to try another way. I took out the Dell HDD and connected it to my Mac via SATA-USB adaptor, live booted Ubuntu on my Mac and started the installation on the external HDD. This got me a working installed version of Ubuntu, but when I put the HDD back in the Dell computer I'm still unable to boot into Ubuntu since it's missing Grub (which is automatically installed onto the Mac's internal HDD, for some reason). Any suggestion on how to solve this?
Thanks in advance,

Antonino

---

### Post by yancek on 2018-05-24
Does the Dell have any operating system on it prior to trying to install Ubuntu?
Is this a newer EFI capable machine.  If it is EFI, are you booting Ubuntu in EFI mode?  Ubuntu documentation on EFI at the link below.
Some systems list usb devices under hard drives, have you looked there?
If the Dell is less than about 10 years old, it should boot from a usb.  Have you booted a usb device on this machine in the past?  
Macs have been using EFI for years.  I've never used one so am not sure about the process.  If it is similar to PC's, you will have a separate EFI partition and Ubuntu Grub will install some of it's files in a separate directory on that partition.  These files are necessary to boot Ubuntu EFI and therefore it won't work on the Dell. 

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by modica-anto on 2018-05-24
The Dell doesn't have any OS installed; in fact, the HDD from the Dell has been formatted completely, and I did a clean Ubuntu install through the SATA adapter from the Mac.
But I'd prefer to install directly from the Dell computer, since as you said the partitioning is going to be specific for it. I've been trying to figure out why the USB port are not showing up.
In this ([https://imgur.com/a/dcO94wC](https://imgur.com/a/dcO94wC)) picture you can see what I get when I boot the Dell, I cannot define what the Removable Drive is, and also there's no physical DVD drive on the laptop.
Any clue?
[IMG]https://imgur.com/a/dcO94wC[/IMG][IMG]https://imgur.com/a/dcO94wC[/IMG]

---

### Post by oldfred on 2018-05-24
External drives only boot from an ESP - efi system partition and /EFI/Boot/bootx64.efi.
Full install of grub in UEFI mode installs to ESP and boots from /EFI/ubuntu and uses a grub.cfg with configfile (UUID & partition) to find full grub.cfg in your actual install.
So and install to a second drive normally does not even create an ESP (FAT32 with boot flag) partition on the second drive. You have to manually create that first and use Something Else install option to add / (root) and optionally /home. Swap partition not now required.
Then you techinically can copy /EFI/ubuntu from internal drive to second drive on Mac and have a drive that will boot internally. If you also copy all of /EFI/ubuntu into /EFI/Boot on second drive and rename shimx64.efi or grubx64.efi to bootx64.efi, it should boot directly from UEFI as external drive or using internals drive's fallback or hard drive direct boot entry.

Better easier just to install directly to Dell.
I just installed to my Haswell based Dell Small Form Factor system. I did turn secure boot off. I know it used to be that Dell wanted legacy on, but you still  booted in UEFI mode. Almost everyone else has to have legacy off to be able to boot in UEFI mode at all. I noted that I did not have legacy on. But have updated UEFI from Dell.
And I do have a setting for full USB support which enables booting from USB ports.

---

### Post by modica-anto on 2018-05-25
I really could not find a way to boot from USB drives on the Dell, apparently the BIOS version does not allow it.
I'm now trying to install a windows version from another windows computer, and once I'll have it running on the Dell I'll be able to perform a BIOS update and then to install Ubuntu from a live USB.
If this doesn't work I'll try, as you said, to manually create the boot partition on the external drive. Only problem with that is that when I tried manually creating a partition table on the drive before installing Ubuntu, every time I created the first partition (wether primary or logical) GParted left exactly 33MB before it, eventually stopping me from continuing the installation and returning an error regarding the alignment of the partitions and performance issues.

---

### Post by oldfred on 2018-05-25
Did you set it to use gpt first in gparted?
        Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sdX mklabel gpt #where sdX is your drive sdb, sdc etc It may erase drive, so be sure you use correct drive.

What model Dell?
Have you updated UEFI?

---

### Post by modica-anto on 2018-05-25
I already set the partition table to be gpt. I think the problem was something else: the HDD I was using was taken from a Macbook Pro, and apparently it had an Apple Recovery Partition that was not readable by any of my systems. I ended up borrowing a Windows computer from a friend and doing a drive wipe with the Windows partition manager. Now I managed to install a Windows system on it and it's up and running, but the BIOS still cannot boot from USB for I don't know what reason. Do I have to enable some advanced boot menu in Windows to be able to do that?

---

### Post by oldfred on 2018-05-25
My Dell is a small form factor desktop with Aptio UEFI and Haswell Intel CPU, so a few years old.

But I have at least two settings specific to USB ports.
In Advanced and USB configuration I have to enable both front & back USB ports.
And in Boot I have to enable USB Boot Support.

Since a laptop, your settings & which UEFI screen those settings are on, may vary. But if a Dell I would expect very similar settings.

---

