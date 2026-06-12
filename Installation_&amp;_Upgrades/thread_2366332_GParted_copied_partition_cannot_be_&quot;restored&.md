---
title: "GParted copied partition cannot be &quot;restored&quot;."
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-07-16
Using GParted in LiveUSB I copied my /home to an external drive. I thought I could then copy it back into sufficient empty disc space. My reading about GParted using e2fsprogs gave me to believe that it copied only that portion of the disc that was in use with files, folders, directories, etc, not empty space. With the /home partition copied I felt I could proceed. This was necessary as the original /sda (or /) was "corrupted" with partitions that could not be deleted. They were like ghost partitions. Nothing in them. Nothing could be changed in them.

Next a bare silicon ssd was connected to the motherboard. Ubuntu 16.04.2 installed. Unetbootin made a LiveUSB of the .iso of 16.04.2. Running a session in LiveUSB and using GParted I unmounted all partitions, turned swapoff, powered up the external device containing the /sda5 copy, made certain it and all partitions were not mounted and tried to copy /sda5 back to the ssd having only a / and a swap. Nothing doing. Next day, I tried to copy the /sda5 to another external device to make a second copy (in case of emergency). Same method LiveUSB. No success. I don't want to touch /home unless I get two copies, in case I run into more problems; if at all possible. I have 2 external devices. Both sata, both ext4. I could not, using GParted copy what was on the first external device to which /sda5 had been copied, to the second external device. Not in "regular" mode and not in LiveUSB mode.

When GParted first copied /sda5 to the external drive, the 150 odd gig were copied over to a 2T device. GParted shows the data on that sata as being the - I don't know how to well describe this - the data (my /home) seems to not be /sda5 but the entire drive, as though it was a single partition on that device and not /sda5 any longer. What appears on the external disc has filenames such as: duplicity-full-20170714T2203599vol1.diftar.... --- Now that GParted has copied the partition over to an external device, it won't load without the session being in LiveUSB mode as well. 

So I have a backup of my /home and need help in recreating that partition or just recovering the files, folders and such from it. I would also like to make a backup of the backup first. (Sorry for the redundancy, here) I don't care how I do it as /home is where the heart is. Can you help me save my /home?

It is more than possible that the above description is sketchy or incomplete. I will answer any queries promptly but bear with me a little please. This problem is the worst I have ever encountered. Yes, it's my doing. Yes, I need help. I would gladly accede to having to reinstall the OS and go from there. I'm getting kinda itchey to get /home recovered.

Both the copied /sda5 as well as the current /sda of /  are ENCRYPTED FS of ext4. Yes I have the passphrase generated at install time.

---

### Post by oldfred on 2017-07-16
I do not use encryption, but always thought it better to backup the data in the encrypted partition, not the encrypted partition itself. Then it may be possible to recover files if issues. Unless you can mount encrypted partition, then it is like no backup at all.

But if it says duplicity, are you sure you used gparted and not duplicity to make backup.
[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)
> Duplicity backs directories by producing encrypted tar-format volumes
and uploading them to a remote or local file server. 
Or does gparted use that in the back ground. 

So have you tried using duplicity to see if it correctly sees your old sda5?
And if it is copying data, you may need partition to copy it into?

---

### Post by Mark_in_Hollywood on 2017-07-16
Thanks for a swift reply.

Responding to your questions:

Or does gparted use that in the back ground. **I am by being asked this,  uncertain that the partition was copied to the external sata (ext4) using GParted. As that was Thursday or Friday last.**

So have you tried using duplicity to see if it correctly sees your old sda5? **Not yet, that is something I have never done. I would like to make a copy of the /sda5 or whatever GParted now calls it to a second external drive for security sake. I'm afraid to run a command on it unless it's backed up twice.**

And if it is copying data, you may need partition to copy it into? **I should make a partition for GParted to copy the (old) /sda5 to? Does GParted need to copy to a larger partition that the device (partition?) it's coming from?**
[B]
I can see the partition that GParted copied to the external sata drive, while I am using LiveUSB sessions.[/B] I cannot copy it using commands like: Ctrl-A Ctrl-C and Ctrl-v in the 2nd external drive.

For the remainder of Sunday (here in the Western Hemisphere) I will be using a LiveUSB mode. 12:53 zulu. 7:54pm Greenwich Mean Time.

How do I mount the encrypted drive or partition or whatever it is? I think I can try Ubuntu "Backups" to restore, but when I'm in ordinary or regular mode, not LiveUSB, I cannot see the files above referenced on the external device.

---

### Post by oldfred on 2017-07-16
I have never used gparted to copy a partition, so not sure what it does.
But I would expect that if you were able to copy to external, then it should be the same to copy again.

If compressed, and encrypted you would not be able to mount with any of the normal commands.

Using terminal or Naulitus to copy, I would not expect to work. Only the same tools you originally used.

How was partition encrypted? Was it full drive encryption inside LVM?
Gparted does not support LVM except for the physical partition the LVM is inside of.

---

### Post by Mark_in_Hollywood on 2017-07-16
During the install from Unetbootin's .iso of 16.04.2, I selected encryption. That is all I know. I see some posts online about doing this, or so I think. I'm not certain what I'm looking at just. yet.

Thank you, Old Fred.

---

### Post by oldfred on 2017-07-16
You probably selected full drive encryption which uses LVM.
Gparted does not fully work with LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)

 Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) 
   [SOLVED]Secure boot issue - fix with Boot-Repair LVM with encryption
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963) 
      
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

---

### Post by Mark_in_Hollywood on 2017-07-18
I am adding this for those who come here looking for solutions.

> **oldfred said:**
> You probably selected full drive encryption which uses LVM.
Gparted does not fully work with LVM.

 Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627)

Per above, my terminal output:

mark@Lexington:~$ [[ -e /sys/firmware/efi ]] && echo EFI || echo BIOS
BIOS

---

### Post by oldfred on 2017-07-18
You can boot LVM with either UEFI or BIOS.
If UEFI, you have an ESP - efi system partition.
If BIOS, grub is installed into the MBR.
With both systems, grub then boots and loads kernel from separate /boot partition and loads the unencryption code and ask for password.

---

### Post by Mark_in_Hollywood on 2017-07-18
I'm double checking about this. I can switch the BIOS, after installing Ubuntu from Legacy+BIOS to UEFI without harming / or /boot or GRUB2? What I'm trying to accomplish is copying the encrypted info from one external sata to another external sata. I say "info", as the .private and all the rest of the icons showing in the file manager, when looking at the external device, seem to indicate that my /home is there. But before I can touch that, I must have a backup of the "info". If it's at all possible.

---

### Post by oldfred on 2017-07-18
Unless you have gpt partitioning and have both the ESP - efi system partition and a bios_grub partition it is not straightforward to switch from BIOS to UEFI or vice-versa. If gpt, and you have both partitions, then you just need to reinstall grub.

But boot mode should have nothing to do with encryption and mounting of encrypted partition.

UEFI normally uses gpt.
BIOS normally uses MBR(msdos).
Windows only works as above, but Ubuntu can use gpt and boot in either UEFI or BIOS.

But if hardware is UEFI, you normally have options to set UEFI or BIOS boot. And then how you install is the only way you should boot.

---

### Post by Mark_in_Hollywood on 2017-07-19
The command I ran in an above post shows I have:

BIOS

That, at least to me, holds true, as the motherboard configuration was set to Legacy (to mean not UEFI). All work since that time is done in Legacy. 

The device where the backup of /home, currently encrypted, and stored on an external device is flagged "msftdata". 

Here is some device info:

```
mark@Lexington:~$ sudo fdisk -l
[sudo] password for mark: 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type:**dos**
Disk identifier: 0x25bf70f8

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048  21483519  21481472  10.2G 83 Linux
/dev/sda2       472772606 488396799  15624194   7.5G  5 Extended
/dev/sda3        21483520 472770559 451287040 215.2G 83 Linux
/dev/sda5       472772608 488396799  15624192   7.5G 82 Linux swap / Solaris

Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type:**gpt**
Disk identifier: 0C16BB68-9E62-466E-8BEB-E2655D8EE7AF

```

I cannot use the /dev/sdd or /sdd1. I want to copy only the used part of about 150 gig to another external device for a safety backup. In general terms, is it safe to shrink the partition to the left? This is a 2T drive, with the /home using about 150 gig, starting at the very left. I've heard it's safe to make more space by enlarging the partition (move to the right) on which the data is. As the 2nd device that would receive a copy of this encrypted partition is smaller than the 2T, I want to copy it safely. 

I would restore it, but for the fact that when 16.04.2 was installed to the ssd, I left the space for /home blank, not understanding that GParted would not actually copy an encrypted partition, even though it says it did copy it.

I ask for your patience with my problem. This started with me installing Ubuntu using the encryption, then backing up /home. If memory serves, I thought I used GParted to copy the partition. I'm now informed that GParted cannot do such. So, in the time between the making of the backup of /home and my bricking the 1st ssd, and replacing it with a 2nd ssd; under much distress, I've forgotten exactly what happened when. I have both 32 element passwords. The /home hold 10 years worth of work. I'm most concerned about making a copy of it. Then I can start to play with restoring.[ATTACH=CONFIG]276053[/ATTACH][ATTACH=CONFIG]276052[/ATTACH]

I am not being asked for a password when the external drive is powered up. What I can see is this:

[ATTACH=CONFIG]276054[/ATTACH][ATTACH=CONFIG]276055[/ATTACH]

---

### Post by oldfred on 2017-07-19
I would never backup an encrypted partition while encrypted. Too many chances of problems and then no way to recover any data. If using encryption on portable computer then the backup would not normally be outside your home or office and should then be secured in your home anyway.

 I would have multiple regular backups of the data from inside the encrypted partition.If real valuable, in fireproof safe and another regular copy in a secure offsite location. 

It does not look like you have partitioned your 2TB drive. You need to partition to have a place to copy data into. I prefer to use gparted.

For my copy of data I prefer rsync, but have to edit each version for different flash drives, so I keep them separate. And I really only consider the DVD copies as backup as copy to another drive as that is not versioned. Or if I change a file, the backup overwrites the old copy, so I cannot get it back. But versioned copy on DVD is stored as long as DVD lasts which may not be forever, but some are now 10 years old and still readable. 

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 


 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 


      
 [https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)

---

