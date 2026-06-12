---
title: "Hard shutdown in Linux Mint LVM installation. Now not starting, need to recover data"
date: 2014-10-22
forum: MINT
---

### Post by Carmen_P on 2014-10-22
I replaced my windows XP (sp3) OS with Linux Mint 17 32-bit (Cinnamon). I didn't knew about file_systems so I chose not to format entire disk as ext4 & let it be NTFS.

Few days back I was unable to eject my flash drive because some *complicated* "exit code 13" issue (see [this]("http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html") & [this]("http://ubuntuforums.org/showthread.php?t=1518031") for more information. And oh, I *didn't* try any one of them - I found these links later).

The issue seemed trivial & so I issued shutdown command **but** _shutdown procedure halted at a certain point... tired, I physically disconnected (pulled out) my flash drive & the system powered off as usual_.

My computer isn't starting normally since then. GRUB screen appears & when I chose to boot normally it gets struck at "Target filesystem doesn't have /sbin/init" error, as in:
```
mount: mounting /dev/mapper/mint--vg--root on **** failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```

I read quite a few articles
 + [http://ubuntuforums.org/showthread.php?t=2220189](http://ubuntuforums.org/showthread.php?t=2220189)
 + [http://ubuntuforums.org/showthread.php?t=1788381](http://ubuntuforums.org/showthread.php?t=1788381)
 + [http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038), etc.
& followed them - no improvements :(. Anyway I collected some useful outputs:

**df -T**
```

Filesystem     Type      1K-blocks   Used Available Use% Mounted on
/cow           overlayfs    997664  67264    930400   7% /
udev           devtmpfs     987848      4    987844   1% /dev
tmpfs          tmpfs        199536    900    198636   1% /run
/dev/sdb1      vfat        3901440 797656   3103784  21% /cdrom
/dev/loop0     squashfs     738944 738944         0 100% /rofs
tmpfs          tmpfs        997664      8    997656   1% /tmp
none           tmpfs          5120      0      5120   0% /run/lock
none           tmpfs        997664     80    997584   1% /run/shm

```

**mount**
```

/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

**sudo fdisk -l**
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc195

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/sdb: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x058ac2ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7821311     3909632    c  W95 FAT32 (LBA)

```

**sudo fdisk -l /dev/sda**
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc195

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

```

**sudo blkid -c /dev/null**
```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4ccfc156-3316-44f2-9bd0-d68baca2692e" TYPE="ext2" 
/dev/sda5: UUID="Vi4FaD-tQ6V-qUzA-1UeP-bXQg-Gzcq-o3RXL7" TYPE="LVM2_member" 
/dev/sdb1: LABEL="UBUNTU 12_0" UUID="4A81-956C" TYPE="vfat" 

```

**sudo fsck -yv /dev/sda1**
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc195

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

```

Typing ```
sudo mount -a
```  after all this gives no output. Please help me to restart the system normally.

---

### Post by Carmen_P on 2014-10-22
**More bad-luck**:
I tried to recover data using ubuntu live CD, I mounted hard drive & found only 3 folders extlinux, grub & lost+found (being the largest, around 255MB). All the usual folders of filesystem like home, opt, etc, etc. are missing & i can not open lost+found folder.

Is my data lost, do I have to using testdisk in this situation?

---

### Post by coffeecat on 2014-10-22
None of the three ubuntuforums threads you link are relevant (as far as I can tell) because you opted for a whole disk LVM system when you installed. I can't tell from the information whether you also opted for an encrypted system but, if you did, that adds another layer of complexity. I'm afraid I can't help you any further because I avoid both LVM and encrypted systems as I'm more interested in preserving both my peace of mind and my sanity, and therefore I have no experience with either to be able to offer any informed advice.

Do you remember whether you opted for encryption? In the meantime and until someone with experience of LVM can help I can only suggest you search for threads on data retrieval from LVM systems.

---

### Post by mips on 2014-10-22
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc195

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended 
/dev/sda5          501760   312580095   156039168   8e  Linux LVM
```[FONT=Verdana]

Did you create a separate /home partition when you installed?

I see sda1 which I'm assuming is / (root) but you also have a extended partition sda2 with a LVM sda5 inside it. Did you by any chance put /home inside the LVM?

If you put /home inside the LVM you won't see it as you will have to mount the LVM first before you can see /home.

Do you remember what you did when you installed?

Anyway here's one guide out of many on how to access LVMs from a livecd [/FONT][FONT=Verdana]http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/

EDIT: As mentioned above did you enable encryption?[/FONT]

---

### Post by mips on 2014-10-22
> **Carmen_P said:**
> 
Is my data lost, do I have to using testdisk in this situation?

Don't do anything before we have assessed the situation, you might just make things worse and then you can potentially kiss your data goodbye!

---

### Post by coffeecat on 2014-10-22
> **mips said:**
> 
I see sda1 which I'm assuming is / (root) but you also have a extended partition sda2 with a LVM sda5 inside it. 

As a point of information, sda1, about 240 MiB in size and formatted ext2 (see the blkid output from the first post), is the boot partition. Everything else will be in the LVM sda5. How do I know this? Unfortunately threads about LVMs are are common as jackdaws on this forum because of the absurdly small size of the boot partition, which get filled up quickly. But that's another matter.

---

### Post by Michael_McKenney on 2014-10-22
The drives don't boot.  Do they show up in the CMOS.  If not in their, they are damaged.  I hope you backup.

---

### Post by mips on 2014-10-22
> **coffeecat said:**
> As a point of information, sda1, about 240 MiB in size and formatted ext2 (see the blkid output from the first post), is the boot partition. Everything else will be in the LVM sda5. How do I know this? Unfortunately threads about LVMs are are common as jackdaws on this forum because of the absurdly small size of the boot partition, which get filled up quickly. But that's another matter.

Ok, missed that thx.

---

### Post by Carmen_P on 2014-10-22
I didn't encrypt anything. And as far as I remember I chose to avoid LVM as I didn't understand what it means.

But yes, I tried to change my password, and strangely
> my login password (and also the password I use for **sudo** authentication) changed to new one
> my **su** (that probably means root?) password didn't change- it remained the same as what I used while installing Linux Mint.

---

### Post by Carmen_P on 2014-10-22
> **mips said:**
> Don't do anything before we have assessed the situation, you might just make things worse and then you can potentially kiss your data goodbye!

Point well taken sir. And I barely understand LVM, so I didn't make /home in LVM or anything like that.

My hard drives are shown correctly in CMOS/BIOS screen, they seem to be working in good state.

---

### Post by coffeecat on 2014-10-22
> **Carmen_P said:**
> I didn't encrypt anything. And as far as I remember I chose to avoid LVM as I didn't understand what it means.

Be that is may, I'm afraid the outputs you provided are unequivocal. You have an LVM system and the only way you can get that from the installer is to choose it. It is not a default.

I think the best thing now would be to retitle your thread to attract those who can help with LVM. I suggest something like this:

*Hard shutdown in Linux Mint LVM installation. Now not starting and need to recover data.*

Let me know if that's OK or post whatever variation you prefer and I'll amend the title for you.

---

### Post by Carmen_P on 2014-10-22
I tried to access LVM from a LiveCD as mentioned on [FONT=Verdana]http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/[/FONT]

I typed in the following commands
```

sudo apt-get install lvm2
sudo pvscan
sudo vgscan
sudo vgdisplay -v
lvgchange -a y mint-vg    #lvgchange was unrecognized command so i just tried vgchange
vgchange -a y mint-vg    #needed sudo
sudo vgchange -a y mint-vg
sudo mount /dev/mint-vg/root /home/Desktop

```

I am getting struck at last mount-ing step, it says
```

mount: you must specify the file system type

```
Any ideas how to over-come this?

---

### Post by Carmen_P on 2014-10-22
> **coffeecat said:**
> Be that is may, I'm afraid the outputs you provided are unequivocal. You have an LVM system and the only way you can get that from the installer is to choose it. It is not a default.

I think the best thing now would be to retitle your thread to attract those who can help with LVM. I suggest something like this:

*Hard shutdown in Linux Mint LVM installation. Now not starting and need to recover data.*

Let me know if that's OK or post whatever variation you prefer and I'll amend the title for you.

Yeah sure, I'd be grateful if you can re-title it with what you said. Thanks for the suggestion.

---

### Post by coffeecat on 2014-10-22
> **Carmen_P said:**
> Yeah sure, I'd be grateful if you can re-title it with what you said. Thanks for the suggestion.

Done.

> **Carmen_P said:**
> ```

sudo mount /dev/mint-vg/root /home/Desktop

```

Ouch! Don't mount anything to your desktop. I'd suggest using a sub-folder of /media. I thought the use of /media/floppy0 in the link a bit eccentric and I'm not even sure you would have a /media/floppy0/ folder as default anyway. You can create a sub-folder for your own purposes with:

```
sudo mkdir /media/*whatever*
```

Actually, /home/Desktop is a non-existent path - it would be /home/*yourusername*/Desktop, so try it with a valid path to a better choice of mountpoint (in /media) and see what happens.

I don't know about the specify filesystem type message - as I said, I haven’t done much with LVM systems. When I get time later I'll do a bit of searching and see if I can find an alternative howto somewhere. I'll only post something if it seems to be usable.

---

### Post by mips on 2014-10-22
> **Carmen_P said:**
> I tried to access LVM from a LiveCD as mentioned on [FONT=Verdana]http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/[/FONT]
I typed in the following commands


Could you please post the output of each step so we can see what your are seeing, would make things easier I think.

---

### Post by Carmen_P on 2014-10-22
**sudo pvscan** gives:
```

  PV /dev/sda5   VG mint-vg   lvm2 [148.81 GiB / 0    free]
  Total: 1 [148.81 GiB] / in use: 1 [148.81 GiB] / in no VG: 0 [0   ]

```

**sudo vgscan** gives:
```

  Reading all physical volumes.  This may take a while...
  Found volume group "mint-vg" using metadata type lvm2

```

**sudo vgdisplay -v** gives:
```

    Finding all volume groups
    Finding volume group "mint-vg"
  --- Volume group ---
  VG Name               mint-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               148.81 GiB
  PE Size               4.00 MiB
  Total PE              38095
  Alloc PE / Size       38095 / 148.81 GiB
  Free  PE / Size       0 / 0   
  VG UUID               V0XC5i-dmAs-97Ye-EUze-xgsc-90S8-FspP3P
   
  --- Logical volume ---
  LV Name                /dev/mint-vg/root
  VG Name                mint-vg
  LV UUID                nQ9tJB-mvMU-B3tk-gGL6-IrRn-vFMC-1ufwo6
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                146.88 GiB
  Current LE             37600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/mint-vg/swap_1
  VG Name                mint-vg
  LV UUID                HgDv7e-8MfH-byNn-Fo0s-468H-UH68-Dhu32a
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                1.93 GiB
  Current LE             495
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Physical volumes ---
  PV Name               /dev/sda5     
  PV UUID               Vi4FaD-tQ6V-qUzA-1UeP-bXQg-Gzcq-o3RXL7
  PV Status             allocatable
  Total PE / Free PE    38095 / 0
   
ubuntu@ubuntu:~$ 

```

**sudo vgchange -a y mint-vg** gives:
```
  2 logical volume(s) in volume group "mint-vg" now active
```

And at last```
sudo mkdir /media/recovery
sudo mount /dev/mint-vg/root /media/recovery
```
gives the **mount: you must specify the filesystem type** error.

---

### Post by Carmen_P on 2014-10-22
Really bad news: I think lvm partition table is corrupted

I google-ed "mount lvm2 ubuntu" & reached [http://ubuntuforums.org/showthread.php?t=1977488](http://ubuntuforums.org/showthread.php?t=1977488)

When I run **fdisk -lu** it gives:```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc195

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/sdb: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x058ac2ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7821311     3909632    c  W95 FAT32 (LBA)

Disk /dev/mapper/mint--vg-root: 157.7 GB, 157705830400 bytes
255 heads, 63 sectors/track, 19173 cylinders, total 308019200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/mint--vg-root doesn't contain a valid partition table

Disk /dev/mapper/mint--vg-swap_1: 2076 MB, 2076180480 bytes
255 heads, 63 sectors/track, 252 cylinders, total 4055040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/mint--vg-swap_1 doesn't contain a valid partition table


```

So what exactly does- "doesn't contain a valid partition table" mean? Physical partition table is courrpted OR LVM's partition table is not understood by fdisk making it look invalid.

Also, I searched for LVM in ubuntu software center & found a graphical utility. Please let me know if that software can let me access my old files
--OR--
googling "testdisk lvm" is the only way left to recover data.

---

### Post by mips on 2014-10-23
**After **you have gone through all those commands could you please post the output of **lvscan**

---

### Post by Carmen_P on 2014-10-23
**sudo lvscan** gives:
```

  ACTIVE            '/dev/mint-vg/root' [146.88 GiB] inherit
  ACTIVE            '/dev/mint-vg/swap_1' [1.93 GiB] inherit


```

---

### Post by mips on 2014-10-23
Ok that's correct. Just wanted to confirm that they are actually active.

If you have a spare hard drive with lots of space I would suggest imaging /dev/mint-vg/root to an *image file* on a spare hdd using dd. Be VERY careful when using dd and make sure you specify the correct source partition and destination file else you could overwrite the wrong thing!

Once you have an image file you could try repairing the file system or use testdisk.

---

### Post by mips on 2014-10-23
You should not have to do this as it should automatically recognise the filesystem but have you tried,

```
sudo mount -t ext4 /dev/mint-vg/root /media/recovery
```

Or ext3 etc depending on what you specified at installation, it uses ext4 by default.

---

### Post by Carmen_P on 2014-10-23
> **mips said:**
> Ok that's correct. Just wanted to confirm that they are actually active.

If you have a spare hard drive with lots of space I would suggest imaging /dev/mint-vg/root to an *image file* on a spare hdd using dd. Be VERY careful when using dd and make sure you specify the correct source partition and destination file else you could overwrite the wrong thing!

Once you have an image file you could try repairing the file system or use testdisk.

Ok, how much space do I need for storing that *image file*, is it
 a. 225MB, which was the total amount of data on my system before failure
 b. 160GB which is the size of my hard disk

---

### Post by Carmen_P on 2014-10-23
Issuing **sudo mount -t ntfs /dev/mint-vg/root /media/recovery** gives:
```

NTFS signature is missing.
Failed to mount '/dev/mapper/mint--vg-root': Invalid argument
The device '/dev/mapper/mint--vg-root' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I tried ext4, ext3 & ext2 but got the same reply, which is:
```

mount: wrong fs type, bad option, bad superblock on /dev/mapper/mint--vg-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```


And all this probably means I will have to resort to testdisk, so can anyone point me to good resources of recovering data from lvm using testdisk.

---

### Post by mips on 2014-10-23
> **Carmen_P said:**
> Ok, how much space do I need for storing that *image file*, is it
 a. 225MB, which was the total amount of data on my system before failure
 b. 160GB which is the size of my hard disk

```
[COLOR=#000000][FONT=Ubuntu Mono]ACTIVE            '/dev/mint-vg/root' [**146.88 GiB**] inherit[/FONT][/COLOR]
```

So you gonna need at least 150GB, a bit more just to be on the safe side.

---

### Post by mips on 2014-10-23
> **Carmen_P said:**
> 
And all this probably means I will have to resort to testdisk, so can anyone point me to good resources of recovering data from lvm using testdisk.

I have never tried recovering from a LVM before (I ran a lvm once before but never again after I had issues with one drive getting bad sectors) but you could have a look at [http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/](http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/)

If you have an image you could also try [FONT=Lucida Grande][COLOR=#333333]fsck but there might be some risk involved here. Testdisk could also potentially recover and repair that root partition.

[/COLOR][/FONT]Here's another resource [http://forum.cgsecurity.org/phpBB3/](http://forum.cgsecurity.org/phpBB3/)

---

### Post by coffeecat on 2014-10-23
I really don't have much more to offer, except that I have found a howto for mounting LVM that differs in a couple of details from the one mips posted earlier. I don't know whether this will make a difference or not, and it's a random blog that came up on a google search (google was actually surprisingly unrewarding for mounting LVM). I wouldn't normally recommend any random blog, but perhaps it's worth considering this one.

mips' link was: [http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/](http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/) which recommended this sequence of commands (after installing lvm2):

```
sudo pvscan
vgscan
sudo vgdisplay -v
lvgchange -a y
sudo mount
```

I've stripped them down for comparison with the next link. As you discovered, and as the next link appears to confirm, "lvgchange" is probably a typo.

The link I came across is: [http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/) which has this sequence after installing lvm2 (again stripped down):

```
pvscan
vgscan
vgchange -a y
lvscan
mount
```

They run lvscan between vgchange and mount. Perhaps that's worth trying.

Another point of information for you:

> **Carmen_P said:**
> Issuing **sudo mount -t ntfs /dev/mint-vg/root /media/recovery** gives:

> **Carmen_P said:**
> I didn't knew about file_systems so I chose not to format entire disk as ext4 & let it be NTFS.

You can't install Linux systems on NTFS which is a Microsoft filesystem, although Ubuntu and Mint can read and write to NTFS, which is another matter. So there's no point in using the -t ntfs option when trying to mount the LVM volume. In fact I suspect that you shouldn't need to use the -t option at all. The two howtos don't.

---

### Post by mips on 2014-10-24
Carmen_p did you come right?

---

### Post by mips on 2014-10-27
Looks like the OP did a multiple hit and run...

---

