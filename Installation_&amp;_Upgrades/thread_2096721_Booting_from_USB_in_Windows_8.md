---
title: "Booting from USB in Windows 8"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by keeganxvx on 2012-12-20
I'm trying to install Ubuntu to dual boot both Windows 8 and Ubuntu. I tried using the WUBI installer, but I get the error for the missing or corrupted wubildr.mbr and I did a little research and read that WUBI doesn't really work for very new laptops (my laptop is an HP 2000 2b16nr, which came with Windows 8).

I've installed Ubuntu before with Windows 7 on my older laptop from a USB and it worked fine, but Windows 8 is ridiculous and I find any information on how to boot from a USB in Windows 8. The only info I can find is how to make a bootable USB with the Windows 8 iso for upgrading from 7.

So, does anyone know how to do this so I can get this thing installed?

Also, are there any problems people encounter when dual booting Windows 8 and Ubuntu due to the lack of a boot menu?

---

### Post by oldfred on 2012-12-20
Wubi does not work with gpt partitions which new Windows 8 systems use with UEFI boot.

Shrink your Windows install using Windows mmc and reboot several times. Fully back up Windows partition and efi partition.
One advantage of UEFI is with gpt partitions you do not have the old 4 partition limit. With gpt the new limit is 128 partitions. :)

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
HP maybe similar UEFI?
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

            UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by keeganxvx on 2012-12-20
Realized I downloaded and burned the 32 bit .iso to the USB instead of the 64 bit :roll:

I think I know how to boot it now.

Just to verify if everything is set to go, I made the K: partition for Ubuntu.
[http://i50.tinypic.com/28lwbig.png](http://i50.tinypic.com/28lwbig.png)
How exactly do I back up the Windows and EFI partitions?...

---

### Post by oldfred on 2012-12-20
Do not create partitions with Windows. It cannot create Linux partitions. Use Windows to shrink its own partition, but use gparted or the Ubuntu installer to create new partitions.

I do not have Windows 8, but these are Windows versions which may be better for Windows backup.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

These are Linux image tools:
       
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
     
    Your install will use the existing efi partition and you do not need the bios_grub from my standard suggestion. All partitions with gpt are primary.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by keeganxvx on 2012-12-21
Alright, so I got everything to boot and I've installed Ubuntu to dual boot, but I don't get the option to choose between Windows 8 or Ubuntu when I start up the computer, it just boots Windows 8.

---

### Post by keeganxvx on 2012-12-21
I got the menu to load up and used 'Try Ubuntu' and used the boot-repair and now I can get Ubuntu running normally, but now I can't load Windows 8. This is getting frustrating.

Here's the link that boot-repair gave me:
[http://paste.ubuntu.com/1454216](http://paste.ubuntu.com/1454216)

---

### Post by keeganxvx on 2012-12-21
I got into Windows 8 by manually booting the efi file.
Now I just want to remove ubuntu from dual boot and just have Windows 8, it was a wild trip, but not for me.

I've deleted the Ubuntu partitions, so what's the next step?
I've read that I need a Windows 8 repair disc, but I don't have one.

---

### Post by oldfred on 2012-12-21
Someone posted this. There is not a lot of info on how to repair Windows 8 with UEFI.

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)


You should just be able to set Windows as the default from UEFI and it will boot. You could remove the ubuntu/grub entry from the efi partition and reformat the space you used for Linux partitions back to NTFS. I would possibly keep the partitions separate as I prefer to keep operating system & data separate for all operating systems. When you have to reinstall operating system you do not have to reinstall data, but of course are still backing up your data.

---

### Post by keeganxvx on 2012-12-21
How do I remove the grub entry from the EFI partition?

In Disk Management I deleted the Linux partitions and expanded my main C:\ drive back to it's normal size. The other three are the same as in the picture I posted before, except K:\ is expanded back into C:\.

When I start the computer i get to this screen where it has says grub> and I can press tab to view what options I have to type. The only way I can boot to windows is if I type 'exit' and then it takes me to the blue themed HP system settings screen where I choose 'boot from efi file' and then it still has the two files from ubuntu, 'EFI' and 'boot'. I go to EFI>Microsoft>Boot>and then use the bootmdfw.efi.bkp to boot to windows. I have to go through this process every time I start the computer. I can still get to the metro looking UEFI screen when I'm in windows by going to the charm bar and going to settings (the gear), clicking 'change pc settings' at the bottoms, then it goes to the app screen where I go to general, and the advanced start up at the bottom. I tried the command prompt thing where I type bootrec /fixboot and bootrec /fixmbr, but it didn't seem to change anything.

If needed, I could make a video of what this all looks like, ha.

---

### Post by oldfred on 2012-12-21
I do not know what commands work from a Windows repairCD to fix UEFI installs.

But you should just be able to set Windows as the default in UEFI and it should continue to boot Windows.

/EFI/Microsoft/Boot/bootmgr.efi

---

### Post by keeganxvx on 2012-12-22
How do I set Windows as a default? I can't find any options to specify what efi file to boot from.

the bootmgfw.efi.bkp is the only one that works. All of the others give me a 'failed to boot from efi' and then I go bet back to the hp system settings screen.

---

### Post by oldfred on 2012-12-22
It looks like the only way to get Ubuntu to work is to add the Windows secure boot shim as the Windows boot file.

> 
Add .bkp to /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi 
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb) 
Add .bkp to /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi 
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Boot/bootx64.efi
It looks like you will have to undo the above, buy deleting the ones that are the really the shimx64.efi and rename the .bkp back to the Microsoft names.
Microsoft has made it extremely difficult to work with and some of the work arounds make it more difficult to undo. 
Not sure if Yann has updated his remove system to cover your case.

---

### Post by oldfred on 2012-12-22
This application should work for you in renaming files back so you just have Windows.

An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by keeganxvx on 2012-12-22
I can't boot Ubuntu, though, because I've deleted the partitions. I can only boot Windows 8. I just have the black screen with grub> where I can get to my HP system screen where I can choose the efi file.

I might just have to live with selecting the efi file to boot all of the time.

---

### Post by oldfred on 2012-12-22
You still should be able to boot the install USB as a live flash drive. And run the uninstall software from that.

---

