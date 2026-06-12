---
title: "GRUB2 repair help requested!"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by Jared_Clark on 2016-05-24
I don't really know what happened. Laptop has been fine for a year, dual booting Windows 10 and Ubuntu 16.04. I went to boot it up and it seems that GRUB may be hosed. I have been trying to use boot-repair and refind to no avail. I do not have a DVD drive, but I do have a functioning UEFI bootable copy of 15.10 that I have been using to get into the system and try to repair. Here's a link to the boot-repair diagnostics:

[http://paste.ubuntu.com/16658905/](http://paste.ubuntu.com/16658905/)

Any tips are greatly appreciated, hoping it's just something I am overlooking.

---

### Post by oldfred on 2016-05-24
You are missing your ESP - efi system partition.

Your fstab has this, which Boot-Repair comments out entry with no permissions (0077) and adds one with defaults so edits can be made to ESP.
>  # /boot/efi was on /dev/sdb1 during installation
#UUID=80AA-9359  /boot/efi       vfat    umask=0077      0       1 
 UUID=80AA-9359    /boot/efi    vfat    defaults    0    1

 


But your blkid output shows no partition with UUID 80AA-9359
And it shows errors on sdb1

So I might try file checks on that partition which should be FAT32 if the ESP.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Normally grub only installs to sda's ESP, so your configuration is a bit unusual that you have the ESP on sdb. 
Did you have to manually set grub into sdb?
Most users cannot get grub to install at all without an ESP on sda.

Because no ESP found, Boot-Repair wanted a bios_grub partition for a BIOS boot. Best not to do that but fix ESP on sdb and/or add on sda an ESP.
Be sure to boot Ubuntu installer in UEFI boot mode.

---

### Post by Jared_Clark on 2016-05-24
Ok, so this is starting to make more sense now. I think I know *how* it happened, just need to get it fixed. So my laptop has an internal 16GB SSD. Before this happened, I had flashed a USB stick with a RetroPie image... you guessed it I had inserted a 16GB USB stick. Most likely something happened during that, that screwed up GRUB. It certainly *did* live on SDA1, and all my EFI files are there. SDB in this case I don't care if it has errors, it's not being used. 

As far as SDA not being flagged for ESP, it's because I was tinkering around with boot-repair and gparted and I was trying different flags. If memory serves the first time I looked at the partition it had no flags set, and I tried various ones.

---

### Post by oldfred on 2016-05-24
Do not know how drive order would change, unless because of the corruption UEFI does not make it sda?

ESP needs boot flag and FAT32, but if you reformat it, it will erase any data. 
Hopefully it is not a copy of your RetroPie and still has the .efi boot files & folders.

---

### Post by Jared_Clark on 2016-05-24
Thanks for the reply, but I am confused. I am pretty sure originally that SDB was how the laptop shipped with Windows 8. It's 16GB flash embedded in the laptop, and probably where the original OS booting information resided. I installed a new 250GB SSD which is SDA, and where both OSes currently reside. Obviously SDB got hosed and that must have been where my booting was coming from. So, I am still a bit confused. I should what, format that 16GB internal partition, flag it as boot/ESP, formatted to FAT32, and install GRUB2 to that?

 The files on /boot (SDA1) seem to be the legit ones, as grub.cfg has valid entries and is dated May 8th, probably the last time a kernel upgrade happened. Heck, I think that's when I did the upgrade to 16.04 from 15.10.

---

### Post by Jared_Clark on 2016-05-24
I am making progress but still a bit confused. I was able to install grub to SDB1 after formatting a slice on it with FAT32, and marking it as boot as you suggested. Then, I was able to run boot-repair and select SDB as the target for boot/efi. This did indeed let me boot back into my linux partition correctly. No windows partition shows up as of yet, but maybe I need to run a windows BCDedit or something, as 'update-grub' now only looks to SDB where the only apparent EFI entries are for Ubuntu now? As I said before, it's confusing because it seems that the correct files lived in /boot on the SDA drive, but obviously SDB was critical to the boot process, at least here.

[http://paste.ubuntu.com/16664185](http://paste.ubuntu.com/16664185)

---

### Post by oldfred on 2016-05-24
You are still showing gpt errors.

Do not confuse the old BIOS boot flag with a new UEFI/gpt boot flag. Gparted just uses the convention of a boot flag to set the FAT32 partition as the ESP. It actually is a very long GUID code. 
In BIOS/MBR Windows used the boot flag in MBR to know which NTFS primary partition had the rest of Windows boot code. Grub did not use boot flag.
With UEFI/gpt most of the start up code is in the ESP, but Ubuntu still has a /boot folder in the / (root) partition with kernels & rest of grub.

Windows only boots in UEFI mode from gpt partitioned drives. But you now have sdb1 with Windows efi boot files but drive is MBR(msdos) partitioned. 
While Linux installer does boot with most systems in UEFI mode from a MBR partitioned flash drive, some require gpt. And I think your sdb needs to be gpt partitioned for Windows to boot. 
I would first back up all the files in sdb as with UEFI you do not need to install boot loaders, but can copy files from one FAT32 partition to another.
Then either repartition and restore backup or use gdisk to convert to gpt from MBR.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You will have to reinstall grub as UEFI entry is for a MBR UEFI boot, not gpt.
 

    
You also added a boot flag to sda1. But that is your main Ubuntu install with ext4 formatting.
The ESP - efi system partition must be FAT32. If you want an ESP on sda, you have to create a new partition of 100 to 500MB, formatted FAT32 with boot flag.
Use gparted to remove boot flag from sda1. Some systems will not boot seeing that.

Not sure which drive this is from, but I would run gdisk repairs on both drives, but conversion of sdb will remove it, if that is the problem.
> Primary GPT is invalid, using alternate GPT.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 
    [http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

---

### Post by Jared_Clark on 2016-05-24
Excellent response, thank you. I at least now feel like I am learning something in the process. I won't have time to play again until later tonight, but I'll use your well formatted advice and go after it later and report back. Thanks so much for your time helping me out! Pretty sad that I've been in IT for 15 years, and still feel like a lost sheep when it comes to UEFI, at least in scenarios like this. Old dog and new tricks, I guess.

---

### Post by Jared_Clark on 2016-05-25
> **oldfred said:**
> You are still showing gpt errors.

Do not confuse the old BIOS boot flag with a new UEFI/gpt boot flag. Gparted just uses the convention of a boot flag to set the FAT32 partition as the ESP. It actually is a very long GUID code. 
In BIOS/MBR Windows used the boot flag in MBR to know which NTFS primary partition had the rest of Windows boot code. Grub did not use boot flag.
With UEFI/gpt most of the start up code is in the ESP, but Ubuntu still has a /boot folder in the / (root) partition with kernels & rest of grub.

Windows only boots in UEFI mode from gpt partitioned drives. But you now have sdb1 with Windows efi boot files but drive is MBR(msdos) partitioned. 
While Linux installer does boot with most systems in UEFI mode from a MBR partitioned flash drive, some require gpt. And I think your sdb needs to be gpt partitioned for Windows to boot. 
I would first back up all the files in sdb as with UEFI you do not need to install boot loaders, but can copy files from one FAT32 partition to another.
Then either repartition and restore backup or use gdisk to convert to gpt from MBR.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You will have to reinstall grub as UEFI entry is for a MBR UEFI boot, not gpt.
 

    
You also added a boot flag to sda1. But that is your main Ubuntu install with ext4 formatting.
The ESP - efi system partition must be FAT32. If you want an ESP on sda, you have to create a new partition of 100 to 500MB, formatted FAT32 with boot flag.
Use gparted to remove boot flag from sda1. Some systems will not boot seeing that.

Not sure which drive this is from, but I would run gdisk repairs on both drives, but conversion of sdb will remove it, if that is the problem.


       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 
    [http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

Looks like I am taking steps backward. Here is the current state of the mess I am making.

[http://paste2.org/88HFBHbw](http://paste2.org/88HFBHbw)

After dd'ing the first 512 of sdb to get rid of MBR, and clearing/installing fresh GPT onto it, I simply could not get boot-repair to run and install grub onto sdb. I consistently got 'GPT detected. Please create a BIOS-Boot partition'
I also checked sda for GPT errors with gdisk and seemed to be OK. Out of frustration, I resized my /home partition to allow a slice to be formatted to FAT32 and flagged as bios_grub (sda). This did allow me to run boot-repair against sda, but system will not boot. I did back up what was originally on sdb. I see some errors regarding the Windows installation.

*edit* I changed my bios options to allow to boot either legacy or UEFI, and it allows Ubuntu to boot now in BIOS mode, I checked using this: ```
[COLOR=#111111][FONT=Consolas]#!/bin/bash
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas][ -d /sys/firmware/efi ] && echo UEFI || echo BIOS[/FONT][/COLOR]
```

Still no Windows option but is that due to errors? an 'update-grub' from within the booted BIOS ubuntu OS doesn't find anything other than /boot/vmlinuz* images. Sorry, maybe I'm just not seeing the obvious solution.

---

### Post by oldfred on 2016-05-25
The bios_grub flagged partition must be unformatted.
The ESP - efi system partition is FAT32 partitioned with boot flag.

I actually put both an most new gpt partitioned drives particularly larger flash drives, so I can configure for either UEFI or BIOS or later change.
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

But UEFI & BIOS are not compatible. They write data to hard drive differently for operating system to use to boot with.
Or once you start booting in one mode you cannot change.
And if booting to grub in BIOS mode, you the cannot from grub boot Windows in UEFI mode. You can then only dual boot from UEFI boot menu or one time boot key like f10 or f12, check manual.

Best to always have all systems installed in same boot mode. Avoids confusion and allows you to dual boot from grub menu.
But how you boot install media is then how it installs for both Windows & Ubuntu. So if Windows already UEFI, you want to boot Ubuntu installer in UEFI boot mode.

Boot-Repair can convert a BIOS install of Ubuntu to UEFI if on gpt partitioned drive. But you must have ESP - efi system partition. It actually uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI) which also changes some other settings.
 
Errors on sda6 (bios_grub) or sda4 (Windows system reserved) are normal as both partitions are unformatted and should be unformatted.

But now sdb is totally missing, probably needs chkdsk or dosfsck as in post #2.

---

### Post by Jared_Clark on 2016-05-26
Hello again. Let me make sure I say firstly, I really appreciate you helping me out here. It's not too often that I feel completely stymied, especially considering all the answers are out there you just have to read and learn long enough to find them. Wife, 2 kids and a job though of course limit some of that time these days! Selfless help from strangers is quite uplifting. :) Anyway, I did as you suggested and have the BIOS as well as the EFI partitions installed onto sda, sdb unformatted as I really don't care about that at this point. I am now booting correctly from the hard drive into Ubuntu in UEFI mode, as I was originally. My Windows 10 data partition mounts, I can see all my info there, users and whatnot. boot-repair/grub2 still cannot seem to be able to see/add the Windows OS back into the booting menu. Any ideas whenever you have a free moment?

[http://paste2.org/yskLfFet](http://paste2.org/yskLfFet)

---

### Post by oldfred on 2016-05-26
Boot-Repair seems to want to default to a BIOS install of grub. Not sure if that is because it sees the bios_grub partition or some other reason.
But if you have run this and grub2's os-prober does not see the Windows efi boot files something still must be wrong with the ESP.
sudo update-grub

You do show the typical Windows efi boot files that the Summary report normally shows.
But you do not show any Windows UEFI boot entry. This shows lots of entries, but not the typical Windows entry:
sudo efibootmgr -v

UEFI suggests the ESP be the first partition, but Windows typically makes it the 2nd or 3rd. And yours does not look like it is so far into drive to be an issue, and if you can boot Ubuntu in UEFI mode it must be ok.

Often /EFI/Boot/bootx64.efi which is a fallback or hard drive boot entry is a copy of Windows .efi boot file. Boot-Repair when run with 'Use the standard EFI file in advanced options will back up that file and make it a copy of /ubuntu/shimx64.efi. Then you can use a hard drive entry to boot Ubuntu for those systems that only boot Windows.

You show several hard drive boot entries, but I do not know if UEFI or BIOS. I might from UEFI or one time boot key like f10 or f12, check manual or may show on first UEFI start up screen try to boot those entries.
About the only way to tell what bootx64.efi is, is just to compare sizes with shimx64.efi and with Windows /EFI/Microsoft/Boot/bootmgfw.efi.

If hard drive entries do not work, we can try manually adding a Windows UEFI boot entry so you can directly boot from UEFI. Probably best to use a Windows repair flash drive to run repairs which should also fix it.

Of course you do this when Windows is working. If you have access to another Windows system with same version or newer Windows 10, you should also be able to use that. Just must be 64 bit version of Windows. Or if you have a Windows install flash drive or DVD, that also should have safe mode or repair console.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

---

### Post by Jared_Clark on 2016-05-26
I just made a UEFI bootable Windows 10 USB stick. Would your suggestion be to try to repair the windows boot using the Win10 environment then? I was fairly certain that both OSes were installed and running in UEFI mode.

---

### Post by oldfred on 2016-05-26
Yes that should be the preferred way to repair Windows.
But it probably will make Windows the default boot in UEFI.

You can go into UEFI and change boot order. And some Windows updates may periodically reset order again, so best to know how to reset.

You should also be able to boot Ubuntu from one time boot key anytime.

And you should be able to reset boot order with efibootmgr.

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
Check order, example with 2,1 is just an example, use your desired boot order.
sudo efibootmgr -v
sudo efibootmgr -o 2,1
Launch EFI Shell from File System Device
[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell
[/URL]
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 

[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell"]
[/URL]

---

### Post by Jared_Clark on 2016-05-26
I had a small amount of time to tinker today. I managed to do a bcdedit repair, (after several errors about c:\boot not being found) but it looks like it used the flash drive itself for the target, as now if I boot the laptop with the flash drive in, and BIOS set to boot UEFI only flash drive first it boots into Windows 10 with my existing data. Also it's strange but if I do the one time boot f12, it will never boot the device. It's like it has to boot up with looking at the boot order. (This behavior is the same with an Ubuntu or Windows flash drive) I suppose it's a matter of figuring out exactly how to repair the stupid boot record using the proper partition on sda and not the usb flash drive, lol.

---

### Post by oldfred on 2016-05-26
I still might try running either chkdsk from Windows or from Linux:
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

And see if your standard efi boot files appear.
Your new ESP on sda, shows no Windows efi boot files or BCD which are normally there.

I would also backup the ESP on sda, and if you get ESP on sdb to work, back that up separately.
You may be able to copy BCD to sda's ESP, but Windows has lots of support files that script does not show.
And external devices boot from /EFI/Boot/bootx64.efi which for Windows is usually just a copy of bootmgfw.efi.

---

### Post by Jared_Clark on 2016-05-26
I will try, but honestly I don't have much hope. I mean, I imaged over it accidentally, and then deleted partitions and reformatted. I guess I misunderstood you as I thought the game was to try to get everything on sda using new partitions, and not trying to make sdb work as it must have before. Currently sdb is unallocated, GPT. [COLOR=#000000]sudo dosfsck -t -a -w /dev/sdb1 returns a 'open: No such file or directory.' [/COLOR][COLOR=#000000]sudo dosfsck -t -a -w /dev/sdb returns a 'Logical sector size is zero.'

Is there anythnig I can copy from the now apparently functioning flash drive over to sda?

*edit*

I did run gpart recovery on sdb, all it found was the previous retropie installation that I fubared over what was originally there.[/COLOR]

---

### Post by oldfred on 2016-05-26
I was hoping to find the missing files for Windows UEFI boot.
Not sure why Windows repairs would not install UEFI boot files. Not sure with Windows but with Ubuntu you have to be sure to always boot in UEFI mode.
I would expect that you must boot Windows repair disk in UEFI mode to get UEFI repairs.

---

### Post by Jared_Clark on 2016-05-27
Finally, success. In the end it was a whole lot of me just not really understanding the UEFI boot process. Between your help and lots of reading, I have a much better understanding of how the magic works and should help troubleshooting other stuff in the future!

Once I realized that I had done the bcd repair using the d: drive as the target (which was that usb stick loaded) and could boot into windows with the drive installed, I knew that I simply wasn't getting the bcdboot target to point to the right place. In retrospect, pretty simple. I didn't have the EFI partition mounted! For anyone that comes across this thread later..

Boot into Windows recovery UEFI mode from a USB stick, open a command prompt.
diskpart
select disk 0 (in this case my sda)
select partition 7 (where my EFI home lives)
assign (pick a drive, or just let it choose. e:)

then it's a matter of changing how the typical boot repair process works because you're not pointing to c: (where the typical location would be in a MBR scenario)

attrib -s -h e:\EFI\Microsoft\Boot\BCD
del e:\EFI\Microsoft\Boot\BCD
bcdboot c:\windows /s e:

after all that, booted back into Ubuntu and performed a boot-repair, made sure to point to the separate partition for EFI, and purge-reinstall of grub. 


Huzzah. Thanks so much for your time, hopefully this can help someone else later!

---

### Post by oldfred on 2016-05-27
Glad you got it working.

---

