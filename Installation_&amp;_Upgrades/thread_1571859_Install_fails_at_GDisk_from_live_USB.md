---
title: "Install fails at GDisk from live USB"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by a5sketchbook on 2010-09-10
I'm having big problems trying to install Ubuntu 10.04 (32bit) on a new computer - nothing has ever been on it so it's fresh as a daisy.

It has no optical drive so I created a live USB installation through Unetbootin, which starts up no problem and I can start the installation to the hard drive.

After picking my keyboard layout in stage 3, the installer hangs. A crash message appears in the top right (but nothing overtly obvious happens and I can close the installation window easily). Trying to start GParted from the applications menu also results in the same crash error.

Looking around I thought this may be some disk formatting issue so I created a new ext4 partition for the whole hard drive (160GB) with the disk utility which went without a hitch but hasn't made any difference.

I can however start GParted from the command line (gksudo gparted) into the partition created above just fine but still no dice when opening from the applications menu, it just pops up, starts to read then closes.

Just to check if this was Ubuntu specific I also tried running Fedora off another USB and the same thing happens, the installer hangs when reading the hard disk.

Looking around this seems like a common problem with many users finding the same issue (there's a 4 page topic about it going back 12 months) but unfortunately I'm unable to see a solution or hints at what the problem may be. Any ideas... possibly something very simple?

---

### Post by oldfred on 2010-09-10
If it is a new system then I am suspicious of BIOS settings.  I have saved a few comments on things to review.

BIOS should be set for IDE compatibility mode

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happend to set it on)

---

### Post by a5sketchbook on 2010-09-10
It's definitely to do with the USB stick.

If I remove the stick it will proceed without a hitch. Obviously though I cannot actually install the system as the whole OS is corrupted when the stick is taken out and re-entered but it's a start...

Does this provoke any ideas about what to do?

Can I copy the contents of the USB stick to a small hard drive partition or something?

---

### Post by oldfred on 2010-09-10
It sounds like the install on the Flash drive or the flash drive is defective. I would first redownload and reinstall to the flash. If not I would try another flash drive.

If you want to create a 1GB FAT32 partition (I would put it at the end of the drive & I think it has to be primary) you can install grub2 and the ISO to the hard drive. You can either boot from the hard drive or the USB flash drive then. You might want to set up all your partitions in advance. I download gparted and use it separately from the gparted that is on the install ISO. How big is your drive and what partitioning plan do you have?

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)


MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by a5sketchbook on 2010-09-12
I tried several USB sticks and several different downloads which unfortunately had no effect.

However, I have installed 9.10 flawlessly then performed the automatic upgrade.

This is a very common issue users are having so I hope it is fixed soon.

---

### Post by ronparent on 2010-09-12
I always like to run the live cd before I install. Defective install media will often show up there as well. But more, importantly, any issue that is likely to prevent booting or installation usually shows up and you can debug before you install. Editing the menu boot line by removing 'quiet splash' will allow the boot process to write to the screen. Often where it stops give you some clue of where the boot glitch is. By and far most installation will happen quite easily. If some rare hardware feature causes pain, the process for finding can it self be tedious.

---

