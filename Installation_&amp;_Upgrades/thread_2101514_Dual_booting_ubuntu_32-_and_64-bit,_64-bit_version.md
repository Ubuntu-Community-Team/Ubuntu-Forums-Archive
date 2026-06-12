---
title: "Dual booting ubuntu 32- and 64-bit, 64-bit version stuck at initramfs"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by spiffman on 2013-01-04
I am trying to set up a usb hard drive to dual boot 32-bit ubuntu and 64-bit ubuntu in separate partitions, while sharing a /home partition. The 32-bit version works fine (it was installed first), but after installing the 64-bit version in a new partition, I crash on booting into it.

The output is:

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/5cf1b255-86f8-4924-901b-ebe7662da8d5 does not exist. Dropping to a shell!

```

When I try to find the hard drive containing the ubuntu partitions, it does not show up in blkid, nor in any of the /dev/disk/by-X folders.

In dmesg i find the following problem which seems to indicate why I can't find the usb hard drive:

```

unable to enumerate USB device on port 2

```

Even though the 32 bit partition has no problem booting.

I ran update-grub and checked the entries, the only differences are that the 32-bit version has insmod gzio, recordfail, and sets the gfx.

---

### Post by oldfred on 2013-01-05
Are you using the grub in the hard drive to boot an install in a USB drive?

 Is system able to boot USB devices? Have you installed grub to USB drive and booted from that?


Separately, not sure you should share /home. Setting may be just enough different that it causes issues. If upgrading from 32 bit to 64 bit then you could reuse the /home as settings would just get updated.
I would suggest keeping /home inside / (root) and moving all data to a shared data partition, or splitting /home.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by efflandt on 2013-01-06
When running 2 systems like that, where did you put grub for each system?  One might step on the other if they both think they control grub in the same mbr.

When I ran both 32 and 64-bit systems from the same internal drive some time ago, I put the grub for one in the mbr and for the other on its primary partition.  That worked fine, I just had to boot the one that controlled the mbr and run sudo update-grub on that if the other one did kernel updates.  They did not share a /home.

When I installed both 64-bit Lubuntu and Ubuntu 12.04 on SD for my tablet PC with separate common /home partition, I put grub for Lubuntu in mbr of SD, but Ubuntu would not let me put grub on its partition, so I did not install any grub for Ubuntu.  Those both work fine with common /home partition.  I just have to do sudo update-grub from Lubuntu for Ubuntu kernel updates.

---

### Post by spiffman on 2013-01-07
Thanks for the responses, I definitely didn't pay much attention to where grub was being installed in this process...

I have one ssd in the laptop with windows 7, and I believe I installed grub for the 64-bit ubuntu in the MBR of this ssd by accident. Now when I open my boot device menu on startup, it shows ubuntu as an option even if the usb drive is not plugged in. 

The 32-bit version looks to have grub installed on the usb drive. When I run grub from the usb drive, I can boot into the 32-bit version just fine.

I ran update-grub from the 32-bit ubuntu, and it recognized the 64-bit installation. When I boot from the usb drive's grub and choose the 64-bit ubuntu, that's when I get the initramfs screen.

Should I install grub on the primary 64-bit ubuntu partition then, and try to remove it from the SSD MBR? Is there a safe way to remove grub from the SSD MBR while retaining the windows entry?

---

### Post by oldfred on 2013-01-07
Just to be sure of what is where:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by spiffman on 2013-01-07
Awesome, I'd never played with boot-repair but this is quite handy.

[Boot-info output]("http://paste.ubuntu.com/1508049/")

Also, doing some further drilling I found that the ubuntu entry in the boot device menu is actually an EFI variable (not in MBR), so am currently setting up a UEFI live USB to use efibootmgr to remove the faulty entry.

---

### Post by oldfred on 2013-01-07
You have your SSD in UEFI mode and your hard drive in BIOS mode? The only way to boot either system is from UEFI menu and change from UEFI to BIOS each time. I believe UEFI & BIOS write system parameters differently so you cannot chain boot from an Ubuntu BIOS boot to a UEFI Windows.

The UEFI may have confused your second install? All systems really need to be installed in either UEFI or BIOS.

But you hard drive is MBR and if you want UEFI you need gpt and the first partition as the efi partition.

---

### Post by spiffman on 2013-01-07
After installing grub on the 64-bit partition, I was able to boot into both with no problems :-) thanks all.

oldfred, since my ubuntu installations are in BIOS, can/should I change them back to UEFI to keep everything consistent? How would I change this?

---

### Post by oldfred on 2013-01-07
At this point it is not easy to change. There is software to convert MBR to gpt, but you need the efi partition to be first or at least near first on the drive. You still would need a full backup which you should really have anyway, convert to gpt, move first partition to the right to make a 300MB efi partition. Might just be easier to buy a new drive? Or live with having to go into UEFI/BIOS to reboot. 

I still have BIOS and all new drives are now gpt with space for an efi partition but using a bios_grub partition to boot from gpt drive into BIOS. That way I should be able to easily move my newer drives to the new system I was buying last summer. :)

---

