---
title: "Dual Booting Windows 10 and Ubuntu on separate drives"
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by lambs2 on 2020-05-05
[COLOR=#454545][FONT=&amp]Hi there, please help![/FONT][/COLOR][COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I just built a new PC and wanted to dual boot Windows 10 Education and Ubuntu on two separate discs: Windows (SSD 500GB for gaming), Ubuntu (HDD 1TB for programming). First, I installed Windows on SSD. Then, I installed Ubuntu on HDD. Following the information online (link at the bottom), I changed the following in my BIOS UEFI settings (Motherboard: ASUS ROG STRIX B450F Gaming) after inserting USB Flashdrive with Ubuntu installation media:[/FONT][/COLOR]

[LIST=1]
[*]**Disabled fast boot**
[*]**Attempted to disable secure boot** (but no option was available, only a drop down menu with &#8216;Windows OS&#8217; or &#8216;other OS&#8217; so I left it unchanged as &#8216;other OS&#8217;
[*]**Set CSM to &#8216;UEFI only&#8217;** as my Windows mode was set to &#8216;UEFI&#8217;
[*]**Changed the boot order** to: **(1)** UEFI Kingston USB Flashdrive **(2)** Kingston USB Flashdrive** (3)** UEFI Windows Boot **(4)** SSD Samsung EVO 860 500GB
[*]**Changed the Boot Option BBS **to: **(1)** HDD Western Digital 1TB **(2)** SSD Samsung EVO 860 500GB
[/LIST]
[COLOR=#454545]
After booting into Ubuntu installation, I selected[/COLOR]

[LIST=1]
[*]&#8216;***Something else***&#8217; where I had dev/sda (SSD) with Windows partitions on it and sdb (HDD) with 1TB free space.
[*]Following the partioning scheme I found on the link (listed at the bottom) for an isolated dual boot, I manually partitioned the HDD drive for Ubuntu as:
[/LIST]

[LIST]
[*]/dev/sdb1 > / (ext4)
[*]/dev/sdb2 > swap
[*]/dev/sdb3 > efi
[*]/dev/sdb4 > /home (ext4)
[/LIST]
[COLOR=#454545][FONT=&amp]Everything works fine. GRUB menu pops up to choose which OS I want to boot into. Both OS seem to function properly. However, the HDD that I installed Ubuntu on is no longer detected in my BIOS/UEFI menu. Instead, it shows as installed on SSD (where Windows was installed) as:[/FONT][/COLOR]

[LIST=1]
[*]Ubuntu SSD 500GB
[*]Windows SSD 500GB
[/LIST]
[COLOR=#454545][FONT=&amp]Also, I can no longer see the Boot Option BBS menu and when going to Ubuntu > Settings > About, it states the disk capacity is 1.5TB, which is incorrect as the SSD (Windows) has 500GB and the HDD (Ubuntu) should have 1TB. So, I'm not sure if it's a real issue but[/FONT][/COLOR]

[LIST]
[*]Why did Ubuntu install it&#8217;s boot loader onto the SSD when it was specified to install on the HDD (/dev/sdb3)?
[*]Should I have not created the efi partition?
[*]How do I fix this to install Ubuntu on a separate drive safely without affecting my current Windows 10 OS on the SSD?
[/LIST]
[COLOR=#454545]Ideally I would've liked the 1TB HDD split in half for shared storage as: SSD (500GB: Windows) and HDD (500GB: Linux | 500GB: shared space between both OS), however when adding the first partition table during the Ubuntu installation, it wiped the previous partition on the HDD (500GB Allocated | 500GB Free Space) to 1TB Free Space and I just let it be as I was already in installation and thought I could shrink it later.
[/COLOR][COLOR=#454545][FONT=&amp]
Would REALLY appreciate some proper help.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp][B]
Additional information:[/B]
Link I used as a guide (top voted answer): [[COLOR=#e4af0a]https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives[/COLOR]]("https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives") 

And here's the results of running ***sudo fdisk -l ***on Ubuntu terminal:
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop0: 142.94 MiB, 149856256 bytes, 292688 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop1: 93.94 MiB, 98484224 bytes, 192352 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop3: 54.97 MiB, 57618432 bytes, 112536 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop4: 57.32 MiB, 60096512 bytes, 117376 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop5: 160.16 MiB, 167931904 bytes, 327992 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop6: 240.82 MiB, 252493824 bytes, 493152 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop7: 49.8 MiB, 52203520 bytes, 101960 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]**Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors**[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk model: Samsung SSD 860[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk identifier: 495EB8EA-XXX-XXX-XXXX-XXXXXXXXXXXX

[/FONT][/COLOR][TABLE="width: 50"]
[TR]
[TD]Device[/TD]
[TD]Start[/TD]
[TD]End[/TD]
[TD]Sectors[/TD]
[TD]Size[/TD]
[TD]Type[/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sda1[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]2048[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1085439[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1083392[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]529M[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Windows recovery environment[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sda2[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1085440[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1288191[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]202752[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]99M[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]EFI System[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sda3[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1288192[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1320950[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]32768[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]16M[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Microsoft reserved[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sda4[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1320960[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]976771071[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]975450112[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]465.1G[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Microsoft basic data[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#454545][FONT=&amp]**Disk /dev/sdb: 931.53GiB, 1000204886016 bytes, 195352168 sectors**[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk model: WDC WD10EZEX-60W[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk identifier: 75F94AAD-XXX-XXX-XXXX-XXXXXXXXXXXX
[/FONT][/COLOR]
[TABLE="width: 50"]
[TR]
[TD]Device[/TD]
[TD]Start[/TD]
[TD]End[/TD]
[TD]Sectors[/TD]
[TD]Size[/TD]
[TD]Type[/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sdb1[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]2048[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]58593279[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]58591232[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]28G[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Linux filesystem[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sdb2[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]58593280[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]107421695[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]48828416[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]23.3G[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Linux swap[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sdb3[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]107421696[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]108691455[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1269760[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]620M[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]EFI System[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#454545][FONT=&amp]/dev/sdb4[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]108691456[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]976771071[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]1844832256[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]879.7G[/FONT][/COLOR][/TD]
[TD][COLOR=#454545][FONT=&amp]Linux filesystem[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#454545][FONT=&amp]Disk /dev/loop8: 62.9 MiB, 65105920 bytes, 127160 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop9: 242.43 MiB, 254193664 bytes, 496472 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Disk /dev/loop10: 27.9 MiB, 28405760 bytes, 55480 sectors[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Thanks![/FONT][/COLOR]

---

### Post by yancek on 2020-05-05
The Ubuntu EFI installer defaults to installing the EFI boot files to the first drive which in your case was sda2 where the windows EFI files are.  Some people see this as a "feature" others as a "bug".  If you had physically dis-connected the windows SSD or disabled it in the BIOS (if possible?) then Ubuntu would have put the EFI files on sdb3 which is the EFI partition on the Ubuntu drive.

You could try booting Ubuntu and mounting sda2 and looking for an ubuntu directory there to see if this is what happened.  Also check sdb3 to see if any files are there.  If your ubuntu efi files are on sda2 and sdb3 is empty you could try copying the ubuntu directory and contents from sda2 to sdb3 and running update-grub.

---

### Post by lambs2 on 2020-05-05
Thank you for your response! I didn't know it defaulted to install on the first drive regardless of whether you changed the Boot Order Priority options. A lot of the resources online say you shouldn't nor have to unplug any hard drive SATA power cables but seems as though that's not the case.

I ran $ findmnt command in terminal and didn't see sdb3 anywhere but found:

/boot/efi     /dev/sda2   vfat    rw, relatie, fmask=0077

which contains the Windows EFI as well.
So how do you go about accessing and copying the contents over? Will I need to delete any content after copying? And is there another way of doing this? I just really don't want it to affect my Windows 10 OS as it's an Education version and you get only get a one time use product key.

---

### Post by oldfred on 2020-05-05
It is only the Ubuntu Ubiquity installer that chooses to install grub to first drive.
I have installed other distributions just to see how grub installs & works and they installed to my sdb's ESP without issue.

I regularly install a test install of Ubuntu to sdb drive. But only have main working install on sda, now NVMe drive and my sdb became sda.

You can just copy /EFI/ubuntu & /EFI/Boot from sda's ESP to sdb's ESP. Edit fstab to change mount of efi partition to sdb's ESP, so updates are to sdb. And then delete UEFI boot entry as it uses GUID of sda's ESP to know where to look and and new UEFI boot entry using efibootmgr.

Usually easier just to totally reinstall grub, but have to change fstab as it uses that to know where to install with default settings. 
Or use Boot-Repair.

Please add to this bug report. I posted work around, but unless many complain (more heat) it will  not be fixed. And bug is really old as related to the other much older bugs.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

I typically have to manually mount any other ESP or use Disks to mount it.
I also have to change mount of ESP from 0077 to defaults like they used with 14.04. It probably is 0077 for security reasons and I may change back and then have to use live installer or another install that mounts my other ESP to edit it.

#14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    [COLOR=#ff0000]defaults [/COLOR]       0       1
#16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1

---

### Post by yaminb on 2020-05-06
Yep, I did pretty much your same install recently.
This 'feature' of Ubuntu confused the hell out of me. Even Windows let's you choose the drive you want to install to.

In my case, I manually created the partitions for Ubuntu on the drive I wanted and told it to use those drives.

I also created an EFI boot partition on each drive.

Windows Drive has it's own EFI boot partition that windows uses (I installed windows first)
I manually created the Ubuntu partitions in the installer and had it use it's use it's own EFI boot partition on it's own drive.

I generally use the old school BIOS boot order to choose which drive to boot to.

Unless you have a lot of personal data, just reinstall everything. I don't think the Windows key would be impacted as your hardware is still the same. I've never had that issue with windows unless the hardware changes (motherboard...)

---

