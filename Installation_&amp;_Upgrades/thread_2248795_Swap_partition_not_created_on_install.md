---
title: "Swap partition not created on install"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2014-10-17
Fresh install of 14.04 on a Eee PC1001P.
I used the automatic install and chose to use LVM and encrypt the whole of the drive.
I've just noticed that the automatic install did NOT create a Swap partition.
I can't re-size the existing partition in GParted.
The specs of the machine are:
Processor 
 CPU    Intel Atom N450 / 1.66 GHz dual core 
Memory    RAM    1 GB ( 1 x 1 GB )
160 GB HDD.
I shall be upgrading the RAM shortly to 2GB.
Here's what Disks shows:
[https://drive.google.com/file/d/0B7c0iOOzxM3LUTNZWl9JZkliOGc/view?usp=sharing](https://drive.google.com/file/d/0B7c0iOOzxM3LUTNZWl9JZkliOGc/view?usp=sharing)

[IMG]https://drive.google.com/file/d/0B7c0iOOzxM3LUTNZWl9JZkliOGc/view?usp=sharing[/IMG]

Can anyone tell me what the 1.1 GB partition is, and do I need a Swap area?

---

### Post by Bucky Ball on 2014-10-17
Boot from an install USB/DVD, 'Try Ubuntu', get to a desktop, launch Gparted and try there. I know nothing about LVM so don't know if that's preventing it, but you may be trying to resize the partition Ubuntu is running from and that's not possible unless you're running a Live boot. ;)

The 1.1Gb looks like the /swap. Open Gparted and look.

---

### Post by Gordonbp531 on 2014-10-17
Hi Bucky,
I should have mentioned I had alreadt tried that.
Booting from live USB, GParted won't allow me to re-size the partition, and doesn't even see the 1GB partition....

---

### Post by fantab on 2014-10-17
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Gordonbp531 on 2014-10-17
> **fantab said:**
> Post the output of:
```
sudo parted -l
sudo fdisk -l
```

Sudo parted -l:

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label             

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 159GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  159GB  159GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label 

sudo fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064ffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   83  Linux

Disk /dev/mapper/sda5_crypt: 159.8 GB, 159782010880 bytes
255 heads, 63 sectors/track, 19425 cylinders, total 312074240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 158.7 GB, 158712463360 bytes
255 heads, 63 sectors/track, 19295 cylinders, total 309985280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 1065 MB, 1065353216 bytes
255 heads, 63 sectors/track, 129 cylinders, total 2080768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by oldfred on 2014-10-17
LVM is an advanced partitioning that overlays the physical partitions with logical partitions. You an even span multiple drives. But it is more advanced, requires different tools to edit and if one partition fails you lose the entire thing.
Gparted does not work on LVM and will only see the underlying physical partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by Bucky Ball on 2014-10-17
> **oldfred said:**
> 
Gparted does not work on LVM and will only see the underlying physical partitions.

 

Now I know something about LVM. Thanks oldfred, I learn something everyday round here. ;)

---

### Post by Gordonbp531 on 2014-10-18
Thanks for all that info - I think I'm going to do a re-install without LVM!

---

### Post by Bucky Ball on 2014-10-18
Might be a good idea. Unless you have a specific reason, unsure why LVM would come into the equation. But as I say, uneducated on that front ... ;)

Good luck and post a new thread with a descriptive title if you have any further issues with the re-install rather than tacking them on to this one. Will improve your chances of support.

PS: oldfred is a font of wisdom when it comes to this stuff, as can be plainly seen. ;)

---

### Post by Gordonbp531 on 2014-10-18
> **Bucky Ball said:**
> Might be a good idea. Unless you have a specific reason, unsure why LVM would come into the equation. 

This being a Netbook, which I take out and about,  I need to encrypt the whole drive.
In the Install dialog, if you click on the option to encrypt the whole drive, LVM is automatically selected. You apparently cannot choose whole disk encryption without using LVM...

---

### Post by Gordonbp531 on 2014-10-18
Using the LVM GUI tool to reduce the space in Root to give more space to the Swap area, I get the following error:

Logical volume is not mounted but is in use. Please close all applications using this device (eg iscsi)

The only application in use is LVM, and there's no process (AFAICS) named iscsi.....

---

### Post by Bucky Ball on 2014-10-18
You have marked this thread as solved. How did you fix the problem? Please share with the community. Thanks. ;)

---

### Post by Gordonbp531 on 2014-10-19
> **Bucky Ball said:**
> You have marked this thread as solved. 

Sorry, I'd forgotten I'd done that when I had decided to re-install. I've now decided NOT to re-install for the reason above re encryption.
So now I have a problem with the LVM tool...

---

### Post by oldfred on 2014-10-19
You should then start a new thread with LVM in title. 
Then those who know about LVM may offer to help. It may be better to be in server sub-forum  as LVM is more often used with servers. 

I do not use encryption, but believe full drive with LVM does offer some advantages. 
But you can do encryption of just /home or just encrypt the files or one partition with files that you are concerned about. 

But any encryption adds complexity and requirements for better backup procedures as recovery from errors is not possible.

---

