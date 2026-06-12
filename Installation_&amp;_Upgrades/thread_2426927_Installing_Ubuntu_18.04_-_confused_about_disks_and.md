---
title: "Installing Ubuntu 18.04 - confused about disks and directory structure"
date: 2019-09-15
forum: Installation &amp; Upgrades
---

### Post by ptolemytoo on 2019-09-15
I am utterly confused regarding the disk and partition setup of Ubuntu 18.04 on my recently acquired refurbished Dell Latitude E7440. The good news, such as it is, is that I bought this computer in order to experiment and see if I can use Linux as my full time platform before I spend serious money on a new machine. This is an endeavour to free myself from the unilateral actions and control, not to mention unwelcome surveillance of both Apple and Microsoft.

So here's what happened and what led to my current confusion:

System information:

[INDENT]i7-4600U - 2.10GHz x 4
16GB RAM[/INDENT]

Apart from processor and RAM specifications shown above, this computer has a 1TB HDD and a 256GB SSD. The latter having been installed as a special incentive by the company from whom I had purchased it. It came with Windows 10 Pro loaded.

When it came to loading Ubuntu, (installed from a bootable flash/thumb drive) I chose to go with the minimal install and to encrypt the entire system. I then let the installation program do it's thing with whatever defaults were set.

I should mention that when installing the OS, the drive it defaulted to for the installation was the 1TB drive. For obvious reasons, I prefer to have it install to the 256GB SSD. That is all I changed in the partition/drive setup. I saw both drives listed there and assumed Linux would install itself in the best way possible, creating all the traditional UNIX/Linux directories and that it would also include the 1TB drive; all formatted to ext4. Apparently not.

On the bright side, I was delighted to see that everything worked right away; WiFi, Bluetooth and trackpad and even the little IBM/Lenovo like Trackpoint.

While playing around and installing some of my favourite apps, editors etc. I came across the Disks program. (I have set up a Linux server or two in the distant past but this is my first foray into the Linux GUI world.) I noticed that the "secondary" drive, the 1TB HDD, was listed as /dev/sda and the boot drive was /dev/sdb/. I'm not sure if that is significant or not.

But my main problem -- I thought -- was that the 1TB drive was still formatted as NTFS and appeared to be "outside" the Linux file system. I was perturbed, but no problem, I used Gparted (or was it Disks) to kill that partition and create a new partition which I formatted as ext4. Big. Mistake. I effectively locked myself out of my computer. On rebooting, the system encryption password was no longer accepted and I was essentially dead in the water.

At this point, due to increasing irritation and frustration, I have sort of lost the plot. I don't remember exactly what I did next. Generally speaking, I reinstalled a few times, with and without encryption. The last installation was without encryption, allowing the install program to just do whatever it wanted to do. But, when I inspected, the disks' setup and the file and directory structure, I was surprised to see that I did not recognise anything. It seems that both drives have been created with a single partition and that there were things I had never heard of happening.

Where is */boot?* Where is */home?* Where is */?* Where is */var?* And there appears to be no */swap.*

Instead of the familiar directory structure, I see Loops and snaps.

The terminal command *lsblk -f* produces the following:

```

NAME   FSTYPE   LABEL UUID                                 MOUNTPOINT
loop0  squashfs                                            /snap/gnome-logs/61
loop1  squashfs                                            /snap/gtk-common-themes/1313
loop2  squashfs                                            /snap/core18/1066
loop3  squashfs                                            /snap/gnome-calculator/406
loop4  squashfs                                            /snap/gnome-characters/296
loop5  squashfs                                            /snap/gnome-system-monitor/100
loop6  squashfs                                            /snap/core/7270
loop7  squashfs                                            /snap/gnome-3-28-1804/67
loop8  squashfs                                            /snap/core18/1144
loop9  squashfs                                            /snap/core/7713
loop10 squashfs                                            /snap/gnome-characters/317
loop11 squashfs                                            /snap/gnome-logs/73
loop12 squashfs                                            /snap/gnome-calculator/501
loop13 squashfs                                            /snap/gnome-3-28-1804/71
sda                                                        
&#9492;&#9472;sda1 ext4           41094aa3-b4f0-460a-8d9d-46779c0f1a5f /media/ptolemy/41094aa3-b4f0-460a-8d9d-46779c0f1a5f
sdb                                                        
&#9492;&#9472;sdb1 ext4           43790a07-577c-406a-bb12-a7de65f3ee00 /


```
And the command *fdisk -l* produced the following.

```

Disk /dev/loop0: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x78e8ef54

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1  *     2048 1953523532 1953521485 931.5G 83 Linux


Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2bb57bf7

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 500117503 500115456 238.5G 83 Linux


Disk /dev/loop8: 54.4 MiB, 57065472 bytes, 111456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 89 MiB, 93327360 bytes, 182280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 149.9 MiB, 157192192 bytes, 307016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


```
So that rather long winded preface sets the scene and I hope provides enough information.

My question is: How can I (*provided it is still possible to do so)* reinstall Ubuntu, preferably with system encryption turned on (but that can be a subject for another post) with the following conditions:

1. It boots off the 256GB ssd.
2. Incorporates the 1TB drive as part of the overall directory structure, perhaps as */home*
3. Creates the traditional \*NIX directory structure, as mentioned above.
4. Leaves out the *loops* and *snaps* ... and is it desirable to do so?

Thanks in advance

---

### Post by CatKiller on 2019-09-15
> **ptolemytoo said:**
> 
My question is: How can I (*provided it is still possible to do so)* reinstall Ubuntu, preferably with system encryption turned on (but that can be a subject for another post) with the following conditions:

1. It boots off the 256GB ssd.
2. Incorporates the 1TB drive as part of the overall directory structure, perhaps as */home*
3. Creates the traditional \*NIX directory structure, as mentioned above.
4. Leaves out the *loops* and *snaps* ... and is it desirable to do so?

The first three are straightforward by choosing the **something else** option in the installer. Set your SSD to be your / and your HDD to be /home. The installer will make an ESP on the first drive - probably your HDD from the names you've described - and use a swap file rather than a swap partition. You don't need to muck about with partitions for other parts of the filesystem. 

I've not played with encryption, but the people who have don't suggest that it adds any real problems to the installation.

You can't technically do number 4. [Snaps](https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0) are containerised applications with their own sandbox filesystems so that they don't interfere with anything else. Canonical have pushed them into the install so that everyone gets some real-world usage experience with them. What you *can* do, however, is get rid of them after you've installed Ubuntu. You can either just remove the ones that you don't want with snap commands or get rid of snapd, which will take out all of them.

---

### Post by TheFu on 2019-09-15
I don't have 18.04 (too new for me), but with a 16.04 install, using encryption, to a UEFI booting system, this is what can be achieved.  I don't recall the original installation, but I did have to shrink / to be a reasonable size and create a new LV for /home and for my "/stuff" LV to hold other things.  To my knowledge, anytime encryption is used, so is LVM.
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9500;&#9472;ubuntu--vg-swap_1   253:2    0   4.5G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home 
&#9492;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi
```

Snaps can be ignored.  They aren't really mounts.
By default, /home and /stuff are not created during the installation, but thanks to LVM, reducing / and adding  new LVs is pretty easy.  They are all encrypted - anything contained by sda3_crypt is encrypted using LUKS.  It is the entire sda3 partition.

Notice that I haven't allocated most of the storage. It is kept in reserve to be added where needs - which takes about 20 seconds.  LVM makes this sort of stuff really easy.

And the storage, minus any unimportant stuff like loop devices (I don't have any)
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
/dev/sda2                       ext2  721M  252M  433M  37% /boot 
/dev/mapper/ubuntu--vg-root     ext4   25G   14G  9.6G  59% /
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff
lxd/containers/devoted-sunbird  zfs    15G  421M   14G   3% /var/lib/lxd/containers/devoted-sunbird.zfs




```

---

### Post by oldfred on 2019-09-15
New installs are just / (root). If UEFI install then it also adds an ESP - efi system partition.
It now creates a swap file, so swap partition is not required. But with LVM installs it will still create a swap partition inside the LVM.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
> For new installs, a **swap file** will be used by default instead of a swap partition. 

---

