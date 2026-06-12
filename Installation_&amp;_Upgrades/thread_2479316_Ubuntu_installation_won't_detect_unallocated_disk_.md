---
title: "Ubuntu installation won't detect unallocated disk space on HD"
date: 2022-09-20
forum: Installation &amp; Upgrades
---

### Post by jbtz93 on 2022-09-20
[FONT=Whitney]Hi everyone! I left 36 GB of my HD unallocated in order to install Ubuntu there: [/FONT][https://imgur.com/a/ktAil8i](https://imgur.com/a/ktAil8i)

[FONT=Whitney]However, this unallocated space is not shown on the list of available volumes during Ubuntu installation: [/FONT][https://imgur.com/a/hVMeAUC](https://imgur.com/a/hVMeAUC)[FONT=Whitney]

Instead of installing Ubuntu right away, I also clicked the "Try Ubuntu" option, ran GParted and came to this warning about my HDD: [/FONT][https://imgur.com/a/DEKE5A1](https://imgur.com/a/DEKE5A1)[FONT=Whitney]
The possible solutions I found online involved disabling safe boot, which I did, and checking if disk types were "dynamic", but they're already listed as "basic" in my PC. Other useful info regarding my notebook:-One SSD (100 GB) where Windows is installed-One HDD (1 TB) where everything else goes, including Ubuntu if this works out-UEFI-Disks are GPTHas anyone ever faced this issue or could guess what the problem is?For reference, I was trying to follow the guide displayed here: [/FONT][https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73](https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73)[FONT=Whitney]Thanks in advance![/FONT]

---

### Post by oldfred on 2022-09-20
Have you turned off fast start up in Windows? That sets hibernation flag on all NTFS partitions preventing the Linux NTFS driver from mounting them.
Note that Windows updates may turn fast start up back on, so later is issues, they may be the same issue.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Have you updated UEFI firmware & SSD firmware to latest available from vendor?
If Windows not hibernated, it may need chkdsk which you can only do from within Windows.

---

### Post by Impavidus on 2022-09-21
It looks like the partition resize of sdb wasn't properly written to disk. Try rebooting Windows and let it run some disk checks.

---

### Post by jbtz93 on 2022-09-21
Hey folks! Thanks for the quick replies.

> **oldfred said:**
> Have you turned off fast start up in Windows? That sets hibernation flag on all NTFS partitions preventing the Linux NTFS driver from mounting them.
Note that Windows updates may turn fast start up back on, so later is issues, they may be the same issue.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Turned it off, shut down the system, tried installing Ubuntu again, still no luck.

> Have you updated UEFI firmware & SSD firmware to latest available from vendor?

That seens a little bit extreme. Besides, I'm not an advanced user. I would like to try every other possible solution before doing that.

> If Windows not hibernated, it may need chkdsk which you can only do from within Windows.

Chkdsk returned no erros on both SSD and HDD.

---

### Post by oldfred on 2022-09-21
You did not mention brand/model system.
Windows  now often does an UEFI update in background & users do not know it occurred. And update often resets UEFI settings back to defaults, so any changes you make, you must redo.

Some systems also now can be updated from Ubuntu using fwupdate.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
Older systems that fwupdate does not support
[https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)

Many have posted that the UEFI update resolved issues with their system.

There also are these virus. Vendor have had to update UEFI/BIOS, kernels & drivers also have had to have updates. 
Spectre virus, repoline, RETBleed

---

### Post by tea for one on 2022-09-21
Do you have Bitlocker enabled on your Windows OS?
If not, can you boot into a live Ubuntu session, open a terminal and enter:-
```
sudo parted -l
```
Please post the output within code tags via Adv Reply.

---

### Post by jbtz93 on 2022-09-21
> **oldfred said:**
> You did not mention brand/model system.
Windows  now often does an UEFI update in background & users do not know it occurred. And update often resets UEFI settings back to defaults, so any changes you make, you must redo.

Some systems also now can be updated from Ubuntu using fwupdate.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
Older systems that fwupdate does not support
[https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)

Many have posted that the UEFI update resolved issues with their system.

There also are these virus. Vendor have had to update UEFI/BIOS, kernels & drivers also have had to have updates. 
Spectre virus, repoline, RETBleed

Hey Fred!

Sorry, model and brand should have been the first things I mentioned. I'm using an Acer Predator Helios 300 notebook. Its full specs can be found on the link below:

[https://kelaptop.com/en/acer-predator-helios-300-ph315-52-748u-nh-q62al-001](https://kelaptop.com/en/acer-predator-helios-300-ph315-52-748u-nh-q62al-001)

Not sure if this is relevant, but I still haven't updated my Windows from 10 to 11, although Microsoft sends me a warning to do so every now and then.

Because I tried every possible solution in the span of a single day, I believe it's unlikely that the UEFI updated and reseted any changes I made on the settings during this period.

Later today, I might try to format my HDD and see if that solves anything. Do you have any suggestions on how to safely do so? Also, maybe installing Ubuntu in it before anything else could be a recommended approach?

Note that the Ubuntu installer does detect my HDD and its storage capacity; the problem seens to be on the detection of the filesystem, preventing it from "seeing" the unallocated space I left there.

---

### Post by jbtz93 on 2022-09-21
Hi there, tea.

> **tea for one said:**
> Do you have Bitlocker enabled on your Windows OS?
If not, can you boot into a live Ubuntu session, open a terminal and enter:-
```
sudo parted -l
```
Please post the output within code tags via Adv Reply.

I did not find a BitLocker in my Windows OS. For some reason, I think it didn`t came with the default installation.

Here goes the output of the Ubuntu terminal...

```
Model: ATA ADATA_IM2S3338-1 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  106MB  105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB  16.8MB               Microsoft reserved partition  msftres
 3      123MB   127GB  127GB   ntfs         Basic data partition          msftdata
 4      127GB   128GB  544MB   ntfs                                       hidden, diag


Model: ATA WDC WD10SPZX-21Z (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Warning: failed to translate partition name
Number  Start   End     Size    File system  Name                   Flags 
 1      1049kB  135MB   134MB                                       msftres
 2      135MB   1000GB  1000GB               Pool de armazenamento


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  31.0GB  31.0GB  fat32        Main Data Partition  msftdata
```

---

### Post by tea for one on 2022-09-21
In post no.1, you mentioned 36GB of free space for Ubuntu, but there is no unallocated space on sda nor sdb?
Where do you intend to install Ubuntu?
You must use Windows (Disk Management) tools to reduce Windows partition size and create free space.
Reboot Windows to allow chkdsk to run.

---

### Post by jbtz93 on 2022-09-21
> **tea for one said:**
> In post no.1, you mentioned 36GB of free space for Ubuntu, but there is no unallocated space on sda nor sdb?
Where do you intend to install Ubuntu?
You must use Windows (Disk Management) tools to reduce Windows partition size and create free space.
Reboot Windows to allow chkdsk to run.

That`s the whole point. Neither Ubuntu installer or GParted are detecting the free space.

I did left 36gb unallocated in my HDD (using Windows Disk Management) as per screenshot: [https://imgur.com/a/ktAil8i](https://imgur.com/a/ktAil8i)

I want to install Ubuntu into that unallocated space.

I already ran chkdisk as well and it found no errors.

---

### Post by tea for one on 2022-09-21
Yes, in your image, I see the space in Disk 2 (1000GB) but what is Pool de armazenamento?

---

### Post by jbtz93 on 2022-09-21
> **tea for one said:**
> Yes, in your image, I see the space in Disk 2 (1000GB) but what is Pool de armazenamento?

I'm sorry, my system is in Portuguese. It means Storage Pool.

---

### Post by tea for one on 2022-09-21
For some unknown reason, gparted will not recognise this 1000GB disk although Windows identifies the partition as ntfs.
In post 8, you can see that both sda and sdc are recognised together with the respective Microsoft file systems.

Do you have a data back up of both disks?
If you have solid backups, then we can try to use other disk management tools.

---

### Post by jbtz93 on 2022-09-21
> **tea for one said:**
> For some unknown reason, gparted will not recognise this 1000GB disk although Windows identifies the partition as ntfs.
In post 8, you can see that both sda and sdc are recognised together with the respective Microsoft file systems.

Do you have a data back up of both disks?
If you have solid backups, then we can try to use other disk management tools.

My SSD only contains the Windows OS (which I can download an installation iso from Microsoft) and the HDD contains only local copies of files that are in the cloud, so it's ok.

Because the SSD seens to work fine with Ubuntu, I believe only the HDD would have to go through other disk management tools.

Looking forward to hearing your suggestions!

---

### Post by oldfred on 2022-09-21
Google told my your Pool is some sort of Windows Storage Spaces like a virtual space.
> You can use Storage Spaces to group two or more drives together in a  storage pool and then use capacity from that pool to create virtual  drives called storage spaces.

Is this something you did, or did system come from vendor.
Not familar with Storage Spaces or if you even can undo them?

---

### Post by jbtz93 on 2022-09-21
> **oldfred said:**
> Google told my your Pool is some sort of Windows Storage Spaces like a virtual space.


Is this something you did, or did system come from vendor.
Not familar with Storage Spaces or if you even can undo them?

Hmm... good point. I bought the notebook from someone else, and I myself formated it and created those partitions. Could be that I messed things up at some point, sure.

---

### Post by jbtz93 on 2022-09-21
Thank you all for the help, problem solved!

Turns out, it was definitely the "pool" thing. I removed my HD from the storage pool (which also required me to format that drive) and Ubuntu finally detected my unallocated space.

You can find a detailed guide on how to remove disks from the Windows Storage Pool here: [https://superuser.com/questions/1411233/can-we-add-a-linux-partition-on-a-drive-containing-a-windows-10-storage-pool?_gl=1*10kv492*_ga*Mjk1MjkyMTc2LjE2NjM3MTIwMTQ.*_ga_S812YQPLT2*MTY2MzgxMDM3MC4zLjEuMTY2MzgxMDQ4Mi4wLjAuMA]("https://superuser.com/questions/1411233/can-we-add-a-linux-partition-on-a-drive-containing-a-windows-10-storage-pool?_gl=1*10kv492*_ga*Mjk1MjkyMTc2LjE2NjM3MTIwMTQ.*_ga_S812YQPLT2*MTY2MzgxMDM3MC4zLjEuMTY2MzgxMDQ4Mi4wLjAuMA.")

---

### Post by MAFoElffen on 2022-09-21
I am in the middle of maintenance on my main workstation doing away with my old storage pools from Windows. Linux was not the deciding factor.

I heard that MS is going away from supporting Storage Spaces... Had been putting it off. Since the new Linux Kernels are supporting NTFS better now at the Kernel level, transforming them into NTFS drives that can share data between Windows and Linux.

---

