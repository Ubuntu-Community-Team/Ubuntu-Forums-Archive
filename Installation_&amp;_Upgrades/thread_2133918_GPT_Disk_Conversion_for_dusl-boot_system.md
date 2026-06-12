---
title: "GPT Disk Conversion for dusl-boot system"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2013-04-09
I have a Kubuntu 12.04 system with three disks. The Kubuntu boot disk is /dev/sda and has one ext4 partition. On the other two disks /dev/sdb and /dev/sdc, the first partition is a Linux RAID partition, and I use Linux software Raid and mdadm to mirror these partitions in a RAID1 mirrored volume. The second partitions on /dev/sdb and /dev/sdc were ntfs partitions, on which I installed the Win7 boot disk C: and a Win7 data disk D: respectively. Thereafter I tried to upgrade to Win8, and, perhaps unfortunately, deleted the Win7 install on /dev/sdb (I haven't touched the Linux RAID partitions on the first partitions of /dev/sdb and /dev/sdc, and the Linux software RAID1 volume continues to work fine.

My system has a UEFI BIOS, and I found out in the process that to install Win8 on a UEFI system you have to create a UEFI-compatible Win8 USB flash install stick. OK, so I did that, and booted the Win8 install from that. The Win8 install started up, but when I select the NTFS partition on /dev/sdb, previously the Win7 C disk, and started the Win8 install, I get the error message "On EFI Systems, Windows can only be installed on GPT disks".

I take it that /dev/sdb and /dev/sdc are MBR disks, and I believe Linux supprts GPT disks and that there's a way to convert them to GPT disks with my NTFS partitions as before .... but I's unclear what this means for the Linux software RAID partitions. I believe GPT has a different scheme for disk boot sectors, and while I'm far from an expert on Linux software RAID, I have the impression that GPT changes the boot sector layout and that mdadm may have information on the boot sector, thus screwing up my RAID1 volume if I convert. Can anyone tell me if this can be done, and if so describe and/or point me to a link as to how?     Thx, Gus

---

### Post by darkod on 2013-04-09
Boot sectors are not an issue, but the fact that writing a new partition table destroys all data, is. I'm not aware of any way to write a new gpt table without destroying the partitions (which means the data also).

On the other hand, win8 can install in legacy mode as far as I know. You just have to be careful how you boot the dvd/usb. If you boot it in uefi mode, it will try to install in uefi mode. If you boot it in legacy mode it will install in legacy mode and using msdos tables shouldn't be a problem.

You say you have uefi bios but according to the partitions you listed, you are not actually using uefi boot, which is great. For uefi you need FAT32 efi system partition, you didn't mention you need one.

Go into bios and disable uefi boot, select Legacy Only or depending how the option will be called. That will make sure you never boot any install media in uefi mode.

After that boot the win8 dvd/usb and it should install fine on the current ntfs partition(s) on the disks with msdos tables. You might need to create ntfs partition for it in advance, and not using the win8 installer because it might try to create the small system reserved partition if you use the installer to make partitions.

---

### Post by gus_zernial on 2013-04-09
My motherboard (ASUS Sabertooth 990FX) has no option to disable UEFI, Secure Boot, or to switch to "Legacy" BIOS.

The /dev/sdb on which I want to install Win8 has one RAID partition, which is part of a Linux mdadm software RAID1 mirror, and a second partition for Win disk C:. So what about this ..... I reformat /dev/sdb with GPT and same size partitions. I use mdadm to restore the "destroyed" RAID1 mirror on /dev/sdb, by syncing it with the RAID partition on the other /dev/sdc disk. I then install Win8 on the second partition on /dev/sdb, which is now a GPT disk. 

Would that work?

---

### Post by oldfred on 2013-04-10
Microsoft's requirement on Vendor's installing Windows with secure boot is that the use must be able to turn secure boot off. 
What has not been said is if Windows still works. Some systems will boot Windows with secure boot off, others will not.
A few early UEFI implementations would boot in UEFI mode by looking for efi partition, then if not found try to boot from BIOS mode looking into MBR. 
I might check if you have to newest UEFI/BIOS version. Gigabyte recently released major updates for newer boards to a full UEFI over the previous partial UEFI.

---

### Post by darkod on 2013-04-10
Are you sure the board hasn't got the option to disable uefi? My Gigabyte does, and works without problems.

Another thing you could do, is put the uefi boot devices at the end, so that it boots CDs/DVDs in legacy mode. Or even better, when we are talking about a one time boot to install an OS, boot the win8 dvd/usb using the board boot menu, where you can select the exact device you want to boot. There should be one legacy and one uefi device for each dvd-rom and usb stick. Simply select the legacy usb stick (if booting from stick) and it should boot it in legacy mode which also means installing in legacy mode.

I wouldn't worry too much about turning off Secure Boot oldfred, he is trying to do a clean install of win8. So, it's not like switching with windows already preinstalled. However, he says there is no option to turn secure boot off, and there should be. If there is, I would turn it off before installing win8 of course.

---

### Post by gus_zernial on 2013-04-10
Trust me, there is *no* option to turn UEFI/Secure Boot off and/or go to Legacy mode. I went to Asus forums to confirm, and they did.

---

### Post by darkod on 2013-04-10
OK. But in that case oldfred has a point in saying most systems will try booting in legacy if they don't find the efi system partition. Your board can obviously boot legacy since that's what you had with win7. It wasn't installed in uefi mode and there is no efi partition.

So, I think it's worth a shot installing win8 in legacy mode, just make sure when booting the dvd/usb to do it in legacy mode, not uefi. That way it will install in legacy mode and it can use msdos ntfs partition.

If that fails, I guess you can go with the idea to fail one member of the mdadm raid, create gpt table on that disk, add the new partition to mdadm, wait to fully sync, and then do the same with the other disk. Or leave only one disk as gpt if you wish to.

But I would give legacy win8 a shot first.

---

### Post by gus_zernial on 2013-04-11
At the beginning of this ordeal I did try booting the original Win8 install DVD in "legacy" mode, and received the message "We couldn't create a new partition or locate an existing one" .... despite the fact that I was trying to install to an existing NTFS partition. I have an earlier post in this forum about that effort, and finding no solution began to pursue the UEFI usb flash stick install, which was recommended in other forums. 

I think what I'm about to try after all this is to install a separate hard drive for Windows 8, and partition that as a GPT drive. I'm afraid if I continue to fool around with my existing Linux/Windows drives I'll accidently destroy my Linux data.

---

### Post by oldfred on 2013-04-11
Dual booting becomes difficult if one system is UEFI and the other BIOS. Each writes data to system differently for operating system to use. BIOS uses interupts, UEFI uses drivers.

So you have to Cold boot, usually you have to go into UEFI/BIOS and change setting, but if no setting then you just change which drive is boot drive. A chainload entry from grub will not work as internal data is too different.

---

### Post by darkod on 2013-04-11
I am wondering if the message you got was if the ntfs partition didn't have boot flag on it. If there is no boot flag, I think the installer since win7 will try to create the small system reserved partition, which it didn't have space or opportunity to do.

Have you tried from ubuntu formatting the partition destined for win8 (format it as ntfs of course), and making dure it has boot flag on it.

Then see what the win8 installer says when you tell it to use that partition. And use the Advanced installer of course, in case there is one, similar to how it was for win7.

---

### Post by Aide9aic on 2013-04-21
Sometimes legacy mode is labeled with the cryptic "CSM," meaning *compatibility support module.* On the Samsung Series 7 slate I used to have, that was the trigger. I would select **Enable CSM** and the machine would boot into legacy BIOS mode. Perhaps the same lableling is used by Gigabyte?

---

