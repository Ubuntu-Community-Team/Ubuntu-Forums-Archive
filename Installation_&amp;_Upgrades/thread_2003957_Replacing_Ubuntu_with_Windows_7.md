---
title: "Replacing Ubuntu with Windows 7"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by DexusDaxus on 2012-06-14
So for awhile I was trying out Ubuntu 12.04 on a virtual PC. I decided after a month of working with it that I wanted to switch from Winodws 7 to Ubuntu. So like the idiot I am, instead of setting up a dual-boot, I installed Ubuntu over Windows 7 completely. After about two weeks of more messing around I decided that it just wasn't for me. I went to reinstall Windows 7 using a bootdisk but I got a partition error. Something about not being in the proper format to install? I want to get rid of Ubuntu and replace it with Windows 7 again. Thanks for reading! Also, it's x64-bit Ubuntu 12.04, if that helps. Also, I'm not in the least very tech-savvy.

---

### Post by critin on 2012-06-15
I don't believe Windows will install over ubuntu (as ubuntu does).  You'll need to format the disk for Windows, ntfs.  Then it should install cleanly.

Can you still get into ubuntu or is it gone already?  Using gparted you can format the disk.  If it's gone you can use a live linux cd--it will have gparted.

I'm not familiar with the Windows install disk.  Does it offer to format for you?

---

### Post by wilee-nilee on 2012-06-15
If it is the install disc for W7 make sure it is, it will reformat the whole HD and install without removing Ubuntu first.

It would ask you how you wanted done though in the install.

---

### Post by DexusDaxus on 2012-06-15
When I go to the directory to install Windows, I get two partitions:
Disk 0 Partition 1     Total Size: 927.5GB     Free Space: 0.0MB     Type: System
Disk 0 Partition 2     Total Size: 4.0GB          Free Space: 0.0MB     Type: Logical

It won't allow me to format either from there, and I get this error:

[I]"Windows cannot be installed to this disk. The selected disk has an MBR partition table. On EFI systems, Windows can only be installed to GPT disks.

Windows cannot be installed on this hard disk space. Windows must be installed to a partition formatted as NTFS.

Windows cannot be installed to this hard disk space. The partition is of an unrecognized type."

[/I]So I went ahead and installed GParted and I was given 3 partitions:
Partition:         File System:     Mount Point:   Size:   Used:   Unused:        Flags:
/dev/sda1       ext4                          /                         927.55GB       892.54GB      Boot
/dev/sda2             extended                        3.96GB           
    /dev/sda5         linux-swap                                                         3.96GB           

I can't unmount the first one because, [I]"Could not unmount /dev/sda1. The partition could not be unmounted from the following mount points:   /. Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

[/I]I can't unmount the other two. I really hope I'm not repeating too much of what you guys have already suggested.

---

### Post by darkod on 2012-06-15
1. You can't manipulate the partition from Gparted running from ubuntu on the same disk. Of course you can't unmount root since the system is running.
Use Gparted from live mode (Try Ubuntu) if you want to manipulate partitions. To unmount swap in live mode in Gparted, right-click, select Swapoff.

2. The windows installer told you, you can't use win7 with MBR (msdos) partition table with EFI boot mode. Linux can do that, but win7 needs gpt table to work with EFI. And you seem to have EFI boot.

Use the ubuntu cd to boot into live mode, open Gparted, unmount swap until all keys symbols are gone, then click in the menu Device - Create Partition Tables. Click on Advanced, select GPT table. That should change the disk to GPT table. NOTE: THIS WILL DESTROY ALL DATA ON THE DISK.
Click the green button on the Gparted toolbar to execute the changes.

Boot with the win7 dvd and try the install again.

---

### Post by coldraven on 2012-06-15
You cannot unmount a disk that you are working from. You have to boot with a Live CD or USB stick. Then run Gparted and delete all the partitions. Then try Windows again, it should see an empty disc and install OK.

---

### Post by jmore9 on 2012-06-15
When i use the whole disk for linux and then want to get rid of it and put windows back on i use the manufacturs cd to format the drive in question.  Works every time.  You could also try using a gparted live cd and format the whole drive that might work also i have never tried that,

---

### Post by wilee-nilee on 2012-06-15
> **darkod said:**
> 1. You can't manipulate the partition from gparted running from ubuntu on the same disk. Of course you can't unmount root since the system is running.
Use gparted from live mode (try ubuntu) if you want to manipulate partitions. To unmount swap in live mode in gparted, right-click, select swapoff.

2. The windows installer told you, you can't use win7 with mbr (msdos) partition table with efi boot mode. Linux can do that, but win7 needs gpt table to work with efi. And you seem to have efi boot.

Use the ubuntu cd to boot into live mode, open gparted, unmount swap until all keys symbols are gone, then click in the menu device - create partition tables. Click on advanced, select gpt table. That should change the disk to gpt table. Note: This will destroy all data on the disk.
Click the green button on the gparted toolbar to execute the changes.

Boot with the win7 dvd and try the install again.

+1

---

### Post by steve7777777 on 2012-06-15
> **jmore9 said:**
> When i use the whole disk for linux and then want to get rid of it and put windows back on i **use the manufacturs cd to format the drive in question**.  Works every time.  You could also try using a gparted live cd and format the whole drive that might work also i have never tried that,

Exactly. Download the CD image from the manufacturer and prepare the drive that way.

---

