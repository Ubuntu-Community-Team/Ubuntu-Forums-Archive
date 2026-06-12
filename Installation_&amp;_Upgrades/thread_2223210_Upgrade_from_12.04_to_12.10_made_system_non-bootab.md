---
title: "Upgrade from 12.04 to 12.10 made system non-bootable"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by GRobLewis on 2014-05-10
When I power on my Dell Dimension 4600i, I hit F12 to get a menu of devices to boot (otherwise it will just boot Windows XP). 
I select the main hard drive, and I get the bootloader menu. The first item on the list is Ubuntu, and this used to work fine. 

Until I upgraded Ubuntu from 12.04 to 12.10. Now it thinks for a few seconds, the screen goes black, and ... nothing. 

I'm a fairly experienced user but I'm clueless when it comes to Linux and dual-boot systems. How can I get my Ubuntu back?

---

### Post by ibjsb4 on 2014-05-10
Sorry for the bad news, but you should not of done this.  If you manage to get this repaired you would then need to upgrade to 13.04 which has already reached EOL.

Instead you should of gone from 12.04 direct to 14.04 and bypass those releases.  All LTS releases can upgrade direct to the next LTS.

---

### Post by mörgæs on 2014-05-10
This hardware will perform better with Lubuntu. A fresh install of 14.04 is worth considering. 
When you have that running you don't have to think of upgrades for three years.

---

### Post by GRobLewis on 2014-05-10
Thanks, sounds good. If only I knew how to do a fresh install on the Linux partition. Is it something I can do from Windows XP, which still works on the system? Do I need to burn an install DVD or something? 

Also, for my purposes I don't really have any complaints about how Ubuntu was performing. I have 1.5GB RAM and have upgraded the on-board graphics with a Radeon 9800 XT card.

---

### Post by oldfred on 2014-05-10
I find on my laptop with only 1.5GB of RAM that I can run full Ubuntu but it is slow. So I install fallback/flashback which is somewhat like the old gnome2 menus with top & bottom panels. But laptop is old and only has Intel internal chip so you video card may help a lot.

You need to download a new Ubuntu 14.04 and create a DVD or flash drive intaller. 
         Also instructions for DVD or USB flash drive
[URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]http://www.ubuntu.com/desktop/get-ubuntu/download

[/URL]
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

Is this a two drive system? If so better to use Something Else or manual install and choose to install grub to MBR of Ubuntu drive and set that as default boot in BIOS.

      
 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    


[URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]
[/URL]

---

### Post by GRobLewis on 2014-05-11
OK, I downloaded 14.04 and made a bootable USB stick from it. Booting that, I chose to install Ubuntu "alongside" my other OSes. It all seems to work, the bootloader lets me boot it, but I can't figure out (a) where it actually got installed (i.e., which partition), and (b) what happened to my existing install of Ubuntu 12.04. 

If it simply overwrote my previous Ubuntu I can live with that, though it seems odd it never asked me for permission to do this. And I was never offered the option of a "dirty" install that would preserve my existing user directory. 

Right now, Unity is showing 3 drives: WinPATA (the original hard drive partition for this machine), WinSATA (a partition on new drive I added and installed Windows on) and "270 GB Volume", which I presume is where Ubuntu lives, but how can I tell?

---

### Post by sudodus on 2014-05-11
I'm not happy with the 'Alongside' install options. Instead I recommend to select the option 'Something else' and have 'full freedom' to create and or select partitions to use, which was also recommended by oldfred.

You can tell from the output of the following terminal windows commands

```
sudo parted -l
```

```
sudo blkid
```

```
df
```

If you want help to interpret the output, cut and paste it into a reply. Select Advanced, mark the text lines and click on the # icon at the top of the editing window to surround the text lines with code tags. In other words, please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by GRobLewis on 2014-05-12
The output from sudo parted -l:
```

Model: ATA ST340014A (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  32.9MB  32.9MB  primary  fat16        diag
 2      32.9MB  35.5GB  35.5GB  primary  ntfs         boot
 3      35.5GB  40.0GB  4458MB  primary  fat32




Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  210GB  210GB   primary   ntfs            boot
 2      210GB   218GB  8000MB  primary   linux-swap(v1)
 3      218GB   488GB  270GB   primary   ext3
 4      488GB   500GB  12.4GB  extended
 5      488GB   500GB  12.4GB  logical   ext4

```

Output from sudo blkid:
```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-071E" TYPE="vfat" 
/dev/sda2: LABEL="WinPATA" UUID="B2FC3901FC38C201" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: LABEL="WinSATA" UUID="B2FC3901FC38C201" TYPE="ntfs" 
/dev/sdb2: UUID="4e78b4d5-a83b-4d44-83d4-754494d4ac92" TYPE="swap" 
/dev/sdb3: UUID="72fb0764-dd96-462e-89c1-f66008befff3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e669334c-d847-41fc-8d62-d9bf15dd7786" TYPE="ext4" 

```

Output from df: 
```

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdb5       11782436 5101516   6059352  46% /
none                   4       0         4   0% /sys/fs/cgroup
udev              762708       8    762700   1% /dev
tmpfs             154448    1072    153376   1% /run
none                5120       0      5120   0% /run/lock
none              772228   19356    752872   3% /run/shm
none              102400      28    102372   1% /run/user

```

Thanks for your help.

---

### Post by GRobLewis on 2014-05-12
Notes on the above: 
1. /dev/sda is the original 40GB Windows XP ATA drive that came with the Dell
2. /dev/sdb is a 500GB SATA drive that I added. It also has Win XP on it, and it had the earlier (12.04) Ubuntu release. Partitions 4 and 5 on it appear to point to the same space, which IIRC I left unallocated when I partitioned the drive. 
3. As you can see, I also defined an 8GB Linux swap partition but have never attempted to use it. Is this a worthwhile thing to do? Where can I find out how? 
4. Where is my new 14.04 Ubuntu? And do I still have 12.04?

---

### Post by GRobLewis on 2014-05-12
Examining the above, I'm starting to think that installing 14.04 took over the unallocated 12.4GB at the end of the SATA drive, formatted it ext4, and installed Ubuntu there. Assuming I'm right, that's certainly not what I wanted. How can I move the install back to overwrite 12.10 on /dev/sdb3?

---

### Post by oldfred on 2014-05-12
Use Something Else and choose partition. Also choose to install grub2 boot loader to sdb and set BIOS to boot sdb.

My second install screen is to my SSD which using gpt partitioning. First install is to a partition on sdc that had an old install so it shows the old install that I am overwriting. It also shows at bottom a combo box with drive sda. You want to change that to drive that is sdb.

---

### Post by GRobLewis on 2014-05-15
@sudodus Haven't heard anything for several days. Have I been abandoned?

---

### Post by sudodus on 2014-05-15
*Oldfred* is our best expert on installing and booting at the Ubuntu Forums, so when he is helping you, so you are not abandoned.

Follow the instructions in post #11. Do you want help which partition to use?

```
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  210GB  210GB   primary   ntfs            boot
 2      210GB   218GB  8000MB  primary   linux-swap(v1)
 [COLOR=#ff0000]3      218GB   488GB  270GB   primary   ext3[/COLOR]
 4      488GB   500GB  12.4GB  extended
 [COLOR=#ff0000]5      488GB   500GB  12.4GB  logical   ext4[/COLOR]
```

I assume you want to install into partition 3, /dev/sdb3, because partition 5 is rather small (more suitable for a test installation).

---

### Post by GRobLewis on 2014-05-26
Yes, exactly, thank you. If I could simply copy the 14.04 install from partition 5 to partition 3 and make Grub work with it, I'd be good to go. Though shouldn't I upgrade the partition's file system from ext3 to ext4 first? (I'm still puzzled how the 14.04 installer simply chose to use partition 5, without any direction from me that I can recall.) 

I still have the 14.04 installer on a USB stick, if that's of any use. 

Preserving the work in my user directory in the 12.11 install on partition 3 would be a bonus, though not essential. 

A big fear is that I'll accidentally do something to kill the Windows XP install in partition 1. 

Final question: when I partitioned the drive I created the 8GB partition 2, thinking I'd use it for swap space. Is there any advantage to this? How do I enable it? (This machine is basically a learning tool for ubuntu, and not a day-to-day workstation or server.)

---

### Post by oldfred on 2014-05-26
If you use auto install it finds unallocated space and installs to that. It also tried not to use all 4 primary partitions without creating the 4th or often swap in the extended as a logical partition.

You can just reinstall using something else to sda3, if you change format from ext3 to ext4 it will erase all your data. You should back up all of /home no matter what you do. If you can boot the old install, export a list of installed apps, so it is easy to reinstall all the one's you may have added.

Screen shots in post #11 show the important settings, and the combo box at the bottom to change to install grub2 boot loader to sdb, not default of sda.

More examples. Even if older versions, install process is still the same, screens have not changed much over the years.
       Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by sudodus on 2014-05-26
***Warning 0: Read the whole post including the warnings near the end before you start doing anything!***

> **GRobLewis said:**
> Yes, exactly, thank you. If I could simply copy the 14.04 install from partition 5 to partition 3 and make Grub work with it, I'd be good to go. Though shouldn't I upgrade the partition's file system from ext3 to ext4 first? (I'm still puzzled how the 14.04 installer simply chose to use partition 5, without any direction from me that I can recall.) 

I still have the 14.04 installer on a USB stick, if that's of any use. 

1. Boot from the 14.04 installer on a USB stick

2. Start ***gparted*** and format partition 3 to ext4.

3. Mount the two drives, assuming it it still device b, /dev/sdb. Check this !!!

```
sudo mkdir -p /mnt/sdb3
sudo mkdir -p /mnt/sdb5
sudo mount /dev/sdb3 /mnt/sdb3
sudo mount /dev/sdb5 /mnt/sdb5

```
4. Copy the content of partition 5 to partition 3 with ***rsync***

First a DRY RUN (with the option n to see that it works correcly)

```
sudo rsync -Havn  /mnt/sdb5/ /mnt/sdb3  # the trailing slash '/' in /dev/sdb5/ is important

```
Then run the real thing

```
sudo rsync -Hav  /mnt/sdb5/ /mnt/sdb3  # the trailing slash '/' in /dev/sdb5/ is important

```
5. Fix the bootloader, so that it points to sdb3 according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

> 

Preserving the work in my user directory in the 12.11 install on partition 3 would be a bonus, though not essential. 

A big fear is that I'll accidentally do something to kill the Windows XP install in partition 1. 

Final question: when I partitioned the drive I created the 8GB partition 2, thinking I'd use it for swap space. Is there any advantage to this? How do I enable it? (This machine is basically a learning tool for ubuntu, and not a day-to-day workstation or server.)

***Warning 1:***

If you want to preserve your work in the home directory, you should *not* work along the previous tips, but keep the home directory in sdb3 and let it become a separate home partition. Shrink the partition and use the other part as the root partition. This is more complicated but certainly possible. I am not sure which method would be the best. Maybe a fresh installation onto a system including a blank root partition and your home partition.

***Warning 2:***

In all cases, there are many risky moments both for mistakes and power failure, so ***be sure to have a good backup before you star***t.

-o-

It is good to have swap. If you intend to hibernate, you need at least the same amount in gibibytes as the RAM. Otherwise it is probably enough with one or two GB swap.

---

