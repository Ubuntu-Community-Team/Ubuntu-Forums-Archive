---
title: "OS disk failed - questios concerning reinstall otions"
date: 2020-08-29
forum: Installation &amp; Upgrades
---

### Post by bhcarpe on 2020-08-29
I have been on Ubuntu 18.04.5 x64.  I have a backup of the data partition created by Clonzilla but not the grub/directory partition,  I have ordered a new drive that should be here in 2 days,  In the meantime, I am trying to clarify what I can and cannot do when I install the new disk.  So, I have some questions.


[LIST=1]
[*]If I restore the backup data partition, how do I get the grub/directory partition installed? 
[*]Assuming I can do (1), does the directory need to be updated to align with the data? 
[*]As in (2), do i I have to do anything concerning grub? 
[*]If I can't do (1), can I do a clean install and copy my home directory from my backup over the home directory created by the clean install? 
[*]Are there any questions I am overlooking? 
[/LIST]

I realize if I have to do a clean install, I will have to install all my applications.  I do have a list of those applications.

Thank you for your help.

---

### Post by oldfred on 2020-08-29
When you say grub directory partition which partition are you referring to? The ESP - efi system partition?
Or a separate bios_grub partition? Or just the MBR where grub boots from with BIOS/MBR configuration.

Normally a new install will install grub with all the default settings. Only if you changed grub settings would those be lost if you did not back those up. I change 40_custom and one or two other files in /etc, so make copies into /home so my normal backup includes those. 

If you have a / (root) you really want to restore, you may need to totally reinstall grub & that would still reset grub settings to defaults.

Not sure what your backup does, but installs need sync of GUID/partUUID, UUID and sometimes device like /dev/sda. New install makes sure all that is in order. A restore may require some editing, which if you know what to do, is not difficult, but if you do not know can be a task to learn.

---

### Post by bhcarpe on 2020-08-29
> **oldfred said:**
> When you say grub directory partition which partition are you referring to? The ESP - efi system partition?
Or a separate bios_grub partition? Or just the MBR where grub boots from with BIOS/MBR configuration.

Normally a new install will install grub with all the default settings. Only if you changed grub settings would those be lost if you did not back those up. I change 40_custom and one or two other files in /etc, so make copies into /home so my normal backup includes those. 

If you have a / (root) you really want to restore, you may need to totally reinstall grub & that would still reset grub settings to defaults.

Not sure what your backup does, but installs need sync of GUID/partUUID, UUID and sometimes device like /dev/sda. New install makes sure all that is in order. A restore may require some editing, which if you know what to do, is not difficult, but if you do not know can be a task to learn.

I have a 2 TB system disk and a 2 TB desktop USB disk.  Both are Western Digital.  If I try to back up disk to disk (i.e., get both partitions in the backup), Clonzilla tells me the desktop is smaller capacity than the internal system disk.  I have been meaning to check out some other options, but time seems to get away.

Is it your opinion that I should do a clean install and copy my old home directory to the new install?  If so, are there good reasons to save the new home by renaming it?  I do keep all my data files on a separate data disk, so the main reason to restore my old home would be configuration files.  But if I could install the old system partition, I wouldn't have to install all my applications.  That would be great.  That is why I'm hoping someone can help me with question 1 in my original post.

---

### Post by bhcarpe on 2020-08-29
I know one can get UUID from gparted and Disks. The type of partition table is available from them both as well.  I'm not sure where to get GUID/partGUID.

---

### Post by oldfred on 2020-08-29
If UEFI, you should have gpt partitioning. UEFI uses GUID, but it is shown as partUUID.

lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

when I changed to use a separate data partition, I stopped using a separate partition for /home as it was too small. I do many new installs, but just import list of installed apps, so I have the same apps in new install.

---

### Post by bhcarpe on 2020-08-30
If I use Clonzilla to restore the OS partition to the new disk, can someone tell me the steps required to get the grub/directory partition defined so that I have a bootable system disk on the new disk?  I think (don't really know) that I could boot the Ubuntu DVD, use gparted to create the required partition and install grub.  If that sequence is workable, could someone help me by giving me the steps required to accomplished it?  If that approach will not work, could someone let me know?  Thanks.

---

### Post by oldfred on 2020-08-30
There is not a grub directory.
Do you have an ESP for UEFI boot or a bios_grub for BIOS boot on gpt drives?

You you want an ESP, you create a 300 to 500GB FAT32 formatted partition with the boot,esp flags.
If you want a bios_grub partition it is 1 or 2MB unformatted with bios_grub flag. But not required if you use old MBR partitioning, but you should not only use MBR if you have to have Windows in BIOS boot mode. If blank drive, you need to change to gpt first, as gparted still defaults to MBR unless large drive.

Installer in UEFI mode uses gpt unless drive seen as MBR. It really should not install in UEFI mode to MBR as that often breaks a Windows install if on same drive.

---

### Post by bhcarpe on 2020-08-30
> **oldfred said:**
> There is not a grub directory.
Do you have an ESP for UEFI boot or a bios_grub for BIOS boot on gpt drives?

You you want an ESP, you create a 300 to 500GB FAT32 formatted partition with the boot,esp flags.
If you want a bios_grub partition it is 1 or 2MB unformatted with bios_grub flag. But not required if you use old MBR partitioning, but you should not only use MBR if you have to have Windows in BIOS boot mode. If blank drive, you need to change to gpt first, as gparted still defaults to MBR unless large drive.

Installer in UEFI mode uses gpt unless drive seen as MBR. It really should not install in UEFI mode to MBR as that often breaks a Windows install if on same drive.

Thanks.  I had a bios_grub partition on my failed drive.  I only have Windows as a guest under VirtualBox,  Which type partitioning do you recommend?  It is a 2 TB drive.

When I upgraded from 16.04 to 18.04, I did a clean install, so Ubuntu selected the type of partitioning.  They chose bios_grub.  I have never created a bios_grub partition manually.

So should I


[LIST=1]
[*]Create the bios_grub partition with gparted; 
[*]use Clonzilla to restore my OS partition; 
[*]install/update grub. 
[/LIST]

How will the directory get aligned with the OS partition.  It seems as if there is a missing step somewhere?

---

### Post by oldfred on 2020-08-30
You typically have to just reinstall grub either manually or with Boot-Repair.

I highly suggest using gpt. The only reason for MBR, is if you must have Windows in BIOS mode. 
Do not know about Windows in virtual installs.

When I only had BIOS, I started converting new or repartitioned drives to gpt back in 2010. In 2012 when Microsoft required vendors to install Windows in UEFI/gpt mode, I started to add both ESP & bios_grub to all new or changed drives. Only one or other required, but if moving drive to newer UEFI system having ESP makes it easier to just reinstall grub rather than major redo of drive.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Older screenshots, but still same with updated graphics now.

---

### Post by bhcarpe on 2020-08-30
> **oldfred said:**
> You typically have to just reinstall grub either manually or with Boot-Repair.

I highly suggest using gpt. The only reason for MBR, is if you must have Windows in BIOS mode. 
Do not know about Windows in virtual installs.

When I only had BIOS, I started converting new or repartitioned drives to gpt back in 2010. In 2012 when Microsoft required vendors to install Windows in UEFI/gpt mode, I started to add both ESP & bios_grub to all new or changed drives. Only one or other required, but if moving drive to newer UEFI system having ESP makes it easier to just reinstall grub rather than major redo of drive.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Older screenshots, but still same with updated graphics now.
Okay, thanks for the info.  I don't dual boot, so I've never had to deal with many of the issues listed.  I wonder if the following sequence would work:

[LIST=1]
[*]Install to new disk from live DVD of 18.04.05; 
[*]Use Clonezilla to restore my backup of my 18.04.5 over the fresh install. 
[/LIST]
Then I would have gpt, and the partitioning of he new disk would be correct.  The only thing that worries my mind is how will the directory know that the contents of the OS partition have changed.
What do you think?

---

### Post by oldfred on 2020-08-30
If you are just restoring /home, should not be an issue, unless you are not user 1000 (default first user). But that can quickly be corrected.

Issue is if restoring system files and new install has new UUID in /etc/defaults/grub for example, but your backup overwrites that with old info. I normally suggest including in a backup /etc or any files you may have manually edited, but not just restore them as new install may want or need different settings.

---

### Post by bhcarpe on 2020-08-30
Okay, here's what I have done:
[LIST=1]
[*]Booted from my Live DVD; 
[*]used gparted to create a gpt directory; 
[*]defined the disk partition as EXT4; 
[*]booted from Clonzilla CD 
[*]restored my system partition backup to the new disk. 
[/LIST]

When I boot from my new disk, the grub menu appears.  I select the newest kernel from the list and press enter.  I end up in emergency mode,

If I ente]```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```
it shows that sda1 is mounted at /.  My assumption is I need to install grub,.

So I booted Live DVD again and installed grub.  I then tried to boot from the new disk and got an error that symbol grub_call?? (don't remember the exact name) was missing.
I am now running fsck on sda1.  When that completes, I'll try again to boot.  If it fails, I will install over the new drive from Live DVD and restore my home from the backup.  I will then start all my application installs.

---

### Post by oldfred on 2020-08-30
Do you have a bios_grub partition?

Post your lsblk command output in code tags.

Or to exclude all the loop devices:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by C.S.Cameron on 2020-08-30
I use Grsync to copy my home directory from an old install to a new install.

---

### Post by bhcarpe on 2020-09-05
Well, after much sweat and toil, I bit the bullet and did a clean install from the Live DVD.  Then I restored my home directory, got the configuration files straightened out, and am almost through installing my applications.  This has been a lesson for me, and you folks have been the teachers.  Thanks for all the help.  I'll mark this thread as closed.

---

