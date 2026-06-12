---
title: "Installing Ubuntu on UEFI System"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by mitchell8 on 2014-03-19
I am trying to install and run Ubuntu (12.04.4 LTS) on my ocmputer (64-bit). It defaulty came with Windows 8 and I formated the hard drive and installed Windows 7 on it. Now I am trying to dual boot Windows 7 and Ubuntu. I have gotten to the point where in the GRUB2 bootlader I can see many different choices. I can pick the Windows option and boot Windows, but if I pick the Ububntu option, the screen just goes to the really dark purple color. If anyone can help please do!! Here is the past.ubuntu website from the boot recovery I used while running Ubuntu from the USB i have put the Ubuntu iso on: [http://paste.ubuntu.com/7116564/](http://paste.ubuntu.com/7116564/)

Please help!
-Thanks

---

### Post by bookrt on 2014-03-19
Go into BIOS with USB Ubuntu disk inserted. There should be options to boot the USB stick in EFI or regular. Select EFI, then redo the installation. It will then install normally in EFI mode. In my opinion this will be easier than doing the boot repair.

---

### Post by slooksterpsv on 2014-03-19
What graphics do you have kin the computer?

When in grub, highlight Ubuntu, press the e key and go to the line that says quiet, remove the word quiet and put in nomodeset, press F10 to boot and see if that makes any difference.

---

### Post by mitchell8 on 2014-03-21
OK I have now have pretty much started from scratch again. I have figured out that my Windows 7 install I'm pretty sure is installed in legacy mode, not EFI. If I want to now dual boot Ubuntu now, what s the best way to do it? If anyone can give me a link to a step by step way to install Ubuntu alongside Windows 7 in legacy mode, it would be greatly appreciated.

-Thanks

---

### Post by slooksterpsv on 2014-03-21
If you boot into the installation of Ubuntu it'll give you the option to install alongside Windows 7.

Now here's the kicker, GRUB will be required to boot into Windows 7 from that point on until you either reinstall Windows 7 or restore the MBR for Windows 7.

Best thing to do is use Windows 7 and shrink down your disk in:

 diskmgmt.msc

use the search/run command to execute that app. If it's going to be on the same drive as drive C:, right-click and choose shrink. Shrink by amount you want for Ubuntu (60GB is sufficient for me personally) and let Windows resize it. Leave that partition empty. Now just boot from the LiveCD and install.

---

### Post by mitchell8 on 2014-03-21
I tried this and the purple screen still is on there. I have the integrated Intel HD 4000 graphics.

---

### Post by slooksterpsv on 2014-03-21
press CTRL+ALT+F2 - it should take you to a command line interface; if you've installed the system already you'll need to login with your username and password; if this is off of the livecd you should be logged in automatically.

To login, if you're not, type in your user name e.g.: during install if your name was John Doe, your username would default to john. When you press enter, it'll prompt for your password, it won't show as you type it, so you'll need to type it in and press enter.

Once your to the CLI type in:

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

Now type in:
sudo start

If you got into the GUI let me know, if not try this one:

sudo lightdm

---

### Post by fantab on 2014-03-21
> **mitchell8 said:**
> OK I have now have pretty much started from scratch again. I have figured out that my Windows 7 install I'm pretty sure is installed in legacy mode, not EFI. If I want to now dual boot Ubuntu now, what s the best way to do it? If anyone can give me a link to a step by step way to install Ubuntu alongside Windows 7 in legacy mode, it would be greatly appreciated.


```
parted -l:

Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  106MB  105MB   fat32           EFI system partition          boot
2      106MB   240MB  134MB                   Microsoft reserved partition  msftres
3      240MB   645GB  645GB   ntfs            Basic data partition
4      645GB   646GB  499MB   ext4
5      646GB   666GB  20.0GB  ext4
6      666GB   744GB  78.0GB  ext4
7      744GB   750GB  6000MB  linux-swap(v1)
8      750GB   750GB  99.6MB                                                bios_grub 
```

The output of 'parted -l' shows that your HDD has GPT table.
Windows can boot from GPT disk only in EFI mode.
So your Windows is booting in EFI... this is also manifested in the contents of the EFI System Partition [ESP]:

```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/bootx64.efi /ubuntu/grubx64.efi 
                       /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/refind/refind_x64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi /Microsoft/Boot/bootmgfw.efi 
                      [B] /Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi [/B]
                       /EFI/refind/drivers_ia32/btrfs_ia32.efi 
                       /EFI/refind/drivers_ia32/ext2_ia32.efi 
                       /EFI/refind/drivers_ia32/ext4_ia32.efi 
                       /EFI/refind/drivers_ia32/hfs_ia32.efi 
                       /EFI/refind/drivers_ia32/iso9660_ia32.efi 
                       /EFI/refind/drivers_ia32/reiserfs_ia32.efi 
                       /EFI/refind/drivers_x64/btrfs_x64.efi 
                       /EFI/refind/drivers_x64/ext2_x64.efi 
                       /EFI/refind/drivers_x64/ext4_x64.efi 
                       /EFI/refind/drivers_x64/hfs_x64.efi 
                       /EFI/refind/drivers_x64/iso9660_x64.efi 
                       /EFI/refind/drivers_x64/reiserfs_x64.efi 
                       /EFI/refind/tools_ia32/gptsync_ia32.efi 
                       /EFI/refind/tools_x64/gptsync_x64.efi

```

Or those entries can be from 'erased' Windows 8. And if they are left overs from Win8 then those entries are being run by Grub but there is no corresponding OS to boot.

This also shows that you are using or used 'rEFind' Boot manager. It is suggested that you either use Grub or rEFind, and not both.

I would suggest that you try ubuntu latest 13.10. The latest versions of Ubuntu support 'newer' hardware techs better.
Remember to install Ubuntu in U(EFI) the ubuntu install media has to be booted in UEFI mode only.

If you think Winodows may not have been installed properly then try re-installing it again.
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

And one more thing, remove the 'bios_grub' flag on /dev/sda8 or your 8th partition, this partition is needed only to boot Linux OS from a GPT disk in 'BIOS/Legacy/CSM' mode. This could interfere in the proper Grub install.

---

