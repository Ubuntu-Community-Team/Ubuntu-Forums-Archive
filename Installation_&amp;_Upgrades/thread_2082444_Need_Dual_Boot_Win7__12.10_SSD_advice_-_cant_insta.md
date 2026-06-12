---
title: "Need Dual Boot Win7 / 12.10 SSD advice - cant install win7 SP1 now"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by Rahabib on 2012-11-09
So this is a two part issue.  Currently I have a dual boot that, with one exception, has worked fine.  I have an SSD 128g with Win7 and 12.10 on it working fine and a 1TB SATA drive thats split into two 500g partitions half NTFS and half Ext4 (/home).  Everything has been working fine for about a month but then in Win7, I noticed that I could not install SP1.  I get the infamous: [COLOR=#000000][B]0x800F0A12

[/B]I have tried everything, marking the system reserve as active via disk manager in win7 as well as using diskpart.  I have booted into safe mode and installing via a SP1 disc that I have downloaded from Microsoft's website - nothing works.

So, I guess I am going to have to reformat and start a new.  Part of the problem may be from the fact my 1TB SATA drive is set to disk 0 and my SSD is disk 1 - which may be part of the problem why I cant install SP1.  So I plan to just wipe everything out and install win7 and SP1 then add in ubuntu afterwards.

The question now is, is there a proper way to install the grub so that I wont have this issue when SP2 comes out?  Do I install the grub to the main linux partion ("/")?

Any help on any of the issues is greatly appreciated. :KS
[/COLOR]

---

### Post by oldfred on 2012-11-09
Moved to other OS. Since primarily a Windows issue.

Have you tried installing the Windows boot loader to the boot drive. Are you sure all the Windows boot is on the SSD. When Windows is installed to the second drive it puts it boot partition on the first drive if the first drive is set to boot from BIOS. OR is all of Windows install in SSD? 

Post this or run a full BooInfo repair for lots of detail:

sudo fdisk -lu

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems. Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Rahabib on 2012-11-09
> **oldfred said:**
> Moved to other OS. Since primarily a Windows issue.

Have you tried installing the Windows boot loader to the boot drive. Are you sure all the Windows boot is on the SSD. When Windows is installed to the second drive it puts it boot partition on the first drive if the first drive is set to boot from BIOS. OR is all of Windows install in SSD? 

Post this or run a full BooInfo repair for lots of detail:

sudo fdisk -lu

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems. Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

ok Ill give it a try when I get home.  I assumed the MBR was in the system reserve partition, but its possible they wrote it to the other drive since its marked as disk 0.  However I marked that as active and it still didnt seem to help.

---

### Post by oldfred on 2012-11-09
MBR is the very first sector of a hard drive and is not part of any partition, nor normally shown. BootInfo will show what is in MBR. 

System Reserved is normally a (hidden) NTFS 100MB boot/repair partition. Only with partition tools will you see it, Windows will not display it or give a a 'drive' letter.

---

### Post by Rahabib on 2012-11-10
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x26f38bb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976564547   488281250    7  HPFS/NTFS/exFAT
/dev/sda2       976566270  1953523711   488478721    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       976566272  1953523711   488478720   83  Linux

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51ec8e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   195519347    97656250    7  HPFS/NTFS/exFAT
/dev/sdb3       195520510   250068991    27274241    5  Extended
/dev/sdb5       195520512   211191807     7835648   82  Linux swap / Solaris
/dev/sdb6       211193856   250068991    19437568   83  Linux

```

---

### Post by oldfred on 2012-11-10
It looks like sdb1 is typical Windows boot partition. Which is your main install sdb2 or sda1?

May be best to post link to full BootInfo report.

---

### Post by MarkAtNeerim on 2012-11-11
In my experience this problem occurs because Windows 7 wants the boot disk to be the one that contains the Windows MBR.

To install the Service Pack you need to reconfigure your BIOS 'Hard Disk Priority' (Award BIOS) to select the disk containing the Windows MBR at boot.   Once you do this and boot into Windows 7 you will be able to install the Service Pack.  

Once installed you can go back into the BIOS and reset the 'Hard Disk Priority' back to the disk that contains the Grub MBR and get your dual boot back.

You may need to boot into Ubuntu,  open a Terminal window and execute 'sudo update-grub' to fix up dual boot.  I didn't find this necessary but it may help with certain installations.

---

### Post by Rahabib on 2012-11-14
> **MarkAtNeerim said:**
> In my experience this problem occurs because Windows 7 wants the boot disk to be the one that contains the Windows MBR.

To install the Service Pack you need to reconfigure your BIOS 'Hard Disk Priority' (Award BIOS) to select the disk containing the Windows MBR at boot.   Once you do this and boot into Windows 7 you will be able to install the Service Pack.  

Once installed you can go back into the BIOS and reset the 'Hard Disk Priority' back to the disk that contains the Grub MBR and get your dual boot back.

You may need to boot into Ubuntu,  open a Terminal window and execute 'sudo update-grub' to fix up dual boot.  I didn't find this necessary but it may help with certain installations.

I think thats the problem.  sdb1 is the main  boot (win7/ubuntu)  but is disk 1 and sda1 is the sata (ntfs-data/home partition) and is disk 0.  Ill try the bios priority and report back.  I was planning on just opening up the computer and swapping the ports and maybe re-installing everything, but if this works - thats better.

---

### Post by Rahabib on 2012-11-14
> **oldfred said:**
> It looks like sdb1 is typical Windows boot partition. Which is your main install sdb2 or sda1?

May be best to post link to full BootInfo report.

using the commands you gave me, that was the full report.

---

### Post by oldfred on 2012-11-14
Not just the fdisk, but download the Boot-repair into your Ubuntu liveCD or download the full Repair ISO. Then run Boot-Repair and run the BootInfo report. Post link it gives you to lots of detail on your system.

Windows normally installs to drive 0 or sda, but if you install to one drive and have BIOS set to boot from another it will put its boot/repair partition on the BIOS boot device.

---

### Post by Rahabib on 2012-11-17
well thanks to your help I figured it out.

1) apparently windows wants to be on disk 0, so I simply swapped the ports in the computer - rebooted, made sure that the system reserve partition was active and then updated.  It went smoothly from there.

so if anyone else has issues and nothing else seems to be working, find a way to get your windows to disk0.

Thanks again everyone. :P

---

### Post by LinGNUbie on 2013-02-01
I have also a fix that might be working, posted in thread [http://ubuntuforums.org/showthread.php?p=12487329#post12487329]("http://ubuntuforums.org/showthread.php?p=12487329#post12487329")

More thorough instructions [here]("http://ubuntuforums.org/showthread.php?t=2111400").

---

