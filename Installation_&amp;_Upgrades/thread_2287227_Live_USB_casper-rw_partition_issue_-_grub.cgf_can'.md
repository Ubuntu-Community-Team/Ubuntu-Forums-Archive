---
title: "Live USB casper-rw partition issue - grub.cgf can't be edited"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by JTko on 2015-07-17
Hi everyone,

I am having a bit of trouble making a live USB stick persistent. I have a 64gb stick that is partitioned to have one small (<3Gb) boot partition and another casper-rw partition (~58Gb). I read a lot on this and other forums about editing grub.cfg in the /cdrom/boot/grub folder to add the word "persistent" to a couple lines, but when I go to make those changes, I am told it's read only and can't be edited. This occurs even when I open it with "gksudo gedit" or open the containing files as administrator. In fact, the entire casper-rw partition seems to be read-only. Another popular response is that you should NEVER edit grub.cfg, and even if you did, all the changes would be lost. However, editing grub.cfg seems to be successful for a lot of people to add persistence. 

So if anyone had any advice to be able to edit grub.cfg (from what I understand it is generated from script files? might I be able to edit those?), or any other method to make the stick persistent, I would appreciate it. If anyone needs more information I could give that.

Thanks!

---

### Post by Bucky Ball on 2015-07-17
*Thread moved to **Installation & Upgrades**.*

Welcome. And now you will hear it again. You don't edit grub.cfg. You should never edit that. You edit /etc/default/grub and then, when you saved and exited, you:

```
sudo update-grub
```

... and that writes the changes to grub.cfg.

As I said, don't edit grub.cfg directly.

---

### Post by yancek on 2015-07-17
There are several methods which you can use to create a persistent usb such as usb-creator-gtk or unetbootin.  How did you try to create with persistence?  I would not expect simply adding the word 'persistence' to the grub.cfg file is going to do what you want.  If the filesystem is read-only you will not be able to make any changes.  The reason for not editing the grub.cfg file is stated at the top of the file.  Any time you run grub-mkconfig (in the case of Ubuntu the update-grub), any changes you have made to the file will not remain.  If you don't run update-grub, any changes will remain.  I generally install new systems from the iso directly or as an extracted iso and edit grub.cfg each time and do not run update-grub as I expect I will only need the entry once and there would be no point.

---

### Post by sudodus on 2015-07-18
Welcome to the Ubuntu Forums, JTko :-)

I think I understand your problem. When you run a live system, the partition that 'emulates' the CDROM is read-only unless you already run a persistent live session. There are a couple of solutions.

1. Boot from another drive, mount the partition and edit the file.

2. At boot: select the boot option persistent (a one-off operation) before selecting 'Try Ubuntu or Lubuntu or ...'. I think the tips in the following link will help you doing it.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

After booting like this, the partition with grub.cfg is no longer read-only, and you should be able to edit the file.

-o-

You will find more tips in the next links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
[One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by JTko on 2015-07-18
Thanks Bucky Ball (and yancek for similar advice), I think this is where I was getting confused. The /etc/default/grub file looks pretty different from the grub.cfg file, would you or anyone know where I would add "persistent"?

For the record I created the stick with Mac Linux USB Loader, and used that to create a persistent file, which I then deleted and created a casper-rw partition on the stick. The file created by the program could only be 4Gb, due to FAT32 file size requirements. A whole casper-rw partition could take the rest of the space on the stick.

And sudodus, thanks! I actually am using two sticks, one which is only 8Gb which I'm booting, and the 64Gb one that I'm talking about above. The read only problem remains. I'll take a look at those links a bit later.

---

### Post by sudodus on 2015-07-18
Doing what I suggested in post #4 and also editing with superuser privileges should do it (***nano*** is a simple text editor).

```
sudo nano grub.cfg
```

Are you doing this in a Mac computer? Have you got a computer available with linux or Windows?

Maybe it is easier to start from the beginning and make a new system according to one of the links in post #4.

Maybe the following links will help you get it working

[How to install Ubuntu on MacBook using USB flash drive](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) and [this Ubuntu Forum thread by Quackers](http://ubuntuforums.org/showthread.php?t=2174630)

---

### Post by C.S.Cameron on 2015-07-18
Following creates a Persistent USB install of *buntu, usable on both Legacy and UEFI systems:

Boot Live 64 bit CD, (or 64 bit Live USB).
Plug in flash drive.
Start Partition Editor

Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use excess to move files between computers)
Create a 1.5 - 31 GB ext2 partition to the right of this, label it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.

Un-mount and re-mount flash drive.

Start "Startup Disk Creator".
Select "Discard on shutdown".
Press "Make Startup Disk.

When Startup Disk Creator finishes,

Edit Boot/grub.cfg by adding "<space>persistent" as shown below:

```
file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
```

Next

Replace the contents of syslinux.cfg with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD/USB, reboot.

If you wish a separate home partition name it home-rw.

If you are booted from the USB stick you can find the editable grub.cfg at filesystem/cdrom/boot/grub/grub.cfg

I usually edit grub.cfg booted from the Live DVD.

---

### Post by JTko on 2015-07-19
I created the bootable usbs with a Mac, but I boot to one of the Linux sticks and edit the other. I'll give these links a try, thanks.

> **C.S.Cameron said:**
> Following creates a Persistent USB install of *buntu, usable on both Legacy and UEFI systems:

Boot Live 64 bit CD, (or 64 bit Live USB).
Plug in flash drive.
Start Partition Editor

Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use excess to move files between computers)
Create a 1.5 - 31 GB ext2 partition to the right of this, label it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.

Un-mount and re-mount flash drive.

Start "Startup Disk Creator".
Select "Discard on shutdown".
Press "Make Startup Disk.

When Startup Disk Creator finishes,

Edit Boot/grub.cfg by adding "<space>persistent" as shown below:

```
file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
```

Next

Replace the contents of syslinux.cfg with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD/USB, reboot.

If you wish a separate home partition name it home-rw.

If you are booted from the USB stick you can find the editable grub.cfg at filesystem/cdrom/boot/grub/grub.cfg

I usually edit grub.cfg booted from the Live DVD.

Hi CS Cameron. I understand these steps, but the issue is that when I try to edit grub, it's read only and I can't save any changes. According to Bucky Ball (and numerous others in similar posts) I shouldn't even edit grub.cfg at all, so I'm trying to figure out what I should add to /etc/default/grub, in order for my changes to be saved.

---

### Post by sudodus on 2015-07-19
If you 

1. boot from 'the other' USB stick and

2. mount the USB stick (with grub.cfg) with read + write permissions,

it should work to edit the file, at least with elevated (sudo) permissions.

```
sudo nano grub.cfg
```

---

### Post by JTko on 2015-07-19
Ok so some of you are twlling me never to edit grub, and others are telling me here's how you edit grub, which doesn't work, even when I mount the drive as read-write, even when I open as root, etc.

I tried the method of editing /etc/default/grub, which I was able to save, but when do "sudo update-grub", I get "/usr/sbin/grub-probe:error:failed to get canonical path of /cow." I tried the suggestion found here: [http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow) with no success. I think I'm getting closer but there are still a bunch of snags.

---

### Post by ubfan1 on 2015-07-19
You actually have two grub.cfg files.  The one which is used for UEFI  boot is in root filesystem /boot/grub of the ISO, not the booted system.  This is the one to add the word persistent.  After boot, you have different grub.cfg, which would be the one which gets rewritten with update-grub, but since that is not the one used to boot, any changes are ignored.  You do not have a full install with a persistent live media.  Not all updates can be performed, like kernel updates.

---

### Post by C.S.Cameron on 2015-07-19
You can try editing syslinux.cfg:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
or edit text.cfg or txt.cfg in the same way.
In addition to grub.cfg, these have all worked for me to enable persistence.

You can also enable persistence on a boot by boot basis, when booting tap shift then press F6.
after ...quiet splash --, type <space>persistent.

Edit:
I think you edit syslinux.cfg with a UNetbootin build.
For a Startup Disc Creator build edit text.cfg or txt.cfg, depending on which exists.
Grub.cfg is usually edited in grub2 installs like MultiBootUSB.

---

### Post by sudodus on 2015-07-20
We are trying hard to help, but are only guessing about your system, which makes us confused and our advice confusing. Please describe your system with as many details as possible, for example with the output of the following commands:

```
df
```
```
sudo parted -l
```
```
sudo lsblk -fm
```

And tell us how you created the system, which tools you used etc.

Also, please give the ***full path*** to the file that you try to edit without success:

```
/directories.../grub.cfg
```

Then we have a better chance to give good advice :-)

---

### Post by JTko on 2015-07-21
> **sudodus said:**
> We are trying hard to help, but are only guessing about your system, which makes us confused and our advice confusing. Please describe your system with as many details as possible, for example with the output of the following commands:

```
df
```
```
sudo parted -l
```
```
sudo lsblk -fm
```

And tell us how you created the system, which tools you used etc.

Also, please give the ***full path*** to the file that you try to edit without success:

```
/directories.../grub.cfg
```

Then we have a better chance to give good advice :-)

I do appreciate everyone jumping in to help, I didn't mean to come  across as rude, it's just that all my searches have come up with the  same conflicting answers. Here's some output from those commands:

```
mint@mint ~ $ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             4024000  226932   3797068   6% /
udev             4012532      12   4012520   1% /dev
tmpfs             804804    1424    803380   1% /run
/dev/sdb1        2736800 1521296   1215504  56% /isodevice
/dev/loop0       1513296 1513296         0 100% /cdrom
/dev/loop1       1470464 1470464         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            4024000       4   4023996   1% /tmp
none                5120       0      5120   0% /run/lock
none             4024000     688   4023312   1% /run/shm
none              102400      16    102384   1% /run/user
/dev/sdb2       56938788   53068  53970292   1% /media/mint/casper-rw
```

```
mint@mint ~ $ sudo parted -l
Model: ATA APPLE SSD SM128E (scsi)
Disk /dev/sda: 121GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI system partition  boot
 2      210MB   121GB  120GB               Macintosh HD
 3      121GB   121GB  650MB  hfs+         Recovery HD


Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdb: 62.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1024B   2804MB  2804MB  primary  fat32        boot, lba
 2      2804MB  62.2GB  59.4GB  primary  ext4
```

```
mint@mint ~ $ sudo lsblk -fm
NAME   FSTYPE   LABEL            MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                         sda      113G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat     EFI                         &#9500;&#9472;sda1   200M root  disk  brw-rw----
&#9500;&#9472;sda2                                      &#9500;&#9472;sda2 112.2G root  disk  brw-rw----
&#9492;&#9472;sda3 hfsplus  Recovery HD                 &#9492;&#9472;sda3   620M root  disk  brw-rw----
sdb                                         sdb     57.9G root  disk  brw-rw----
&#9500;&#9472;sdb1 vfat     LINUX            /isodevice &#9500;&#9472;sdb1   2.6G root  disk  brw-rw----
&#9492;&#9472;sdb2 ext4     casper-rw        /media/min &#9492;&#9472;sdb2  55.3G root  disk  brw-rw----
loop0  iso9660  Linux Mint 17.1 Cinnamon 64-bit
                                 /cdrom     loop0    1.5G root  disk  brw-rw----
loop1  squashfs                  /rofs      loop1    1.4G root  disk  brw-rw----
```

I created it with Mac Linux USB Loader. I might just redo it all with Unetbootin, that seems to be an installer with a lot more support. 

I'm not sure if this is what you're looking for, but the grub.cfg file I can't edit is /cdrom/boot/grub/grub.cfg. The file I CAN edit is /etc/default/grub, but even when I edit that I can't update grub to save those changes.

Thanks again everyone for your continued help!

---

### Post by sudodus on 2015-07-22
> **JTko said:**
> ...

```
mint@mint ~ $ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             4024000  226932   3797068   6% /
udev             4012532      12   4012520   1% /dev
tmpfs             804804    1424    803380   1% /run
[COLOR="#FF0000"]/dev/sdb1        2736800 1521296   1215504  56% /isodevice
/dev/loop0       1513296 1513296         0 100% /cdrom[/COLOR]
/dev/loop1       1470464 1470464         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            4024000       4   4023996   1% /tmp
none                5120       0      5120   0% /run/lock
none             4024000     688   4023312   1% /run/shm
none              102400      16    102384   1% /run/user
[COLOR="#008000"]/dev/sdb2       56938788   53068  53970292   1% /media/mint/casper-rw[/COLOR]
```

/isodevice and /cdrom make it that it is a 'grub-n-iso' boot system, booting from an iso file via grub.
And there is a big casper-rw partition for persistence, but it is not active (which is your problem).
> 
```
mint@mint ~ $ sudo parted -l
...
Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdb: 62.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1024B   2804MB  2804MB  primary  fat32        boot, lba
 2      2804MB  62.2GB  59.4GB  primary  ext4
```

```
mint@mint ~ $ sudo lsblk -fm
NAME   FSTYPE   LABEL            MOUNTPOINT NAME     SIZE OWNER GROUP MODE
...
sdb                                         sdb     57.9G root  disk  brw-rw----
&#9500;&#9472;sdb1 vfat     LINUX            /isodevice &#9500;&#9472;sdb1   2.6G root  disk  brw-rw----
&#9492;&#9472;sdb2 ext4     casper-rw        /media/min &#9492;&#9472;sdb2  55.3G root  disk  brw-rw----
loop0  iso9660  [COLOR="#FF0000"][COLOR="#008000"]Linux Mint 17.1 Cinnamon 64-bit[/COLOR][/COLOR]
                                 /cdrom     loop0    1.5G root  disk  brw-rw----
loop1  squashfs                  /rofs      loop1    1.4G root  disk  brw-rw----
```

I created it with Mac Linux USB Loader. I might just redo it all with Unetbootin, that seems to be an installer with a lot more support. 

I'm not sure if this is what you're looking for, but the grub.cfg file I can't edit is /cdrom/boot/grub/grub.cfg. The file I CAN edit is /etc/default/grub, but even when I edit that I can't update grub to save those changes.

Thanks again everyone for your continued help!

This makes it much easier to understand - and help :-)

The other outputs confirm the picture, and also states clearly that it is a live [COLOR="#008000"]Linux Mint 17.1 Cinnamon 64-bit[/COLOR] system.

The file you tried to edit, /cdrom/boot/grub/grub.cfg, resides inside the iso file, and its file system is (and must be) mounted read-only. This is not the file where to add persistence. /etc/default/grub is also the wrong file to edit (and it will not be saved, unless you already have persistence).

I have not used the tool ***Mac Linux USB Loader***, so I don't know the details how to use it. (I haven't even got a Mac computer.) But I would guess that there is a configuration file (with the extension .cfg) in the **/dev/sdb1** partition which is mounted at **/isodevice**. You could try to add **persistent** at the end of a line starting with linux in that file, if the system is using grub2.

As you suggest, you can also try to use ***Unetbootin***, or try the 'grub-n-iso' method described in the following link (post #6 and following). That particular method is made for Ubuntu and the 'nearest family flavours' Kubuntu, Lubuntu, Ubuntu Mate, Ubuntu Gnome, Ubuntu Studio, Xubuntu ...),  and after testing I can confirm that it works with your Linux Mint iso file.

[One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682)

See this link for more alternatives

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Maybe the following links will help you get it working with Unetbootin

[How to install Ubuntu on MacBook using USB flash drive](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) and this [Ubuntu Forum thread by Quackers](http://ubuntuforums.org/showthread.php?t=2174630)

---

### Post by ubfan1 on 2015-07-22
Adding detail for the above, edit the file /isolinux/boot/grub/grub.cfg. 
Your machine appears to be a UEFI machine, and there was a bug creating a persistent USB for UEFI with the native startup-disk creator (bug 1159016) which was fixed in release 15.04.  I'd believe other disk creators also had a similar problem -- basically, UEFI boots used grub.cfg instead of the syslinux/txt.cfg file used in legacy booting.  I'm not sure where Mint 17.1 falls in the Ubuntu releases.

---

### Post by sudodus on 2015-07-22
I was curious and had time, so I downloaded linuxmint-17.2-cinnamon-64bit.iso via torrent and copied it to a 'grub-n-iso' pendrive and ran

```
cd /isodevice
sudo -H ./links2check
```

selected 'Link to targets in the current directory'

and rebooted. It worked without tweaks, and now I know that the 'grub-n-iso' system according to

[One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682)

works also with current Linux Mint iso files. At least in PCs made for linux and Windows. It would be interesting to find out, if you can make it work in a Mac computer too.

---

### Post by JTko on 2015-07-22
So I still can't edit any of those files. You were right about there being a configuration file (isolinux.cfg) in that folder, but everything is read-only. Would it make any difference if I actually install to the USB drive, rather than use it as a live system?

Also, I looked into to Unetbootin, and it says it only works to boot to PCs, not Macs. Does this apply even to Intel Macbooks?

---

### Post by sudodus on 2015-07-23
You have several alternatives now:

1. If you boot from another (pen)drive, and mount the partition with isolinux.cfg with read+write permissions, it should be possible to edit the file. You can try again according to posts #4 and #6.

2. Yes, it would make a big difference, if you actually install to the USB drive. It is possible, but I'm not sure that it is easier to make it work that way.

3. The links at the end of post #15 describe how to use Unetbootin to install linux into a pendrive and run it in Mac computers. So at least it worked for the persons who wrote the text in those links.

4. My message in post #17 is that 'my grub-n-iso' method works also with your Linux Mint iso file - that is it works in UEFI mode as well as in BIOS mode in PCs. It is not yet tested in an Intel based Mac, but I think it will work, so it is worth trying. (But it does not work in a Power PC based Mac, those computers have a completely different processor.)

Persistence is there by default from the installation in these 'grub-n-iso' systems.

---

### Post by JTko on 2015-07-23
Well, 1 didn't work, so I just went with 2. The installation seems to have gone well, but now it boots to a black screen with a blinking cursor. But that's for another thread. Thanks everyone for all your help! If anyone in the future is googling around and looks at this thread for advice, I think my takeaway is that if you have a large enough drive (mine's 64Gb), just install to the drive.

Mods, feel free to mark this as solved if you wish, although it's more of a sidestep.

---

### Post by gordintoronto on 2015-07-24
"if you have a large enough drive (mine's 64Gb), just install to the drive."

Bingo! Booting from one USB drive and installing to another takes a bit of care, but it makes for a much simpler solution in the end.

You can mark the thread as solved from "thread tools" near the top-right of the page.

---

