---
title: "ALERT! /dev/sik/by-uuid/... does not exist. Dropping to shell!"
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by chad27 on 2016-06-15
Something has become corrupted on my system and now it won't boot.  Here's what I'm getting:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/efe24220-9569-4e7b-8fof does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)

---

### Post by Bashing-om on 2016-06-15
chad27; Hello. Welcome to the forum.

Grub sure is not happy !

Let's see what we can do to find out the cause.

Boot up the live medium in "try ubuntu" mode that you used to install the system; Activate a terminal ( ctl+alt+t ) :

Post back - between code tags - the outputs of terminal commands :
```

sudo blkid -c /dev/null -o list
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

as a place to start to see why grub is complaining.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Booting in using LiveCD here are the results of 

```
sudo fdisk -lu
sudo parted -l 
sudo blkid
```

```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1231fddf
```

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *       4196352 1911820287 1907623936 909.6G 83 Linux
/dev/sda2       1911822334 1953523711   41701378  19.9G  5 Extended
/dev/sda3             2048    4196351    4194304     2G 83 Linux
/dev/sda5       1911822336 1953523711   41701376  19.9G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.


Disk /dev/sdb: 14.5 GiB, 15522070528 bytes, 30316544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000
```

```
Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 3      1049kB  2149MB  2147MB  primary   ext4
 1      2149MB  979GB   977GB   primary   ext4            boot
 2      979GB   1000GB  21.4GB  extended
 5      979GB   1000GB  21.4GB  logical   linux-swap(v1)


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  15.5GB  15.5GB  primary  fat32        boot, lba
```
```

/dev/sda1: UUID="81503651-baa2-4a4c-a0f7-ee359432968e" TYPE="ext4" PARTUUID="1231fddf-01"
/dev/sda3: UUID="56cbc6a5-21ea-4745-b1ee-0fa89dff447e" TYPE="ext4" PARTUUID="1231fddf-03"
/dev/sdb1: LABEL="UBUNTU" UUID="5089-2A3A" TYPE="vfat"
/dev/sda5: UUID="86e36571-bcbb-4f88-b2a5-0086551655b4" TYPE="swap" PARTUUID="1231fddf-05"
/dev/loop0: UUID="5ce92d58-8dd9-5141-9b6b-4c867c345ead" TYPE="ext2"
/dev/loop1: TYPE="squashfs"
```

---

### Post by chad27 on 2016-06-15
```
sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 ext2             (in use)       5ce92d58-8dd9-5141-9b6b-4c867c345ead
/dev/loop1 squashfs         /rofs          
/dev/sda1  ext4             (not mounted)  81503651-baa2-4a4c-a0f7-ee359432968e
/dev/sda3  ext4             (not mounted)  56cbc6a5-21ea-4745-b1ee-0fa89dff447e
/dev/sda5  swap             [SWAP]         86e36571-bcbb-4f88-b2a5-0086551655b4
/dev/sdb1  vfat    UBUNTU   /cdrom         5089-2A3A
```

---

### Post by deadflowr on 2016-06-15
i fixed you odd code tag output.
( the fdisk and parted outputs where mixed-up and confusing)

The error in post #1 seems to be correct, there is no uuid listed for that partition in the blkid output.
Was there another disk attached at some point?

---

### Post by chad27 on 2016-06-15
I have attached one at one point, but that was quite a while ago.  Just an external drive.

---

### Post by Bashing-om on 2016-06-15
chad27; Well ..

Seems grub is telling the truth that UUID " efe24220-9569-4e7b-8fof " does not exist.

Let's see if we can find where the UUID originated from.
In this live medium we want to mount the partition that you want to boot. As you have several installs on the system .. you will have to tell us which one where.  And we will read the fstab file that directs what is to be mounted at boot .

By the way .. as linux is installed on both hard drives .. can you boot up the alternate install by changing the boot order in bios ?

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
I'm not sure what is going on.  I only have the one internal hard drive and the usb that I'm booting up with.  I'm a noob, so thanks for the patience and help!

---

### Post by chad27 on 2016-06-15
Here's what I did:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 ext2             (in use)       5ce92d58-8dd9-5141-9b6b-4c867c345ead
/dev/loop1 squashfs         /rofs          
/dev/sda1  ext4             /mnt           81503651-baa2-4a4c-a0f7-ee359432968e
/dev/sda3  ext4             (not mounted)  56cbc6a5-21ea-4745-b1ee-0fa89dff447e
/dev/sda5  swap             [SWAP]         86e36571-bcbb-4f88-b2a5-0086551655b4
/dev/sdb1  vfat    UBUNTU   /cdrom         5089-2A3A 
```

Here's the /etc/fstab file:

```

overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

---

### Post by Bashing-om on 2016-06-15
chad27; Hey !
Not a problem:
> 
 I'm a noob, so thanks for the patience and help!

We were all new at one time .. and in the same shoes you are wearing . None of us were born knowing what we know.

I was a bit confused by the outputs you gave.
so we are looking at a single internal drive and we are booting the 1st partiton (sda1)
sda is the 1st hard drive the system recognizes .. and the 1 is the 1st partition on this drive,
We know it contains the /root file system by the star denoting "boot" on sda1 .. so next is to see what is set to be mounted on boot:
We do that by examining the contents of the file /etc/fstab.
So we mount it from the liveUSB and have a look:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda1 /mnt/looksee
cat /mnt/looksee/etc/fstab

```
With the expectation of seeing that invalid UUID being invoked in this file. In that case we edit it with the correct UUID .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-06-15
chad27; Hey ! Again !

It slipped my mind .. that we have to UN-Mount what we mounted, once we have what we want.
```

sudo umount /mnt/looksee

```

Would not want something unforeseen happening IF the partition remains in a mounted condition .

[INDENT][INDENT]bad things can happen
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Here you go:

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/looksee
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/looksee
ubuntu@ubuntu:~$ cat /mnt/looksee/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=81503651-baa2-4a4c-a0f7-ee359432968e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=86e36571-bcbb-4f88-b2a5-0086551655b4 none            swap    sw              0       0
/dev/disk/by-id/usb-Generic_Flash_Disk_869BF50B-0:0 /mnt/usb auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
#UUID=56cbc6a5-21ea-4745-b1ee-0fa89dff447e    /boot    ext4    defaults    02


```

---

### Post by Bashing-om on 2016-06-15
chad27; Uh Huh ..

I bet:
> 
/dev/disk/by-id/usb-Generic_Flash_Disk_869BF50B-0:0 /mnt/usb auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
#UUID=56cbc6a5-21ea-4745-b1ee-0fa89dff447e    /boot    ext4    defaults    02

this flash disk is not available when booting up .

So, the obvious question is what is your intent here in mounting the device ? This could get tricky if the device is not always present when booting .

Pending what we know
[INDENT][INDENT]is what we do next .
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
The flash drive is how I booted into Linux (the Linux Disk Image).  Should I eject it?

---

### Post by Bashing-om on 2016-06-15
chad27;

NO on ejecting the booting flash drive,
the one here in question is " /dev/disk/by-id/usb-Generic_Flash_Disk_869BF50B-0:0"
Where is this device and do you have a real need to have it recognized when booting up the system ?
I can not imagine a need to do so as the gvfs system will mount that device automagically when inserted .

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT][INDENT]but leads to a non booting system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Okay.  I think I've figured out what is going on with that drive.  I built the disk image on the USB using Linux Live on Windows.  It asked if I wanted Persistent memory I said yes and allocated just under 2 GB for that.  I can rebuild it without the persistent memory.

---

### Post by Bashing-om on 2016-06-15
chad27; K ..

But perhaps the better thing is to remove this mount from the fstab ( File SystemTABle ) file .

Then I bet the system will boot up .

[INDENT][INDENT]I thought I was wrong, once
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Can you explain how to do that?  

I now remember that at some point there was an issue with originally copying my old machine over onto this new hard drive.  Someone told me to create empty space at the beginning of the drive, so it would work (which it did until this morning).

I deleted this part of the fstab file.  Is that correct?

```

# swap was on /dev/sda5 during installation
UUID=86e36571-bcbb-4f88-b2a5-0086551655b4 none            swap    sw              0       0
/dev/disk/by-id/usb-Generic_Flash_Disk_869BF50B-0:0 /mnt/usb auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
#UUID=56cbc6a5-21ea-4745-b1ee-0fa89dff447e    /boot    ext4    defaults    02

```

---

### Post by chad27 on 2016-06-15
Didn't work.

---

### Post by Bashing-om on 2016-06-15
chad27; Sure ..

For the naunce;
while having the sda1 partition mounted in the liveUSB;
Run:
```

sudo -H gedit /mnt/looksee/etc/fstab

```
Assuming that the text editor 'gedit'  is available in the liveUSB installer ( ubuntu ? it is ) .
Place a # character at the start of the line " /dev/disk/by-id/usb-Generic_Flash_Disk_869BF50B-0:0 /mnt/usb auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0 " such that it becomes a "comment" .
Save the file, and exit the editor.

Back out of what we manually mounted:
```

sudo umount /mnt/backup

```
Reboot;
reset in bios to boot the hard drive ;

Do you now boot up as expected ?

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Progress:

I can now on booting up get a screen that has *Ubuntu and then Ubuntu Advanced Options.  If I go to options I see 6 options 

Ubuntu, with Linux 4.2.0-35-generic
Ubuntu, with Linux 4.2.0-35-generic (upstart)
Ubuntu, with Linux 4.2.0-35-generic (recovery mode)
Ubuntu, with Linux 4.2.0-16-generic
Ubuntu, with Linux 4.2.0-16-generic (upstart)
Ubuntu, with Linux 4.2.0-16-generic (recovery mode)

If I select the first three lines I get the same error, but the system allows me to boot into the 4.2.0-16-generic

---

### Post by Bashing-om on 2016-06-15
chad27; Yuk .

Now that is odd to have such a large disparity in versions between 4.2.0-16- and 4.2.0-35-.

In the kernel that does boot .. let's see if we can get a clue :
post back:
```

ls -al /vmlinuz*
ls -al /initrd*
dpkg -l | grep linux
ls -al /usr/src/
ls -al /lib/modules/

```

Make sure all the pieces are there .

It's 'buntu
[INDENT][INDENT]break it, and we get to keep the pieces;
[INDENT][INDENT][INDENT]put her back together again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
```

ls -al /vmlinuz*
ls: cannot access /vmlinuz*: No such file or directory

ls -al /initrd*
ls: cannot access /initrd*: No such file or directory

dpkg -l | grep linux
ii  console-setup-linux                           1.108ubuntu9                               all          Linux specific part of console-setup
ii  libselinux1:amd64                             2.3-2build1                                amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                1.6.3-1                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                          1.6.3-1                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-libc-dev:amd64                          4.2.0-35.40                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                    1.8.0-1                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                      3:6.03+dfsg-8ubuntu2                       amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                               3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                    2.26.2-6ubuntu3                            amd64        Miscellaneous system utilities

ls -al /usr/src/
total 8
drwxr-xr-x  2 root root 4096 Apr 18 18:39 .
drwxr-xr-x 12 root root 4096 Apr  6 22:36 ..

ls -al /lib/modules/
ls: cannot access /lib/modules/: No such file or directory

```

---

### Post by Bashing-om on 2016-06-15
chad27; Ouch !!

Now this just blows me away .. You have NO kernels installed ! 
That even Begs the question of how you can boot up at all .. 

How much time and effort are you willing to expend ?
Is this a fresh install ?

If so, you might consider a RE-install and try again.

But upfront .. I prefer to try and fix . Maybe a learning situation for the both of us .

Whoahhh ...

[INDENT][INDENT]there is a 1st time for everything
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
Sounds fine to me.  Let's see if we can fix it.

---

### Post by Bashing-om on 2016-06-15
chad27; Ho Kay !

Here goes .. NOT nuthin .
In the install - booted to that 4.2.0-16-generic selection - which I have no idea how/why it is/can boot :
run:
```

sudo apt install linux-generic linux-headers-generic linux-image-generic

```

Now show me:
```

sudo update-grub
ls -al /boot

```

depending on what is
[INDENT][INDENT]is what we do next
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
```

ls -al /boot
total 109488
drwxr-xr-x  3 root root     4096 Jun 15 15:05 .
drwxr-xr-x 26 root root     4096 Jun 15 15:05 ..
-rw-r--r--  1 root root  1311978 Oct  8  2015 abi-4.2.0-16-generic
-rw-r--r--  1 root root  1313029 Mar 15 19:45 abi-4.2.0-35-generic
-rw-r--r--  1 root root  1313411 Jun  8 18:40 abi-4.2.0-38-generic
-rw-r--r--  1 root root   184809 Oct  8  2015 config-4.2.0-16-generic
-rw-r--r--  1 root root   184888 Mar 15 19:45 config-4.2.0-35-generic
-rw-r--r--  1 root root   184889 Jun  8 18:40 config-4.2.0-38-generic
drwxr-xr-x  5 root root     4096 Jun 15 15:05 grub
-rw-r--r--  1 root root 33671781 Apr  6 11:50 initrd.img-4.2.0-16-generic
-rw-r--r--  1 root root  8018660 Jun 15 09:37 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root 33629473 Jun 15 15:05 initrd.img-4.2.0-38-generic
-rw-r--r--  1 root root   182704 Aug 27  2015 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 27  2015 memtest86+.elf
-rw-r--r--  1 root root   184840 Aug 27  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3740437 Oct  8  2015 System.map-4.2.0-16-generic
-rw-------  1 root root  3745312 Mar 15 19:45 System.map-4.2.0-35-generic
-rw-------  1 root root  3746271 Jun  8 18:40 System.map-4.2.0-38-generic
-rw-r--r--  1 root root  6797696 Apr  5 19:59 vmlinuz-4.2.0-16-generic
-rw-------  1 root root  6829104 Mar 15 19:45 vmlinuz-4.2.0-35-generic
-rw-------  1 root root  6832624 Jun  8 18:40 vmlinuz-4.2.0-38-generic

```

---

### Post by Bashing-om on 2016-06-15
chad27; Uh Huh ....

Looks promising . Typo correct " sudo update grub " to :
```

sudo update-grub

```
that silly little hyphen .
What is the output from update-grub ?

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
```
sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done



```

---

### Post by Bashing-om on 2016-06-15
chad27; Hey hey ...

Look'n good .. there is promise there >

so let us see what we have now to boot from:
```

ls -al /vmlinuz*
ls -al /initrd*
ls -al /boot
dpkg -l | grep linux
ls -al /usr/src/
ls -al /lib/modules/

```

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
```

$ ls -al /vmlinuz*

lrwxrwxrwx 1 root root 29 Jun 15 15:05 /vmlinuz -> boot/vmlinuz-4.2.0-38-generic

$ ls -al /initrd*

lrwxrwxrwx 1 root root 32 Jun 15 15:05 /initrd.img -> boot/initrd.img-4.2.0-38-generic

$ ls -al /boot

total 109488
drwxr-xr-x  3 root root     4096 Jun 15 15:05 .
drwxr-xr-x 26 root root     4096 Jun 15 15:05 ..
-rw-r--r--  1 root root  1311978 Oct  8  2015 abi-4.2.0-16-generic
-rw-r--r--  1 root root  1313029 Mar 15 19:45 abi-4.2.0-35-generic
-rw-r--r--  1 root root  1313411 Jun  8 18:40 abi-4.2.0-38-generic
-rw-r--r--  1 root root   184809 Oct  8  2015 config-4.2.0-16-generic
-rw-r--r--  1 root root   184888 Mar 15 19:45 config-4.2.0-35-generic
-rw-r--r--  1 root root   184889 Jun  8 18:40 config-4.2.0-38-generic
drwxr-xr-x  5 root root     4096 Jun 15 15:15 grub
-rw-r--r--  1 root root 33671781 Apr  6 11:50 initrd.img-4.2.0-16-generic
-rw-r--r--  1 root root  8018660 Jun 15 09:37 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root 33629473 Jun 15 15:05 initrd.img-4.2.0-38-generic
-rw-r--r--  1 root root   182704 Aug 27  2015 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 27  2015 memtest86+.elf
-rw-r--r--  1 root root   184840 Aug 27  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3740437 Oct  8  2015 System.map-4.2.0-16-generic
-rw-------  1 root root  3745312 Mar 15 19:45 System.map-4.2.0-35-generic
-rw-------  1 root root  3746271 Jun  8 18:40 System.map-4.2.0-38-generic
-rw-r--r--  1 root root  6797696 Apr  5 19:59 vmlinuz-4.2.0-16-generic
-rw-------  1 root root  6829104 Mar 15 19:45 vmlinuz-4.2.0-35-generic
-rw-------  1 root root  6832624 Jun  8 18:40 vmlinuz-4.2.0-38-generic

$ dpkg -l | grep linux

ii  console-setup-linux                           1.108ubuntu9                               all          Linux specific part of console-setup
ii  libselinux1:amd64                             2.3-2build1                                amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                1.6.3-1                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                          1.6.3-1                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                1.149.3                                    all          Firmware for Linux kernel drivers
ii  linux-generic                                 4.2.0.38.41                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-38                        4.2.0-38.45                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-38-generic                4.2.0-38.45                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.2.0.38.41                                amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-38-generic                  4.2.0-38.45                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-38-generic            4.2.0-38.45                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.2.0.38.41                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.2.0-35.40                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                    1.8.0-1                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                      3:6.03+dfsg-8ubuntu2                       amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                               3:6.03+dfsg-8ubuntu2                       all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                    2.26.2-6ubuntu3                            amd64        Miscellaneous system utilities

$ ls -al /usr/src/

total 16
drwxr-xr-x  4 root root 4096 Jun 15 15:05 .
drwxr-xr-x 12 root root 4096 Apr  6 22:36 ..
drwxr-xr-x 24 root root 4096 Jun 15 15:05 linux-headers-4.2.0-38
drwxr-xr-x  7 root root 4096 Jun 15 15:05 linux-headers-4.2.0-38-generic


```

---

### Post by Bashing-om on 2016-06-15
chad27; Yeah !

Looks good 'nuf to give it a try .

Reboot .. the only kernel that is fully installed is the 4.2.0-38, which is the latest and greatest . And ... should boot by default.

Let's see what happens.

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-15
It works!  Thank you so much for your help.  The other kernels appear to still be there when I go to the advanced login options.  Is that expected?

---

### Post by Bashing-om on 2016-06-15
chad27; Well, well !

If this system is functional as is .... we still have a lot of work to do.

IF you check around and all is good booting the 4.2.0-38-, such that it is worthwhile to continue ..

Then we need to install a backup kernel, update the system .. and clean up the debris .

[INDENT][INDENT]but
[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-16
Oh wow!  I thought we were done.  It looks like everything is working, so let's keep going. What's next?

---

### Post by Bashing-om on 2016-06-16
chad27; Morning.

Next up is to get the backup kernel fully installed and functional:
```

sudo apt update 
sudo apt install --reinstall linux-image-extra-4.2.0-35-generic linux-image-4.2.0-35-generic linux-headers-4.2.0-35-generic linux-headers-4.2.0-35
sudo apt upgrade

```

And once more, let us see what grub thinks:
```

sudo update-grub

```
and have a look and "see" if the symlink has been established for this backup kernel -35 :
```

ls -al /vmlinuz*
ls -al /initrd*

``` We can hope the system does it for us .. I will not be surprised at all if we have to make it up ourselves .

Once we have the backup kernel fully installed, then we upgrade this system and check for missing/broken packages;
And when all looks good we finally clean up the debris .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-16
```

ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Jun 16 12:24 /vmlinuz -> boot/vmlinuz-4.2.0-35-generic
lrwxrwxrwx 1 root root 29 Jun 15 15:05 /vmlinuz.old -> boot/vmlinuz-4.2.0-38-generic

ls -al /initrd*
lrwxrwxrwx 1 root root 32 Jun 16 12:24 /initrd.img -> boot/initrd.img-4.2.0-35-generic
lrwxrwxrwx 1 root root 32 Jun 15 15:05 /initrd.img.old -> boot/initrd.img-4.2.0-38-generic



```

---

### Post by Bashing-om on 2016-06-16
chad27l Well ...... Well !

The kernel did install .. and  the system did make up the symbolic link .. However .. I did not expect or anticipate that the -35 kernel would now be the default boot.
I would prefer that the -38 kernel were the default booting kernel.

let's try this:
Boot the -38 kernel from grub's boot menu .
now again run:
```

sudo update-grub

```

Does the boot arrangement change as desired ?
```

ls -al /vmlinuz*
ls -al /initrd*

```
Get the booting arrangement squared away and we can move onto cleaning up the system.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]but getting there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-16
No luck.

```

:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-38-generic
Found initrd image: /boot/initrd.img-4.2.0-38-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done


~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Jun 16 12:24 /vmlinuz -> boot/vmlinuz-4.2.0-35-generic
lrwxrwxrwx 1 root root 29 Jun 15 15:05 /vmlinuz.old -> boot/vmlinuz-4.2.0-38-generic

~$ ls -al /initrd*
lrwxrwxrwx 1 root root 32 Jun 16 12:24 /initrd.img -> boot/initrd.img-4.2.0-35-generic
lrwxrwxrwx 1 root root 32 Jun 15 15:05 /initrd.img.old -> boot/initrd.img-4.2.0-38-generic

```

---

### Post by Bashing-om on 2016-06-16
chad27; Umph !

Not real sure what to do about the situation ? Leave well enough alone and see if the next kernel upgrade fixes it for us ?
Any problem booting as present ?

For now, let us move on and clean things up:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```
I do not anticipate ( famous last words) any problems . IF however the system reports errors , post the command and it's complete output.
If 'dpkg' is happy .. there will only be a return to prompt when the 'dpkg' command is executed.

[INDENT]not done
[INDENT][INDENT]'til the package manager says we are
[/INDENT][/INDENT][/INDENT]

---

### Post by chad27 on 2016-06-16
Everything went smoothly.  Thanks again.  I'm not having any trouble booting, so like you said let's leave well enough alone and hopefully it fixes it at the next kernel upgrade.

---

### Post by Bashing-om on 2016-06-16
chad27; Great ..

Let's call this good then .. and close this thread.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Any problems encountered, open a new thread and we deal with it there .
It has been my pleasure to work with you.

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

