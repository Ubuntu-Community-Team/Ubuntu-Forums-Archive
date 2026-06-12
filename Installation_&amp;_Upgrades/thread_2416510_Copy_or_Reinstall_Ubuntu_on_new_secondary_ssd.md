---
title: "Copy or Reinstall Ubuntu on new secondary ssd"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by ruddypeter101 on 2019-04-10
I currently have ubuntu 18.04 and windows 7 dual boot on my asus laptop, on a 1tb hdd. I have just replaced the optical drive with a 240gb ssd. Is there a way to copy my ubuntu os over to the ssd without copying the windows partitions and my ubuntu home folder. I would like all my photos, videos and documents to stay on my hdd. Is this possible and if not how can I reinstall ubuntu onto the new 240gb ssd. I have tried formatting and mounting the drive and then trying to boot load with a flash drive but as soon as I select install ubuntu i get a black screen and my laptop reboots itself. I also am not the most linux sufficient so may need a lot of explaining. Can anyone help me? Thank you in advance.

---

### Post by oldfred on 2019-04-10
Not all systems will boot from a drive that replaces a DVD drive. Even though DVD drive was bootable on its own.
Some then have to have boot loader/grub and maybe a /boot with kernel to boot on main drive & rest of system on new drive.

This user has an older motherboard that would not directly support the NVMe drive he added via a add in card. But was able to configure a work around.
[https://ubuntuforums.org/showthread.php?t=2415658](https://ubuntuforums.org/showthread.php?t=2415658)

I prefer new installs & copy /home to new install which has all your user settings. Often better to have /home or data partition(s) separate from / (root) partition. But my / with /home but no data uses today 8.6GB of a 25GB partition on my 250GB SSD. My data is all on my HDD. So I seem to have some extra room on my SSD. :) I actually have several / partitions, a partition with multiple ISO to allow install to HDD or flash drives and space for future use.

This becomes a good way to test that your backup procedure includes all your data, settings, and list of installed apps. And if you are missing anything you still have your old install to get missing data from & add to backup procedure.

---

### Post by ruddypeter101 on 2019-04-11
Thank you for your reply, with it I swapped the hdd and ssd location so now the hdd is in the optical drive caddy. This meant I was able to install ubuntu onto the ssd. The problem I have now is when I start my laptop up it goes straight to the bios instead of the bootloader. When I go to boot options there is no options available and the ssd doesn't show up. If I start the laptop and hit esc to enter I do enter the grub bootloader and am able to get into the new install of ubuntu. Is there a solution to boot automatically to the bootloader rather than to the bios. Many thanks

---

### Post by oldfred on 2019-04-11
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2019-04-11
> The problem I have now is when I start my laptop up it goes straight to the bios instead of the bootloader.

Well, that is expected behavior on any computer.  The BIOS/motherboard starts and looks for a bootable drive and then you get your boot menu, if you have one.
Does the SSD show at all in the BIOS?  If not, check your connections to start with.
Did you set the SSD or can you to first boot priority in the BIOS?  Or is that your problem, you don't know how to do this?  What is the manufacturer of the computer as this method varies.  Generally, there is an OS Boot Manager option and you can use that to set priority.

---

### Post by ruddypeter101 on 2019-04-11
I have tried using the boot-repair and when restarted booted straight into windows from the hdd currently situated in the optical drive caddy. This is the report [https://paste.ubuntu.com/p/qqyBnVGJhQ/](https://paste.ubuntu.com/p/qqyBnVGJhQ/). I think the problem may be the partitioning on the ssd. However I am not sure what to do to rectify this. Any help would be much appreciated.

---

### Post by oldfred on 2019-04-11
All your boot files are on sdb in the ESP - efi system partition for UEFI booting.
You only show one ext4 partition on sdb.

It also shows Windows fast start is on or hibernation as it cannot mount the Windows NTFS partitions.
>         The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 
    

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You also show some old kernels. 
Is this install an upgrade? You should remove old kernels.

Can you in UEFI change boot order, probably in a Boot tab in UEFI?
Or:
       
 Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr

---

### Post by ruddypeter101 on 2019-04-14
I'm not really sure how to do any of that. Is there a way to edit the  partitions in the disks application in ubuntu. I currently only have two  partitions on this new ssd; 1 filesystem parition of 30gb ext4, and 1  free space of 210gb. I don't think I installed ubuntu correctly when  choosing and setting the partitions. Currently the hdd is located in the  optical drive and does not appear in the uefi boot menu and neither  does the ssd.

---

### Post by oldfred on 2019-04-14
I suggest that all new drives be partitioned in advance and include an ESP & bios_grub if any chance you may install on drive in UEFI or BIOS mode. Both are small and most drives are now large.
But grub only wants to install to an ESP on first drive, usually sda or first NVMe drive. But I would think & pretty sure I have seen where users changed SATA drive order & grub still booted.

I think you installed to your drive in caddy, but it but the UEFI boot entry in the main drive. Not sure then what happens when you swap drives.
Many UEFI forget boot entries when a drive is disconnected. Many UEFI also then will still find the Windows boot entry, but not any others. But your UEFI may only want to look at main drive?

From live installer you can create an ESP on new drive as FAT32 with boot flag and copy all the files & folders from the ESP on original drive.
Then you can add UEFI boot entries with efibootmgr. see this (not sure if on live installer)
man efibootmgr
More details in link in my signature with various examples.

---

### Post by ruddypeter101 on 2019-04-14
Thank you everyone for your help. I wasn't able to sort the problem out. However as it was a new ssd installed I reinstalled ubuntu and started from a fresh. I made sure I partitioned correctly this time and it boots fine into the grub now. Again thanks for all the help.

---

