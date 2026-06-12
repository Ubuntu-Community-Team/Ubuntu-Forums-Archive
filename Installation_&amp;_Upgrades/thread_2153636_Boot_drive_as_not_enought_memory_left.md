---
title: "Boot drive as not enought memory left"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2013-06-11
After updating my ubuntu via update manager i received the following message

#The voume "boot" has only 6.2 Mb left"

[ATTACH=CONFIG]243740[/ATTACH]

How can I free space in the Boot volume?
Thanks

---

### Post by ajgreeny on 2013-06-11
Let's see the output of ```
sudo fdisk -l
``` in terminal to see what partitions you have.  Do you know if you have a separarte /boot partition?

---

### Post by Kaizoku001 on 2013-06-12
> **ajgreeny said:**
> Let's see the output of ```
sudo fdisk -l
``` in terminal to see what partitions you have.  Do you know if you have a separarte /boot partition?

not too sure what to make of this, but here you are:

```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          978942  3907026943  1953024001    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          978944     4882431     1951744   82  Linux swap / Solaris
/dev/sda6         4884480   102539263    48827392   83  Linux
/dev/sda7       102541312  3907026943  1902242816   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb21b0174

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065  3907024064  1953504000    f  W95 Ext'd (LBA)
/dev/sdc5           16128  3907024064  1953503968+   7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000caf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdd2          206848   409591807   204692480    7  HPFS/NTFS/exFAT
/dev/sdd3       409593240  3907024064  1748715412+   7  HPFS/NTFS/exFAT

Disk /dev/sdf: 15.7 GB, 15728640000 bytes
64 heads, 32 sectors/track, 15000 cylinders, total 30720000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdf2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdf3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdf4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b3c257c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   976768064   488384001    7  HPFS/NTFS/exFAT


```
yes i belive my boot partion is seperat.

---

### Post by ajgreeny on 2013-06-12
It's difficult to be sure as you have so many disks, one of which, sdb, is formatted using GPT partition(s).  However, it looks as if sda1 may be your /boot partition.  Can you boot to ubuntu, or use a live system if that is a problem, install gparted and then show us screenshots of the gparted window for each separate disk, as that will show how fully used each partition is, and perhaps give a clue to which is your problem partition.  The output of ```
sudo parted -l
mount
``` may also help.

---

### Post by gordintoronto on 2013-06-12
At boot time, select the option which will display all the kernel versions you have installed. Write down on a piece of paper enough that you can search for each one, for Ubuntu 12.04 this might be:
0-38
0-39
0-42
etc.

Press ESC to get back to the first Grub menu, and boot into the latest kernel.

Install Synaptic Package Manager. Run Synaptic, and search for "0-38" or whatever your oldest kernel is. It should display about a dozen results, three of which are installed. For those, select "completely remove." Then Apply. Keep the latest two or three kernels, get rid of all the others. Finally, open Terminal and enter this command:
sudo update-grub

---

### Post by ajgreeny on 2013-06-12
You can easily see what kernel versions you have installed with command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` and then completely remove the old ones using synaptic, leaving just two numbered versions, similar to what gordintoronto said.  My command simply means there is no need to reboot or look for the installed kernels in the menu at boot time.

---

### Post by Kaizoku001 on 2013-06-26
> **ajgreeny said:**
> You can easily see what kernel versions you have installed with command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` and then completely remove the old ones using synaptic, leaving just two numbered versions, similar to what gordintoronto said.  My command simply means there is no need to reboot or look for the installed kernels in the menu at boot time.

Ok I ran the code an this is what i got:
```
menuentry 'Ubuntu, with Linux 3.2.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 2.6.38-14-generic (on /dev/sdb3)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sdb3)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.38-13-generic (on /dev/sdb3)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sdb3)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb3)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sdb3)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdb3)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdb3)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb3)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb3)" --class gnu-linux --c
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {


```

when i look at Synaptic for one of the numbers i get the folloiwng screen:

[ATTACH=CONFIG]244201[/ATTACH] 

now do i chose remove or permenantly remove?
do I click on eache of the highlithed itemens? or just the generic ones.
kind of nervous about removing this :)

advice apreciated.

---

### Post by efflandt on 2013-06-26
For now search "linux" in synaptic and mark to **Remove** any **linux-image-generic** and **Completely remove** any **linux-headers** (which also removes same version **linux-headers-generic**) for any version that is **3.2.0-40 or lower**. Once you are able to install most recent kernel (mine is 3.2.0-48) you could also remove the 0.41 version if you want to. Just keep 1 or 2 old kernel versions in case a new version does not work for some reason (never had that problem). That should automatically update-grub unless with so many drives you are booting from a different grub (in which case you may need to sudo update-grub for that one).

---

### Post by gordintoronto on 2013-06-26
For the displayed screen. you can "completely remove" all three of the installed files. By my count, you can get rid of 20 old versions. probably three files each, totalling about 5 GB of disk space in your root partition. (It will save space in Boot, but I don't know how much.) Then run: sudo update-grub

As efflandt said, you can then install 3.2.0-48.

---

### Post by Kaizoku001 on 2013-06-26
Worked like a charme.

Thanks

---

