---
title: "Can I expand the Ubuntu partition if it's mounted as a pseudo-device?"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by MidnightJava on 2011-10-08
I installed Ubuntu as a guest OS in the Windows installation that came with my HP computer, by downloading and running the Windows installer for Ubuntu. It created a 30GB partition, but it seems this is actually a pseudo-device whose contents are physically within the Windows partition. From  Ubuntu I see my Windows 7 files at /host. Using gparted I see only  Windows partitions (the System, OS, and Recovery partitions at  /dev/sda1, /dev/sda2, and /dev/sda3. respectively). Running df on the  Ubuntu system, I see /host mounted on /dev/sda2, and / mounted on  /dev/loop0.

So I have several questions?

1. Is there any way to expand the size of the pseudo-device on which / is mounted, so I can use more of the Windows partition for Ubuntu?

2. I want to install VirtualBox, with Ubuntu as the host and Windows 7 as the guest. I want to follow the instructions [here]("https://forums.virtualbox.org/viewtopic.php?t=33356") to create a raw disk in VB that points to the existing Windows partition, so I can boot Windows native or in the VM. Can that work with my installation configuration? I asked that question on the VirtualBox forum, but I'd like to also get an answer from an Ubuntu perspective.

3. Do I need to install Ubuntu in its own partition to accomplish 1 and 2 above? If not, is there some other reason I might want to do that?

I'm fairly new to Ubuntu, and have been running it for several months. I just downloaded and ran the Windows installer because it seemed like the easiest way to get Ubuntu in a dual boot configuration with Windows. But if I have an installation configuration that's going to limit what I can do in the future, I'd like to change it now, before I get even further along using the current installation.

---

### Post by coffeecat on 2011-10-09
> **MidnightJava said:**
> But if I have an installation configuration that's going to limit what I can do in the future, I'd like to change it now, before I get even further along using the current installation.

I'll take this point first. If I was in your situation, I'd abandon the current Ubuntu system and start afresh with Ubuntu installed natively to its own partition. What you have is a wubi installation.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

It's a perfectly good way of using Ubuntu for a short while but, yes, it is limiting. If you do want to try to resize the Ubuntu pseudo-partition (the C:\ubuntu\disks\root.disk file), you could try this:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

As to your question about installing VirtualBox in Ubuntu, that is not a thing I would want to try in wubi. A wubi install runs significantly slower than a native installation and a guest system in VirtualBox runs slow anyway, so you'd be doubly disadvantaged. Added to which I doubt whether pointing the host Windows partition back to be the guest in VirtualBox would be doable. You would be closing a circle, which would be eccentric if nothing else. :)

Last point. You have a Hewlett-Packard machine. HP have an irritating habit of using up the full complement of 4 primary partitions allowed in an mbr partition table, or at least with Windows 7 systems - although this doesn't appear to be the case from the information you've already posted. This needs to be dealt with if you want to install Linux to its own partition(s). Which version of Windows is installed? Also, from Ubuntu post the output of these terminal commands:

```
sudo fdisk -lu
sudo blkid
```

We'll get a better overview of your partition layout with that.

---

### Post by MidnightJava on 2011-10-09
Thanks for the explanation. You've confirmed my suspicions, and I'll install Ubuntu in its own partition. The HP came with Windows 7 Home Edition. I do only see the three partitions I mentioned. What do they usually install in the fourth partition?

Here's the output of the two commands you requested I run. As you may assume from the label, the sdb device is my backup disk.

```
ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x801f4319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   637943807   318868480    7  HPFS/NTFS
/dev/sda3      1224960000  1250260991    12650496    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaefbb026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625142447   312571192+   b  W95 FAT32
mal@ubuntu:~$ sudo blkid
/dev/loop0: UUID="b48d1b04-84e2-432b-860c-e633291d463e" TYPE="ext4" 
/dev/sda1: LABEL="SYSTEM" UUID="F8C4B13FC4B100C4" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="36AA701CAA6FD6C1" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="6CEAF910EAF8D774" TYPE="ntfs" 
/dev/sdb1: LABEL="BACKUP" UUID="7EF5-1DEE" TYPE="vfat" 
ubuntu:~$ 

```

---

### Post by coffeecat on 2011-10-09
> **MidnightJava said:**
> The HP came with Windows 7 Home Edition. I do only see the three partitions I mentioned. What do they usually install in the fourth partition?

You're lucky! Judging by the number of threads started about this and my own experience of a HP machine, you must have got hold of the only HP in the known Universe with Windows 7 and less than 4 partitions. :)

The fourth partition would have been a tiny FAT32 one with the label HP_TOOLS. I simply copied the contents to my C: partition and deleted it.

> **MidnightJava said:**
> ```
ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x801f4319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   637943807   318868480    7  HPFS/NTFS
/dev/sda3      1224960000  1250260991    12650496    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaefbb026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625142447   312571192+   b  W95 FAT32
```

sda1 is your Windows 7 boot partition, sda2 the C: partition and sda3 the recovery partition. Your easiest option would be to shrink the sda2 C: partition and then create an extended partition in the freed space. You could then create as many logical partitions as you need in the extended. Linux is happy booting from a logical partition unlike Windows, and you could also create a NTFS data partition as a logical partition to be shared by the two OSs if you want. Windows will be happy with a logical data partition.

If you need help with the partitioning, don't hesitate to post back. I'd advise you to use Windows' own Disk Management utility to shrink the C: partition (that's safer than using Gparted), but use Ubuntu's Gparted to create the extended/logical partitions. If you use Windows Disk Management there is a danger that it will convert all your partitions into dynamic ones, and then you'll be up a creek with just a leaf for a paddle as far as running Ubuntu is concerned.

---

### Post by MidnightJava on 2011-10-09
Thanks. I did already shrink the Windows C: partition as far as I could. I should be able to shrink it further after I remove the Ubuntu pseudo-device. But I'll wait until I have Ubuntu installed along-side Windows. Then I'll remove wubuntu, shrink the Windows partition, and grow the Ubuntu partition. I did use the Windows utility to shrink the C: partition. It was nice, because it figured out for me how far I could shrink it, and helped me to see whether a defrag would help.

I just went to the Ubuntu dowload page and saw that the 32-bit version is tagged as recommended. Is this actually preferable even though I have a 64-bit OS, or is it recommended just so people who don't know what they have will be good with the 32-bit version no matter what?

---

### Post by coffeecat on 2011-10-09
I missed that you had already shrunk the Windows partition - the output of fdisk was clear if I had read it properly!

This business about the 32-bit version of Ubuntu being recommended on the ubuntu.com page is the big mystery. I guess your last thought is the right one. If you have a 64-bit processor and at least 2-3 GB RAM then I suggest you go for the 64-bit version. 

By the way, don't forget that you need more than one partition for Ubuntu, which is why you need to create an extended partition. Although you can use a swap file, the usual setup in Ubuntu is to have a separate swap partition.

---

### Post by MidnightJava on 2011-10-10
I created an extended partition with three logical partitions: an ext2-formatted partition for Ubuntu data, a unix-swap-formatted partition for Ubuntu swap, and an NTFS-formatted partition for shared data.

In the Ubuntu installation wizard, I did not choose the option "Install Ubuntu along-side Windows". Instead I chose "Something Other", assuming that would enable me to specify the partitions for data and swap directly.

On the next wizard page, I selected the Ubuntu data partition for installation. There was a drop-down menu for "Device for boot loader installation", with available options: /dev/sda, /dev/sda1, /dev/sda2, /dev/sda3, /dev/sda5, /dev/sda6, /dev/sda7. I wasn't sure which to choose, and was concerned that if I chose the one that contains the current Windows boot loader, I'd over-write the current BCD. So I chose /dev/sda, since it refers to the entire disk, assuming the installer would choose the correct partition.

When I clicked "Install", I got an error message " No root file system is defined. Please correct this from the partitioning menu." There was a column for mount point in the partition table presented by the wizard; but there were no values in it for any partition, and it was not editable.

Did I take the wrong path when I chose "Something Other", or am I missing something else?

---

### Post by coffeecat on 2011-10-10
"Something else" is the correct option. I'm not quite sure what you mean by an ext2 for Ubuntu data. If you are going to have a NTFS partition for shared data between Windows and Ubuntu, you don't really need a data partition formatted with a Linux filesystem. Nevertheless, this seems to be what you tried to choose for installing Ubuntu to. Apart from the NTFS partition, the minimum partitions in your extended partition would be a swap partition and an ext4 partition for the Ubuntu root partition. The shorthand for a root partition is '/'. 

Assuming your ext2 partition is large enough, in the something else option, highlight it and click on 'change'. Choose ext4 for filesystem, it doesn't matter whether you re-format it or not if it's freshly created, and then in mountpoint choose '/'. My guess is that it was the last bit you omitted. You don't need to do anything with the swap partition you've created - the installer will detect and set that up automatically.

Installing grub to /dev/sda is correct. Some grub code will go to the mbr replacing the Windows bootloader, and some is held in the Ubuntu root partition. You will be able to boot Windows from the grub menu. Don't worry that grub code overwrites the Windows mbr bootloader. If you ever need to revert your machine back to a Windows only one, it is easy to re-install the Windows code from a Windows 7 repair disc. By the way, if you haven't done so already, make a repair CD from within Windows. This is different from the HP recovery DVDs which you may already have made. If you type "repair" in the search box in Windows 7, the system will prompt you. It's also possible to re-install the equivament of the Windows bootloader from an Ubuntu live CD.

I should have posted this link before. Much of it you will understand already but there's some useful stuff about partitioning for Ubuntu:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by MidnightJava on 2011-10-10
OK, I was able to get Ubuntu installed in the partition I created. I didn't notice the right-click menu, which was what I needed to enter the mount point. I was just clicking on the partition table record. When I said Ubuntu Data partition, I should have said Ubuntu Root partition. I originally formatted it as ext2 because only ext2 and ext3 were mentioned in the gparted documentation. But I changed it to ext4 per your suggestion, and after entering the mount point I was able to do the installation.

I was able to boot into Ubuntu. I saw the grub entries for Windows, but haven't verified booting into Windows yet. However, I thought I'd be able to boot into the previously-installed Ubuntu installation as well, but I don't see a grub entry for it. Is it possible to do that? If not, perhaps I can mount the pseudo-device /dev/loop0 from the new Ubuntu installation, and then grab the data that I'd like to keep, before removing the old Ubuntu installation. I didn't get a chance to try that before leaving the house today.

I also have two related questions.

1. From Ubuntu I was able to mount the shared partition I created. But I noticed that the backup drive device sdb was already mounted when I booted into Ubuntu. Is there something I should do in the partition table to cause the shared partition to be automatically mounted?

2. How should I remove the old Ubuntu installation when I'm ready? I assume I could delete the C:\ubuntu\disks\root.disk file; but should I do something to the /dev/loop0 device as well? Or maybe there's a windows uninstaller for wubi. Didn't think about looking at that before leaving the house today as well.

---

### Post by coffeecat on 2011-10-10
> **MidnightJava said:**
> However, I thought I'd be able to boot into the previously-installed Ubuntu installation as well, but I don't see a grub entry for it. Is it possible to do that?

Yes, but what I am about to tell you sounds weird. Select Windows from the grub menu that first appears. You will then get the white on black Windows bootloader menu for selecting either Windows or Ubuntu, where this Ubuntu is your wubi install. If you boot into this Ubuntu and then run update-grub, next time after the Windows boot menu you'll get yet another grub menu from which.... :wink:

> **MidnightJava said:**
>  If not, perhaps I can mount the pseudo-device /dev/loop0 from the new Ubuntu installation, and then grab the data that I'd like to keep, before removing the old Ubuntu installation. I didn't get a chance to try that before leaving the house today.

You can - the method is in the Ubuntu wiki article that I linked earlier. But probably easiest is to boot into the wubi Ubuntu and copy your files to your new NTFS data partition. 

> **MidnightJava said:**
> 1. From Ubuntu I was able to mount the shared partition I created. But I noticed that the backup drive device sdb was already mounted when I booted into Ubuntu. Is there something I should do in the partition table to cause the shared partition to be automatically mounted?

Already plugged in USB devices are automounted on bootup. Internal partitions are not by default, but are easily mounted with one mouse-click as you've discovered. The way to get internal partitions mounted on bootup is to add a line to the configuration file /etc/fstab. There are GUI utilities in the repositories for this but I would advise keeping them all at arm's length. They've all been unmaintained for years and are buggy. If you post the output of these two commands I can let you have a line for /etc/fstab:

```
sudo fdisk -lu
sudo blkid
```

> **MidnightJava said:**
> 2. How should I remove the old Ubuntu installation when I'm ready? I assume I could delete the C:\ubuntu\disks\root.disk file; but should I do something to the /dev/loop0 device as well? Or maybe there's a windows uninstaller for wubi. Didn't think about looking at that before leaving the house today as well.

You simply uninstall the wubi installation from Windows control panel as though you were uninstalling an application. The exact method is in the two links I provided earlier.

---

### Post by MidnightJava on 2011-10-11
OK, thanks again for the excellent help. I booted into Windows and the wubi installation, and everything is as expected. Now I'm ready to install VirtualBox and create the raw partition, and I'm really glad I didn't try to do that with the wubi installation.

I didn't get a chance to play with fstab yesterday, but I looked it up just now, and it seems pretty straightforward. It looks like I need the following line for auto-mounting my shared NTFS partition:

```
/dev/sda7        /shared        ntfs        auto        0  0
```Here's the output of the Linux commands you gave me, so you can double-check me.

```
[COLOR=black][FONT=&quot] s5610f:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x801f4319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   637943807   318868480    7  HPFS/NTFS
/dev/sda3      1224960000  1250260991    12650496    7  HPFS/NTFS
/dev/sda4       637945854  1224959999   293507073    5  Extended
/dev/sda5       637945856  1208575999   285315072   83  Linux
/dev/sda6      1208578048  1214719999     3070976   82  Linux swap / Solaris
/dev/sda7      1214722048  1224959999     5118976    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaefbb026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625142447   312571192+   b  W95 FAT32
[/FONT][/COLOR][COLOR=black][FONT=&quot]s5610f:~$
[/FONT][/COLOR][COLOR=black][FONT=&quot]s5610f:~$
[/FONT][/COLOR][COLOR=black][FONT=&quot]s5610f:~$[/FONT][/COLOR]
[COLOR=black][FONT=&quot] s5610f:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="F8C4B13FC4B100C4" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="36AA701CAA6FD6C1" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="6CEAF910EAF8D774" TYPE="ntfs" 
/dev/sda5: UUID="5ebb92a5-b015-4a90-b55a-48a521237010" TYPE="ext4" 
/dev/sda6: UUID="cebc1c17-cd2f-4ccb-be81-20f81b659957" TYPE="swap" 
/dev/sda7: LABEL="Shared" UUID="1FF344F316D8343E" TYPE="ntfs" 
/dev/sdb1: LABEL="BACKUP" UUID="7EF5-1DEE" TYPE="vfat" [/FONT][/COLOR]
```

---

### Post by coffeecat on 2011-10-11
If you mount your ntfs partition to a folder called shared, you won't get an icon on the desktop and/or the Unity launcher, which is may be what you prefer, and you would have to access it through File System in nautilus. If you make your mountpoint in the /media folder, you get an icon, which I prefer. So, first, you need to make your mountpoint. Either:

```
sudo mkdir /shared
```

Or:

```
sudo mkdir /media/shared
```

In your fstab line it doesn't matter whether you use "ntfs" or "ntfs-3g" in the third field - they will both invoke the ntfs-3g driver. You'd be better off with the UUID in the first field, and your options need to be different. I would suggest:

```
UUID=1FF344F316D8343E     /media/shared     ntfs-3g     defaults,locale=en_US.utf8     0  1
```

Change /media/shared to /shared if you want to mount in /shared and you may need to change the locale to your own. The command "locale -a" will give you a complete list. In my case I would have "locale=en_GB.utf8"

You probably know this, but to edit fstab with root privileges:

```
gksudo gedit /etc/fstab
```

---

### Post by MidnightJava on 2011-10-13
Well it seems I have another installation problem. When I created my VirtualBox VM with a raw disk pointing to my existing Windows7 installation, part of the process I was following from a forum post involved copying the MBR from the Windows partition into the VM and then running bootrec /FixMbr from a Windows recovery disk to restore the MBR.

This worked fine for restoring the Windows boot loder, but it wiped out grub. I only had boot records for Windows and wubi,. So I downloaded Boot-Repair and ran the recommended repair. This restored my Ubuntu boot loader and wiped out the Windows boot loader. There are no Windows entries in grub now, just two versions of Ubuntu and the recovery boot loader.

I know these two OSs can co-exist, but I seem to be in an infinite loop. Is there a way to tell grub to add a  boot record for Windows? I assume grub would do that without blowing itself away, which seems to be the effect of Windows installing its boot loader.

---

### Post by coffeecat on 2011-10-13
> **MidnightJava said:**
> Is there a way to tell grub to add a  boot record for Windows?

Yes, run "sudo update-grub". **However**, the Windows entry would not have disappeared spontaneously and what I fear is that somewhere along the line update-grub has been run but that the Windows boot files in the boot sector of the Windows partition have been damaged or removed. The update-grub script looks for Windows boot files to identify a Windows OS partition.

Try running "sudo update-grub" first. If that doesn't restore the Windows entry to grub, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script in Ubuntu and post the contents of the RESULTS.txt file in code tags.

---

### Post by MidnightJava on 2011-10-13
Yes, it was as you surmised. After running update-grub there are still no windows boot loaders found. Here are the results of the boot-info script.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   637,943,807   637,736,960   7 NTFS / exFAT / HPFS
/dev/sda3       1,224,960,000 1,250,260,991    25,300,992   7 NTFS / exFAT / HPFS
/dev/sda4         637,945,854 1,224,959,999   587,014,146   5 Extended
/dev/sda5         637,945,856 1,208,575,999   570,630,144  83 Linux
/dev/sda6       1,208,578,048 1,214,719,999     6,141,952  82 Linux swap / Solaris
/dev/sda7       1,214,722,048 1,224,959,999    10,237,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   625,142,447   625,142,385   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F8C4B13FC4B100C4                       ntfs       SYSTEM
/dev/sda2        36AA701CAA6FD6C1                       ntfs       OS
/dev/sda3        6CEAF910EAF8D774                       ntfs       HP_RECOVERY
/dev/sda5        5ebb92a5-b015-4a90-b55a-48a521237010   ext4       
/dev/sda6        cebc1c17-cd2f-4ccb-be81-20f81b659957   swap       
/dev/sda7        1FF344F316D8343E                       ntfs       Shared
/dev/sdb1        7EF5-1DEE                              vfat       BACKUP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/BACKUP            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8C4B13FC4B100C4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CEAF910EAF8D774
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   8.178569794 = 8.781672448    boot/grub/grub.cfg                             1
   2.061828613 = 2.213871616    boot/initrd.img-2.6.38-10-generic              2
  14.045360565 = 15.081091072   boot/initrd.img-2.6.38-11-generic              2
  26.629467010 = 28.593172480   boot/initrd.img-2.6.38-8-generic               2
  13.734687805 = 14.747508736   boot/vmlinuz-2.6.38-10-generic                 2
  13.564765930 = 14.565056512   boot/vmlinuz-2.6.38-11-generic                 1
   0.421875000 = 0.452984832    boot/vmlinuz-2.6.38-8-generic                  2
  14.045360565 = 15.081091072   initrd.img                                     2
   2.061828613 = 2.213871616    initrd.img.old                                 2
  13.564765930 = 14.565056512   vmlinuz                                        1
  13.734687805 = 14.747508736   vmlinuz.old                                    2

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ebb92a5-b015-4a90-b55a-48a521237010

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-11-generic
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-11-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro  single
initrd        /boot/initrd.img-2.6.38-11-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8C4B13FC4B100C4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CEAF910EAF8D774
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cebc1c17-cd2f-4ccb-be81-20f81b659957 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 312.330825806 = 335.362670592  boot/grub/core.img                             1
 312.335144043 = 335.367307264  boot/grub/grub.cfg                             1
 554.339977264 = 595.218018304  boot/grub/menu.lst                             1
 312.331516266 = 335.363411968  boot/grub/stage2                               1
 305.950748444 = 328.512114688  boot/initrd.img-2.6.38-11-generic              2
 305.243164062 = 327.752351744  boot/initrd.img-2.6.38-8-generic               2
 305.579414368 = 328.113397760  boot/vmlinuz-2.6.38-11-generic                 1
 312.329105377 = 335.360823296  boot/vmlinuz-2.6.38-8-generic                  1
 305.950748444 = 328.512114688  initrd.img                                     2
 305.243164062 = 327.752351744  initrd.img.old                                 2
 305.579414368 = 328.113397760  vmlinuz                                        1
 312.329105377 = 335.360823296  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  4c 18 85 ea 79 18 cf a5  11 77 f5 26 4b 42 37 1d  |L...y....w.&KB7.|
00000010  55 5b 90 84 13 eb 54 27  38 5d e4 fd d6 38 c0 f6  |U[....T'8]...8..|
00000020  a1 73 73 5d 99 34 ec 73  b7 52 44 7e 62 1b 76 06  |.ss].4.s.RD~b.v.|
00000030  79 ef 9c d7 9e f8 82 df  7c 6e 43 10 4a 9c fe 5f  |y.......|nC.J.._|
00000040  ca b5 52 d7 52 55 f4 b9  f3 ff 00 88 35 64 2a e8  |..R.RU......5d*.|
00000050  91 e1 c8 60 1b de bc e5  6c 9c 79 93 9d b9 2c 4e  |...`....l.y...,N|
00000060  e0 79 66 e7 fc fe 34 aa  d1 d9 a6 69 28 ab 26 9e  |.yf...4....i(.&.|
00000070  87 86 f8 a4 49 e6 e7 70  00 92 7e 51 d7 93 d6 b9  |....I..p..~Q....|
00000080  45 2c ec 8e 47 4d c0 fe  95 ce ae cd 2e ad 6f 22  |E,..GM........o"|
00000090  47 c0 84 1e 87 9c 7b d5  0d e4 b9 00 67 38 04 fd  |G.....{.....g8..|
000000a0  69 24 ee 63 66 6a db b9  7d c0 0e 84 1c 01 d7 ad  |i$.cfj..}.......|
000000b0  23 da bc 50 90 fb b2 33  8f 63 ff 00 ea a4 d6 ba  |#..P...3.c......|
000000c0  9a d9 f5 2a cc ab f6 84  c3 12 59 72 07 bf 19 ae  |...*......Yr....|
000000d0  8c 69 d2 aa ef 41 9c 2b  01 f8 d6 89 be 80 b5 7a  |.i...A.+.......z|
000000e0  13 a4 72 c6 78 71 92 00  1f 9f 4f f1 a5 5b e9 5a  |..r.xq....O..[.Z|
000000f0  76 60 73 c9 c6 3e b8 35  2e db 32 ad 77 6b 9d 2e  |v`s..>.5..2.wk..|
00000100  8d 3e e9 94 92 ca 43 15  18 ed 9f ff 00 55 7d 1f  |.>....C......U}.|
00000110  f0 f2 4f 31 94 16 39 00  e7 27 dc e2 92 96 9a 77  |..O1..9..'.....w|
00000120  36 4d e9 ae c7 bf 35 ab  a4 44 02 0e 57 a6 7f 5a  |6M....5..D..W..Z|
00000130  93 c1 e4 7d b9 90 af 1b  89 fa fb ff 00 3a ce 54  |...}.........:.T|
00000140  e2 dd fb 1a a8 a9 36 d7  63 d7 55 4e d1 91 c0 19  |......6.c.UN....|
00000150  18 fa d6 84 10 6e 40 0f  7c e0 fa 73 4a 3d 75 37  |.....n@.|..sJ=u7|
00000160  d9 6a 50 58 a5 0e 08 07  e5 62 6b 45 2e a4 5c 7c  |.jPX.....bkE..\||
00000170  a4 9e 3b f6 ac 5c 2d 26  de cc 94 9d d9 61 2f 65  |..;..\-&.....a/e|
00000180  39 50 9f c4 05 58 6d 50  a4 60 94 fb dc 11 9e 9d  |9P...XmP.`......|
00000190  6b 48 c5 de cb 61 a7 25  a0 91 6b 8a 50 fe ed b9  |kH...a.%..k.P...|
000001a0  63 df ad 3b fb 71 a2 40  56 22 d9 07 23 1d 38 c5  |c..;.q.@V"..#.8.|
000001b0  5b 8a 4e c2 77 ea 71 52  0d 4e ee e8 dc 3c 00 fe  |[.N.w.qR.N...<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 03 22 00 fe  |........... ."..|
000001d0  ff ff 05 fe ff ff 02 20  03 22 00 c0 5d 00 00 00  |....... ."..]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 40 20 00  |.X.BSD  4.4..@ .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  71 ea 42 25 05 2a 01 00  00 00 00 00 02 00 00 00  |q.B%.*..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ee 1d f5 7e 42  41 43 4b 55 50 20 20 20  |..)...~BACKUP   |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


```

---

### Post by MidnightJava on 2011-10-13
A bit more info: I noticed this in the RESULTS file

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8C4B13FC4B100C4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CEAF910EAF8D774
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```And remembered that there was en entry on the grub screen for something like "Chainloader into grub2". So I tried booting into that entry, and I got the error "Error 11: Unrecognized Device Name"

---

### Post by MidnightJava on 2011-10-13
Well the problem is getting stranger. I re-booted to double-check that I quoted the error message accurately above. Previously to get the boot menu I hit the ESC key on the original blue screen as the system was preparing to boot, and I would be taken to a black and white menu, which I think was a grub menu. It wasn't the same style as the black and white Windows menu I used to get when I wanted to boot either Windows or wubi, but it also wasn't the Ubuntu-styled menu I used to get as well (with the same background color as Ubuntu default desktop).

But now when I hit the ESC key, I'm taken to a blue menu that looks like a DOS menu. It says to choose a device, from the following options:

WDC WD6400AAKS-65Z2B0
hp DDVDW TS-H653R
Realtek PXE B03 D00
WD My Book

If I choose either of the first three, it loads grub and boots into Ubuntu in /dev/sda5. If I choose the last one, it goes to a black screen and nothing further happens.

---

### Post by coffeecat on 2011-10-13
You have a strange mixture of legacy grub and grub 2 in your Ubuntu installation. The grub menu you are seeing is the legacy grub menu. This may be the work of "boot-repair", whatever that is. It has seriously muddled the situation. I'll get back to you. Need to check something.

---

### Post by MidnightJava on 2011-10-13
Thanks for looking into it. FYI Boot-Repair came from an Ubuntu support page found [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). It was the first hit when I googled "Ubuntu fix boot loader". I followed the instructions under the heading "Using the Ubuntu CD (Recommended)" booting into the Ubuntu installation disk and then using the following apt-get commands per instructions given when I clicked the Boot-Repair link

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by coffeecat on 2011-10-13
I've not been in this situation. I think the best way around this is to re-install grub2 to the mbr with the liveCD/USB and then purge legacy grub after that. I'm 90% confident that is the way to go, but not 100%, tbh. The person I was hoping to involve is not on-line at the moment, but let's see what we can do and if it doesn't work, I'll call in a second opinion.

Boot up with the 11.04 live CD (or live USB). If you use a live USB, check that your main 640GB drive still appears as sda with "sudo fdisk -lu".

Open a terminal, and:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see if you get the grub2 menu with the Windows entries. Check that you can boot into both Windows and Ubuntu and then we'll see about purging legacy grub.

---

### Post by coffeecat on 2011-10-13
> **MidnightJava said:**
> Thanks for looking into it. FYI Boot-Repair came from an Ubuntu support page found [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Curious. That looks fine and the boot-repair documentation says that it can fix grub2. Whatever - it's legacy grub that's getting in the way, so hopefully from my previous post we'll be able to get you back to the grub2 menu.

---

### Post by MidnightJava on 2011-10-13
I tried to do this before leaving for work today, but was unable to boot into the live CD. I've found it to be quite sensitive, even though I burned it at the slowest speed, per the web site instructions. When I did the original install, I had a CPU panic the first time I tried it, a system hang the second time, and the third time was the charm. This morning, it loaded the main screen and after I clicked "Try Ubuntu" it went to a black screen and I gave up after 10 minutes and rebooted. This time when I clicked "Try Ubuntu" I was able to set up my wireless network connection and access other items in the main menu, but the spinning ball never stopped and the main screen never went away, even after 20 min or so. I think maybe I need to power the computer all the way down before booting it, and I'll try that this evening.

As for Boot-Repair, in hind sight something was a bit odd when I installed it using apt-get. While the packages were loading, suddenly a window popped up titled "Boot-Repair" and asked me if I wanted to run the recommended repair. I was expecting to launch it manually, and was going to follow the instructions on the web page regarding which option to execute. Maybe the auto-launch took me down a different path.

I'll post tomorrow with results of the grub commands. Thanks again for all your efforts and expertise.

---

### Post by coffeecat on 2011-10-13
CDs can be a bit iffy in my experience. If one misbehaves I usually simply burn another one. Something as simple as a bit of dust can cause misreads and weird happenings. I prefer to make bootable USB pendrives, but you do have to be careful with the hard drive designation if you do. With some BIOS's the pendrive comes out as sda.

---

### Post by MidnightJava on 2011-10-14
Running those grub commands seems to have worked. I was able to boot into Ubuntu from the grub2 screen that comes up after the BIOS loads, and I can select the Windows entry from grub2 and I get the secondary screen with Windows and wubi, and successfully boot into Windows. Windows found it necessary to run CHKDSK the first time, but no errors were found.

One minor difference is that I don't see the additional Ubuntu boot entry I used to see, for an earlier version of Ubuntu. I never used that, but I'm curious if that is something always there, or another off-nominal feature of my installation.

I ran boot-info script again and pasted the results below, in case that's needed for getting rid of legacy grub.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   637,943,807   637,736,960   7 NTFS / exFAT / HPFS
/dev/sda3       1,224,960,000 1,250,260,991    25,300,992   7 NTFS / exFAT / HPFS
/dev/sda4         637,945,854 1,224,959,999   587,014,146   5 Extended
/dev/sda5         637,945,856 1,208,575,999   570,630,144  83 Linux
/dev/sda6       1,208,578,048 1,214,719,999     6,141,952  82 Linux swap / Solaris
/dev/sda7       1,214,722,048 1,224,959,999    10,237,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   625,142,447   625,142,385   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F8C4B13FC4B100C4                       ntfs       SYSTEM
/dev/sda2        36AA701CAA6FD6C1                       ntfs       OS
/dev/sda3        6CEAF910EAF8D774                       ntfs       HP_RECOVERY
/dev/sda5        5ebb92a5-b015-4a90-b55a-48a521237010   ext4       
/dev/sda6        cebc1c17-cd2f-4ccb-be81-20f81b659957   swap       
/dev/sda7        1FF344F316D8343E                       ntfs       Shared
/dev/sdb1        7EF5-1DEE                              vfat       BACKUP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/BACKUP            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 36AA701CAA6FD6C1
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=36AA701CAA6FD6C1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8C4B13FC4B100C4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CEAF910EAF8D774
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   8.178569794 = 8.781672448    boot/grub/grub.cfg                             1
   2.061828613 = 2.213871616    boot/initrd.img-2.6.38-10-generic              2
  14.045360565 = 15.081091072   boot/initrd.img-2.6.38-11-generic              2
  26.629467010 = 28.593172480   boot/initrd.img-2.6.38-8-generic               2
  13.734687805 = 14.747508736   boot/vmlinuz-2.6.38-10-generic                 2
  13.564765930 = 14.565056512   boot/vmlinuz-2.6.38-11-generic                 1
   0.421875000 = 0.452984832    boot/vmlinuz-2.6.38-8-generic                  2
  14.045360565 = 15.081091072   initrd.img                                     2
   2.061828613 = 2.213871616    initrd.img.old                                 2
  13.564765930 = 14.565056512   vmlinuz                                        1
  13.734687805 = 14.747508736   vmlinuz.old                                    2

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ebb92a5-b015-4a90-b55a-48a521237010

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-11-generic
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-11-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-11-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro  single
initrd        /boot/initrd.img-2.6.38-11-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        5ebb92a5-b015-4a90-b55a-48a521237010
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5ebb92a5-b015-4a90-b55a-48a521237010 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 5ebb92a5-b015-4a90-b55a-48a521237010
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8C4B13FC4B100C4
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CEAF910EAF8D774
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cebc1c17-cd2f-4ccb-be81-20f81b659957 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 312.333408356 = 335.365443584  boot/grub/core.img                             1
 312.335144043 = 335.367307264  boot/grub/grub.cfg                             1
 554.339977264 = 595.218018304  boot/grub/menu.lst                             1
 312.331516266 = 335.363411968  boot/grub/stage2                               1
 305.950748444 = 328.512114688  boot/initrd.img-2.6.38-11-generic              2
 305.243164062 = 327.752351744  boot/initrd.img-2.6.38-8-generic               2
 305.579414368 = 328.113397760  boot/vmlinuz-2.6.38-11-generic                 1
 312.329105377 = 335.360823296  boot/vmlinuz-2.6.38-8-generic                  1
 305.950748444 = 328.512114688  initrd.img                                     2
 305.243164062 = 327.752351744  initrd.img.old                                 2
 305.579414368 = 328.113397760  vmlinuz                                        1
 312.329105377 = 335.360823296  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  4c 18 85 ea 79 18 cf a5  11 77 f5 26 4b 42 37 1d  |L...y....w.&KB7.|
00000010  55 5b 90 84 13 eb 54 27  38 5d e4 fd d6 38 c0 f6  |U[....T'8]...8..|
00000020  a1 73 73 5d 99 34 ec 73  b7 52 44 7e 62 1b 76 06  |.ss].4.s.RD~b.v.|
00000030  79 ef 9c d7 9e f8 82 df  7c 6e 43 10 4a 9c fe 5f  |y.......|nC.J.._|
00000040  ca b5 52 d7 52 55 f4 b9  f3 ff 00 88 35 64 2a e8  |..R.RU......5d*.|
00000050  91 e1 c8 60 1b de bc e5  6c 9c 79 93 9d b9 2c 4e  |...`....l.y...,N|
00000060  e0 79 66 e7 fc fe 34 aa  d1 d9 a6 69 28 ab 26 9e  |.yf...4....i(.&.|
00000070  87 86 f8 a4 49 e6 e7 70  00 92 7e 51 d7 93 d6 b9  |....I..p..~Q....|
00000080  45 2c ec 8e 47 4d c0 fe  95 ce ae cd 2e ad 6f 22  |E,..GM........o"|
00000090  47 c0 84 1e 87 9c 7b d5  0d e4 b9 00 67 38 04 fd  |G.....{.....g8..|
000000a0  69 24 ee 63 66 6a db b9  7d c0 0e 84 1c 01 d7 ad  |i$.cfj..}.......|
000000b0  23 da bc 50 90 fb b2 33  8f 63 ff 00 ea a4 d6 ba  |#..P...3.c......|
000000c0  9a d9 f5 2a cc ab f6 84  c3 12 59 72 07 bf 19 ae  |...*......Yr....|
000000d0  8c 69 d2 aa ef 41 9c 2b  01 f8 d6 89 be 80 b5 7a  |.i...A.+.......z|
000000e0  13 a4 72 c6 78 71 92 00  1f 9f 4f f1 a5 5b e9 5a  |..r.xq....O..[.Z|
000000f0  76 60 73 c9 c6 3e b8 35  2e db 32 ad 77 6b 9d 2e  |v`s..>.5..2.wk..|
00000100  8d 3e e9 94 92 ca 43 15  18 ed 9f ff 00 55 7d 1f  |.>....C......U}.|
00000110  f0 f2 4f 31 94 16 39 00  e7 27 dc e2 92 96 9a 77  |..O1..9..'.....w|
00000120  36 4d e9 ae c7 bf 35 ab  a4 44 02 0e 57 a6 7f 5a  |6M....5..D..W..Z|
00000130  93 c1 e4 7d b9 90 af 1b  89 fa fb ff 00 3a ce 54  |...}.........:.T|
00000140  e2 dd fb 1a a8 a9 36 d7  63 d7 55 4e d1 91 c0 19  |......6.c.UN....|
00000150  18 fa d6 84 10 6e 40 0f  7c e0 fa 73 4a 3d 75 37  |.....n@.|..sJ=u7|
00000160  d9 6a 50 58 a5 0e 08 07  e5 62 6b 45 2e a4 5c 7c  |.jPX.....bkE..\||
00000170  a4 9e 3b f6 ac 5c 2d 26  de cc 94 9d d9 61 2f 65  |..;..\-&.....a/e|
00000180  39 50 9f c4 05 58 6d 50  a4 60 94 fb dc 11 9e 9d  |9P...XmP.`......|
00000190  6b 48 c5 de cb 61 a7 25  a0 91 6b 8a 50 fe ed b9  |kH...a.%..k.P...|
000001a0  63 df ad 3b fb 71 a2 40  56 22 d9 07 23 1d 38 c5  |c..;.q.@V"..#.8.|
000001b0  5b 8a 4e c2 77 ea 71 52  0d 4e ee e8 dc 3c 00 fe  |[.N.w.qR.N...<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 03 22 00 fe  |........... ."..|
000001d0  ff ff 05 fe ff ff 02 20  03 22 00 c0 5d 00 00 00  |....... ."..]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 40 20 00  |.X.BSD  4.4..@ .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  71 ea 42 25 05 2a 01 00  00 00 00 00 02 00 00 00  |q.B%.*..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ee 1d f5 7e 42  41 43 4b 55 50 20 20 20  |..)...~BACKUP   |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by coffeecat on 2011-10-14
That "Chainload into grub2" entry in the legacy grub menu is weird. I can't see that it would work. Best ignore the fact that it was there. Your grub2 menu looks to have the entries it needs.

I'm posting from Oneiric at the moment. I'll boot into Natty later on to double-check the packages that you need to uninstall to get rid of the residual legacy grub stuff, and then post back. Not that its presence seems to be doing any harm at the moment.  

I've had a further thought about the ntfs /etc/fstab line that I gave you. It's perfectly safe but sub-optimal. There's a forum member, Morbius1, who posts very clearly and knowledgeably about mounting NTFS partitions. If you search for their posts, you'll find several with better mount options and good explanations for why they are needed. One is "windows_names" which I was not aware of until I read one of Morbius1's posts.

---

### Post by coffeecat on 2011-10-14
Picking up your "earlier version of Ubuntu" in the grub menu, the wubi grub menu is showing you the -11, -10 and -8 kernels, the legacy grub menu for your sda5 installation is showing the -11 and -8 kernels, and your grub2 menu for your sda5 installation is showing only the -8 kernel (apart from Windows and memtest). Whilst you are booted into the sda5 Ubuntu, run:

```
sudo update-grub
```

And the -11 kernel will be added to the grub 2 menu.

I'm in 11.04 at the moment and have checked the grub packages. If you want to purge legacy grub (it's not 100% necessary), open Synaptic and search for the package "grub" and mark it for complete removal. Before you apply that, make sure the version is 0.97-29ubuntu*. Have a look through all the grub* packages, and anything that is version 0.97* can be removed. Make sure you don't remove any grub packages that are version 1.99*. That's grub2.

---

