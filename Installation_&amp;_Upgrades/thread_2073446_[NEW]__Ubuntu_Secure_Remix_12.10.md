---
title: "[NEW]  Ubuntu Secure Remix 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2012-10-19
**Ubuntu Secure Remix** is a slightly improved Ubuntu Live-CD designed especially to install Ubuntu in dual-boot with Windows (or MacOS).

[IMG]http://doc.ubuntu-fr.org/lib/exe/fetch.php?hash=1504c6&media=http%3A%2F%2Fpix.toile-libre.org%2Fupload%2Fimg%2F1312537751.png[/IMG]

**_[Downloads]("https://help.ubuntu.com/community/UbuntuSecureRemix")_:** 
Ubuntu Secure can be downloaded here : [https://sourceforge.net/p/ubuntu-secured/](https://sourceforge.net/p/ubuntu-secured/)

**_Functionalities:_**
- same functionalities as the normal Ubuntu CD, but also :
- automatically backup of the MBRs when installing Ubuntu (CleanUbiquity), which is highly recommended for dual-boot Ubuntu-Windows (or MacOS)
- integrates [OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller") (tool to uninstall any Operating System from your PC)
- integrates [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"): tool to repair the PC boot (GRUB/MBR)

Enjoy :)

Ubuntu Secure does not aim at becoming a new distribution, but just to let people install Ubuntu without losing their MBR, until this functionality is [included officially in next releases of Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279")

**You can contribute by** :
- voting on Launchpad for these bugs: [1st]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291"), [2nd]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279"), [3rd]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/653474")
- [translating]("https://translations.launchpad.net/boot-repair/trunk") (now >70 languages)
- suggesting improvements
[URL="https://sourceforge.net/p/ubuntu-secured/home/Home/"]
Official website of Ubuntu-Secure-Remix[/URL]

---

### Post by desesperado on 2013-01-24
Hi, I'm a noob at Linux so please bare with me.

I have a dualboot instalation of Windows XP Professional and Xubuntu 12.10.

My Xubuntu instalation consists on three partitions **/**, **/home** and **swap**.

I've installed Xubuntu after Windows and now I'm planning on removing windows from my computer using OS-Uninstaller option of Ubuntu Secure Remix 12.10 leaving just Ubuntu in it.

My question is does your software automatically resizes the Ubuntu partition to use the space of unallocated space left after the windows deletion operation, or do I have to use GParted afterwards to expand my **/** partition or even **/home**, also?

One last question regards what is the most advisable way to do it, i.e should I do it with a CD including OS-Uninstaller or install OS-Uninstaller in Ubuntu and boot my computer on a Ubuntu live-CD?

Thanks in advance.

---

### Post by YannBuntu on 2013-01-24
hello
> **desesperado said:**
> does your software automatically resizes

No. OS-Uninstaller does not resize any partition.

> **desesperado said:**
> should I do it with a CD including OS-Uninstaller or install OS-Uninstaller in Ubuntu

As you don't remove Ubuntu, you can use OS-Uninstaller from any session (CD or installed).

---

### Post by desesperado on 2013-01-24
Thank you for your prompt answers, YannBuntu.

So, I'll have to resize the partitions after deleting Windows. So, now, allow me to ask you just one last question, do I have to reboot after running OS-Uninstaller and just after it I should resize the partition with GParted or can I do it on-the-fly, i.e after running OS-Uninstaller resize the partiotions right away, without rebboting?

Again, I thank you and excuse myself for my noob questions?

---

### Post by YannBuntu on 2013-01-24
I recommend you reboot in order to check that Ubuntu still boots normally after using OS-Uninstaller.

---

### Post by desesperado on 2013-01-24
Thanks a lot YannBuntu, your advices and courtesy are really appreciated.

I'll do as you suggested and afterwards I'll return to post if I've accomplished it with success.

---

### Post by oldfred on 2013-01-24
You will have to resize partitions from a liveCD and click on swap right click swap off as you cannot work with mounted partitions.

I am not a fan of resizing left or moving partitions unless you have to. You can consider just another data partition where you just reformat the NTFS to ext4. That you probably can do from inside your Ubuntu install with gparted, but you will have to download gparted.

If you decide to move partition left and expand right, I would be sure to do a full backup before hand of all important data. Moving partitions can take a while depending on how full they are and any power failure or interruption will cause corruption.

---

### Post by desesperado on 2013-01-24
> **oldfred said:**
> You will have to resize partitions from a liveCD and click on swap right click swap off as you cannot work with mounted partitions.

I am not a fan of resizing left or moving partitions unless you have to. You can consider just another data partition where you just reformat the NTFS to ext4. That you probably can do from inside your Ubuntu install with gparted, but you will have to download gparted. 

If you decide to move partition left and expand right, I would be sure to do a full backup before hand of all important data. Moving partitions can take a while depending on how full they are and any power failure or interruption will cause corruption. 

Unfortunately I did not saw your post before doing the stupidity  I've done., I'm a real idiot.

First stupid mistake I've made was not to click on swap right click swap off so I wouldn't with mounted partitions.

Second, and even worst stupid mistake I've made was not to do a full backup before hand of all important data. 

So now I'm stuck at a black screen with** error: unknown file system grub rescue**

After some googling I've tried YannBuntu Boot-Repair, with no success, but I manage to get this information out of it:
```
 Boot Info Script 5a35e00 + Boot-Repair extra info      [Boot-Info 22Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for (,msdos2)/boot/grub.

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2               2,048   181,475,797   181,473,750  83 Linux
/dev/sda3    *    181,477,376   230,219,775    48,742,400  83 Linux
/dev/sda4         230,219,776   234,440,703     4,220,928  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda3        0060b00f-e13f-41c0-8058-00c6eff68771   ext4       
/dev/sda4        2cbcbc03-b2c8-429b-9179-673ee534ca89   swap       
/dev/sr0                                                iso9660    Xubuntu 12.10 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/xubuntu/0060b00f-e13f-41c0-8058-00c6eff68771 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 8 (/proc/7921/mounts) leaked on lvscan invocation. Parent PID 12839: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-01-25__00h06 ===================
boot-repair version : 3.197~ppa27~quantal
boot-sav version : 3.197~ppa27~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.197~ppa27~quantal
boot-repair is executed in live-session (Ubuntu 12.10, quantal, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda3: UUID="0060b00f-e13f-41c0-8058-00c6eff68771" TYPE="ext4"
/dev/sda4: UUID="2cbcbc03-b2c8-429b-9179-673ee534ca89" TYPE="swap"
/dev/sr0: LABEL="Xubuntu 12.10 i386" TYPE="iso9660"

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda3    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/xubuntu/0060b00f-e13f-41c0-8058-00c6eff68771.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
2      1049kB  92.9GB  92.9GB  primary
3      92.9GB  118GB   25.0GB  primary  ext4
4      118GB   120GB   2161MB  primary  linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA Hitachi HTS54161;
2:1049kB:92.9GB:92.9GB:::;
3:92.9GB:118GB:25.0GB:ext4::;
4:118GB:120GB:2161MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/xubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xubuntu)
/dev/sda3 on /media/xubuntu/0060b00f-e13f-41c0-8058-00c6eff68771 type ext4 (rw,nosuid,nodev,uhelper=udisks2)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hpet input kmsg kvm log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda2 sda3 sda4 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  189M  1.3G  13% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      606M  800K  606M   1% /run
/dev/sr0       iso9660    694M  694M     0 100% /cdrom
/dev/loop0     squashfs   665M  665M     0 100% /rofs
tmpfs          tmpfs      1.5G   20K  1.5G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      1.5G   88K  1.5G   1% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda3      ext4        23G  694M   22G   4% /media/xubuntu/0060b00f-e13f-41c0-8058-00c6eff68771

=================== fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5d0f855

Device Boot      Start         End      Blocks   Id  System
/dev/sda2            2048   181475797    90736875   83  Linux
/dev/sda3       181477376   230219775    24371200   83  Linux
/dev/sda4       230219776   234440703     2110464   82  Linux swap / Solaris


No OS has been found on this computer.

=================== Recommended repair
Recommended-Repair
This setting will not act on the MBR.
The boot flag will be placed on sda3.


parted /dev/sda set 3 boot on

                                                                          
Information: You may need to update /etc/fstab.


Boot successfully repaired.

You can now reboot your computer.

  
```Also, I've run Boot Info Script, and I'm attaching the results file obtained.

Do you think there's a solution  to recover my system? That would be like hitting the jackpot.

---

### Post by oldfred on 2013-01-24
Not sure about resize and what has occurred.

But I would try fsck first from liveCD so everything is unmounted. Example is sdb1 change to your partition sda2.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by desesperado on 2013-01-24
Thanks for the help you're offering oldfred, but I'm not sure I grasp completely what you are suggesting.

Do you mean to use fsck at a terminal window? How can I make swapp off not using GParted?

---

### Post by desesperado on 2013-01-24
Here's what I've done:

```
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
e2fsck: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by desesperado on 2013-01-24
So, I used the -y option, but no success, apparently:

```
xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda2
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Sorry to be annoying, but is there any other possibilities?

---

### Post by desesperado on 2013-01-24
I tried the following:
```
sudo mke2fs -n /dev/sda2
```

And the output is:
```
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
5677056 inodes, 22684218 blocks
1134210 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
693 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000
```

So I tried to restore the superblock from the backups, and use:
```
sudo e2fsck -b backup_number /dev/sda2
```

But nothing, using all the backup numbers, I always get:
```
e2fsck 1.42.5 (29-Jul-2012)
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I'm starting to despair. Can anyone help me, please?

---

### Post by desesperado on 2013-01-25
I've spent hours trying to fix but I've been not successful. Can't any of the experienced Ubuntu users help me somehow?

Another thing that might cast a light on the issue, the output of ```
cat /etc/fstab
``` is the following:
```
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0
```And the output of ```
df -h

``` is:
```
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.5G   87M  1.4G   6% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           606M  800K  606M   1% /run
/dev/sr0        694M  694M     0 100% /cdrom
/dev/loop0      665M  665M     0 100% /rofs
tmpfs           1.5G   16K  1.5G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.5G   88K  1.5G   1% /run/shm
none            100M   12K  100M   1% /run/user

```And the output of ```
ls -l /dev/ | grep sd
``` is:
```
brw-rw----  1 root    disk      8,   0 Jan 25 08:45 sda
brw-rw----  1 root    disk      8,   2 Jan 25 09:21 sda2
brw-rw----  1 root    disk      8,   3 Jan 25 08:45 sda3
brw-rw----  1 root    disk      8,   4 Jan 25 08:45 sda4
```

And of ```
sudo mount -t ext4 /dev/sda2 /mnt
``` is
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So I tried ```
dmesg | tail
``` and get this:
```
[   99.193167] iwl3945 0000:05:00.0: >loaded firmware version 15.32.2.9
[   99.262755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   99.263044] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  102.005042] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  102.005304] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  698.685105] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[ 2469.909127] CE: hpet increased min_delta_ns to 20113 nsec
[ 2469.909743] CE: hpet increased min_delta_ns to 30169 nsec
[ 2469.910446] CE: hpet increased min_delta_ns to 45253 nsec
[ 2659.480451] EXT4-fs (sda2): VFS: Can't find ext4 filesystem
```

And finally ```
sudo parted -l
``` and get:
```
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 2      1049kB  92.9GB  92.9GB  primary
 3      92.9GB  118GB   25.0GB  primary  ext4            boot
 4      118GB   120GB   2161MB  primary  linux-swap(v1)

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 

```

---

### Post by desesperado on 2013-01-25
I've found this tutorial [Recovering an unmountable partition from Linux]("http://sanjayak71.blogspot.pt/2010/10/recovering-unmountable-partition-from.html") but I'm not sure if it applies to my situation.

Basically the workaround is to run the Unix command 'dd' to do a low level (byte level) read from a device or file and write to a device or file.
In my case it woul be
```
dd if=/dev/sda2 of=/media/disk/sda2.img
```This  command would create an image of the partition sda2 as a file named  'sda2.img' and the 'e2fsck' can be run on this image and correct errors, running:
```
e2fsck -f /media/disk/sda2.img
```I would have to mount the image as a loop device:
```
mount -o loop /media/disk/sda2.img /media/sda2-img
```Afterwards I would have to I wrote the image back in to sda2 using 'dd':
```
dd if=/media/disk/sda2.img of=/dev/sda2 
```Is it advisable to try this workaround in my case?

---

### Post by desesperado on 2013-01-25
Anyone, please::-? ](*,)

---

### Post by oldfred on 2013-01-25
It said to try the backup superblock, did you try that?

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by desesperado on 2013-01-25
First let me thank you oldfred for your patience and willingness to help me. I'm really thankful.

 Answering your question, yes I tried to backup superblock, like I posted in my previous # 13 post. But no matter which number I've used, and I did it with all, I always get the same output:

> **desesperado said:**
> I tried the following:
```
sudo mke2fs -n /dev/sda2
```And the output is:
```
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
5677056 inodes, 22684218 blocks
1134210 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
693 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000
```So I tried to restore the superblock from the backups, and use:
```
sudo e2fsck -b backup_number /dev/sda2
```But nothing, using all the backup numbers, I always get:
```
e2fsck 1.42.5 (29-Jul-2012)
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```I'm starting to despair. Can anyone help me, please?

I will now try to remove first inode and use alternative superblock, as you suggest.

Let me ask you one other thing, do you think that the workaround I mentioned on my post #15 could be a solution to my situation case everything else fails?

Once again, thanks and I do apologize for all the trouble.

---

### Post by desesperado on 2013-01-25
Unfortunately that solution also lead me to no success:

```
 xubuntu@xubuntu:~$ sudo debugfs -w /dev/sda2
debugfs 1.42.5 (29-Jul-2012)
/dev/sda2: Bad magic number in super-block while opening filesystem
debugfs:  clri <8>
clri: Filesystem not open
```

Do you think that there's no hope and just a clean reinstall will end my misery?
[-o<

---

### Post by oldfred on 2013-01-25
The reason for the dd backup is so you do not damage the original and if you run some command that destroys backup then you can create another.  At this point I am not sure it adds much. 

Sometimes dd will not work with damaged drives. I am not sure but gddrescue may work better than just dd.

       gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by desesperado on 2013-01-25
No luck. Nothing seems to solve it. The only choice, since I've been dealing with this for about 18 hours, and I'm starting to feel very tired, is to get some sleep and by the time I'll awake I'll just wipe off everything and start from scratch with a new install.

Anyway, it's not all losses. I learned, the hard way, a few very important lessons and in the process I got to broaden my knowledge of Linux. From that point of view it was a very rewarding adventure.

Finally I just want pay my tribute and  leave a huge thanks to oldfred for all the support he offered. You were truly patience and educational.

---

### Post by oldfred on 2013-01-25
Sometimes re-install is the only option. 

I might also check in Disk Utility, click on drive and see if what Smart Status is. All I really know is green is good or not many errors on drive. But it can run tests.

---

### Post by TerryTAIUx on 2013-02-09
Hello,

As a potential new user of Ubuntu - but not of the Unix/Linux environment -, I plan to install Ubuntu 12.04.1 LTS 32bit on a laptop in dual-boot with Windows. Windows XP Professional SP2 is pre-installed, and the official Ubuntu LiveCD just downloaded. The partition scheme has already been prepared on the single hard disk with GParted LiveCD.

In fact, my preference from far would be to install Ubuntu 12.04.1 LTS directly from the Ubuntu Secure Remix 12.04.1 LTS CD if it exists. So I tried to search for it in the 3 links below but could not find it. As far as I can see, the only versions available are 12.10 32bit and 12.10 64bit:

[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
[http://sourceforge.net/p/ubuntu-secured/home/Home/](http://sourceforge.net/p/ubuntu-secured/home/Home/)
[http://sourceforge.net/projects/ubuntu-secured/files/](http://sourceforge.net/projects/ubuntu-secured/files/)

Did I miss anything? The only thing I observed is that the same Desktop screenshot displayed in the first two links makes appear the icon for installing Ubuntu 12.04.1 LTS, while the current (last) version of Ubuntu Secure Remix is 12.10.

Is that screenshot out of date? Is the icon just an online installation of 12.04.1 LTS or an installation from Ubuntu Secure Remix's previous release?

May be for technical reasons, the 3 features usefully added by YannBuntu would be no more compliant or no more relevant with Ubuntu 12.04.1 LTS? Actually I don't know of it.

I'd be glad if anyone could give a check. Thank you for help.

Regards,

TerryTAIUx

---

### Post by YannBuntu on 2013-02-09
Hello Terry
yes, the screenshots are outdated, I will update them.

Indeed, Boot-Repair (and OS-Uninstaller) still works on 12.04 and previous versions, so you can install it on any supported Ubuntu disk.

But creating/updating the ISO of Ubuntu-Secure takes time, so I prefer to maintain only one (indeed two: 32 and 64bit) Ubuntu-Secure ISO, based on the newest Ubuntu version (12.10 today). That is why you won't find Ubuntu-Secure-12.04 any more.

---

### Post by TerryTAIUx on 2013-02-09
Hello Yann,

Nice to meet you and thank you for the precise info. I quite understand that maintaining the double version of Ubuntu-Secure 12.10 is an effort in itself, for the benefit of whoever wants to use it. That's a very nice contribution indeed.

On my side, as I plan to install and use 12.04 LTS as long as possible, there are quite good alternatives as you said. I already have the Boot-Repair ISO. I also know the option of installing OS-Uninstaller, as well as the possibility of manual backup of MBRs. I'll take my time so I won't get lost anyway, and I guess I could rely on the Ubuntu community if needed.

My current task is now to get more familiar with the forums and their related threads. I will certainly meet useful information there and share the experience to come as well. Hope to see you later!

Best regards,
TerryTAUIx
(bien le bonjour d'un vieux briscard Unix qui a peut-être un peu perdu la main sur les dernières évolutions de Linux ;)

---

### Post by YannBuntu on 2013-02-09
Bonjour Terry,

As you speak French, I recommend you use (also) the French-speaking forum of Ubuntu ( [forum.ubuntu-fr.org]("http://forum.ubuntu-fr.org") ), which is very active/helpful too.

Pour info, il y a une discussion en Français à propos de Boot-Repair : [http://forum.ubuntu-fr.org/viewtopic.php?id=509791](http://forum.ubuntu-fr.org/viewtopic.php?id=509791)

In my opinion, LTS versions are ok if you don't mind using old software and you want minimum maintenance (eg for servers/companies).
For personal use, and as you have experience with computers, I recommend you use the last Ubuntu version (12.10 now).

---

### Post by wildmanne39 on 2013-02-09
Hi, I saw 12.10 remix that it is for dual boot but I suppose it can be used even if you are not planning to install it on a dual boot system correct?
Thanks

---

### Post by TerryTAIUx on 2013-02-09
Bonjour Yann,

Yes, your point of view about the choice between 12.04 LTS or 12.10 is interesting and relevant, I have to think it over a bit more. I initially opted for a minimum maintenance AND personal use, in other words a more cosy environment due to my laziness, but that kind of choice is still to be discussed - with myself...

By choosing the latest version, I had in mind I would take the risk of getting involved in more and more complexity in an endless process - in fact, when I look backwards over my shoulder, I am still amazed by the outstanding stability of some former Unix versions. But I may be wrong in that old-fashioned perspective, and I would lack the constant brainstorming implied by new features and new projects.

All this deserves to be re-considered from scratch.

> **YannBuntu said:**
> 
As you speak French, I recommend you use (also) the French-speaking forum of Ubuntu ( [forum.ubuntu-fr.org]("http://forum.ubuntu-fr.org") ), which is very active/helpful too.

Pour info, il y a une discussion en Français à propos de Boot-Repair : [http://forum.ubuntu-fr.org/viewtopic.php?id=509791](http://forum.ubuntu-fr.org/viewtopic.php?id=509791)


Vraiment intéressant, ce long fil ! Merci pour l'info, Yann, je vais bientôt m'inscrire et regarder ces discussions de plus près.

Best regards,
TerryTAIUx
(TAIUx stands for: "Ask Your Question, The Answer Is Unix" :)

---

### Post by TerryTAIUx on 2013-02-09
Hello Wild Man,

The group of additional features integrated by YannBuntu in the Ubuntu Secure Remix 12.10 CD is meant to help the user manage a dual-boot system more easily, but the CD can be used also for full installation non dual-boot systems.

Regards,
TerryTAIUx

---

### Post by YannBuntu on 2013-02-10
**@Wild Man:** Terry answered correctly. Ubuntu-Secure is just Ubuntu + 3 small tools, so it can also be installed in mono-boot just like Ubuntu. Among the 3 tools, 2 (OS-Uninstaller and Clean-Ubiquity) are useful only for multi-boot. The 3rd one (Boot-Repair) can be useful for mono-boot and multi-boot.

---

### Post by wildmanne39 on 2013-02-10
I thought as much just wanted it clarified in this thread for everyones benefit.
Thanks

---

### Post by YannBuntu on 2013-02-25
**@all:** New version is now available and discussed here: [http://ubuntuforums.org/showthread.php?t=2120127](http://ubuntuforums.org/showthread.php?t=2120127)

**@moderators:** please close this thread.

---

### Post by coffeecat on 2013-02-25
Closed at request of OP.

---

