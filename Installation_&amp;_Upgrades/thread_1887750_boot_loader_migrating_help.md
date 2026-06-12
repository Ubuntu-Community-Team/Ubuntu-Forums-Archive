---
title: "boot loader migrating help?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by henry9419 on 2011-11-27
i run my computer in a dual boot setup with ubuntu 11.04 and windows 7, when i booted i was brought to the ubuntu bootloader screen and prompted to choose an OS, but the loader was on the harddrive with windows 7 on it, and i recently had to reinstall and i havent been able to access my ubuntu files...is there a way to copy the entire installation into a fresh installation some how? settings, programs, files, everything? or can i simply reinstall the ubuntu loader onto the drive with windows again somehow?

in short the drive with ubuntu11.04 wont boot because the bootloader was installed on a drive that was recently wiped

---

### Post by drs305 on 2011-11-27
I'll use sda as your Windows drive and sdb as your Ubuntu drive. Change as necessary. I think what you said you did was wipe Windows from sda and reinstall.

If the Ubuntu files, including the boot files, are still intact:
Boot an 11.04 LiveCD.
Mount your Ubuntu partition.
Install Grub to the MBR of sdb, leaving the sda MBR containing Windows information.
Change the BIOS boot order to boot sdb first.

After booting the 11.04 LiveCD, open a terminal. I'm using sdb1 as your Ubuntu partition. Change to the correct drive and partition designations. Don't use the partition designation in the second command.

```
sudo mount /dev/sd**b1** /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo umount /dev/sdb1
```
Reboot, and make sure sdb boots first.

The advantage in doing it this way is that you can change the boot order back to sda if Grub fails and you need to boot Windows, as you will not have overwritten the Windows bootloader when you install Grub to sdb.

---

### Post by henry9419 on 2011-11-27
> **drs305 said:**
> I'll use sda as your Windows drive and sdb as your Ubuntu drive. Change as necessary. I think what you said you did was wipe Windows from sda and reinstall.

If the Ubuntu files, including the boot files, are still intact:
Boot an 11.04 LiveCD.
Mount your Ubuntu partition.
Install Grub to the MBR of sdb, leaving the sda MBR containing Windows information.
Change the BIOS boot order to boot sdb first.

After booting the 11.04 LiveCD, open a terminal. I'm using sdb1 as your Ubuntu partition. Change to the correct drive and partition designations. Don't use the partition designation in the second command.

```
sudo mount /dev/sd**b1** /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo umount /dev/sdb1
```Reboot, and make sure sdb boots first.

The advantage in doing it this way is that you can change the boot order back to sda if Grub fails and you need to boot Windows, as you will not have overwritten the Windows bootloader when you install Grub to sdb.
uhhhh yeah ill figure it out another day...i just want to use the computer right now, so yeah...ill figure out how to do the above another time...

---

### Post by drs305 on 2011-11-27
> **henry9419 said:**
> uhhhh yeah ill figure it out another day...i just want to use the computer right now, so yeah...ill figure out how to do the above another time...

Once you boot to the LiveCD Desktop, it will take about a minute or two. It really isn't as complicated as it may appear...

---

### Post by henry9419 on 2011-11-28
ok, and i guess in a similar way i could set it up to boot only ubuntu, without the windows installation???

---

### Post by drs305 on 2011-11-28
> **henry9419 said:**
> ok, and i guess in a similar way i could set it up to boot only ubuntu, without the windows installation???

If you install Grub on sdb and sda still has a working Windows OS, Grub will display both. You could hide Windows from the menu via several methods if you really wanted to.

If Grub is on sdb and you install/reinstall Windows to sda it will not overwrite the sdb MBR. If you install Grub on sda and reinstall Windows it will force the Windows bootloader to be used (with only a Windows option) but you can easily restore Grub at that point by making sure sdb boots first.

---

### Post by henry9419 on 2011-11-29
> **drs305 said:**
> If you install Grub on sdb and sda still has a working Windows OS, Grub will display both. You could hide Windows from the menu via several methods if you really wanted to.

If Grub is on sdb and you install/reinstall Windows to sda it will not overwrite the sdb MBR. If you install Grub on sda and reinstall Windows it will force the Windows bootloader to be used (with only a Windows option) but you can easily restore Grub at that point by making sure sdb boots first.
ok right now im at this point i have two hard drives, one 500 with a fresh installation of 10.04 that can boot, and an 80gb hard drive with 11.04 and no MBR or grub as far as i know, i also have a live cd of 10.04 and a sd card with 11.04 that should be bootable, but it isnt, ive been trying to copy the MBR and grub onto the drive with 11.04 for idk a few hours now maybe with no success...i have loads of important files and programs and settings on this installation that are really important and i need some more detailed information on how to get the 11.04 installation up and running again, and at this point idgaf about even having a windows installation available beyond wine so please help!!!

---

### Post by drs305 on 2011-11-29
Part of the problem could be that you are trying to use a 10.04 LiveCD to update the Grub of 11.04. The earlier Ubuntu uses Grub 1.98, and the 11.04 version uses Grub 1.99, and the LiveCD for one can't be used to update the files of the other.

I'm only logged on for a few minutes but I'll try to cover a couple of options. 

Can you have both drives connected and running at the same time? If so, you can boot your 10.04 and mount your 11.04 partition to access the files. 

To just access your 11.04 files, I'll assume they are on the first partition of the sdb drive. Change if they are not on sdb or on another partition:
```
sudo mkdir /mnt/myfiles
sudo chown -R <yourusername>: /mnt/myfiles
sudo mount /dev/sdb1 /mnt/myfiles

```

To install or repair Grub 2 (1.99) to your 11.04 drive, you will need an 11.04 or 11.10 LiveCD.

If you can have both drives connected at the same time, download/run the Boot Info Script from 10.04. Post the contents of the RESULTS.txt it generates. The link to the script page is the "BIS" link in my signature.

If you can get a copy of the 11.04 or 11.10 LiveCD, install the Boot Repair app and see if that can fix your 11.04 Ubuntu installation. I'd disconnect the other drive while attempting the let Boot Repair fix things. Clicking the "Boot Repair" link in my signature line will provide more information.

---

