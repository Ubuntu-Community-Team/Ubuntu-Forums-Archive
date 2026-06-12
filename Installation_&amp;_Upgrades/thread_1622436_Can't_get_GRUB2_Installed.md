---
title: "Can't get GRUB2 Installed"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by shadowofblood on 2010-11-15
EDIT:  After discovering that the "/boot" partition did not end on a cylinder boundary, I booted back up into the alternate cd, re-partitioned everything and re-installed.  It worked fine after that :)

I can't seem to get Grub2 Installed.
After many attempts, my computer boots into a black screen with white text stating:
>  [Minimal BASH-like line editing is supported.  For the first word, TAB  lists possible command completions.  Anywhere else TAB lists the  possible completions of a device/filename.  ]                      I used the Ubuntu 10.10 Alternate CD to set up an unencrypted "/boot" partition (dev/sdb1) and an encrypted volume (dev/sdb2).  I used the Logical Volume Manager to create several partitions on the encrypted volume for "/", "tmp", "var", "usr", "usr local", "home", and "swap".

/dev/Ubuntu/Root is the encrypted root partition on /dev/sdb2.

So far I've tried:

Mount /dev/Ubuntu/Root to /mnt.  Mount /dev/sdb1 to /mnt/boot.  grub-install --root-directory=/mnt /dev/sdb.
Installation was successfull.  But I still boot into the screen described above.

I have also attempted the above, but instead of running grub-install, I ran "mount --bind /dev /mnt/dev" and then attempted to chroot into /mnt, but got an error saying "bash: groups: command not found".  I then tried dpkg-reconfigure grub-pc, but it failed to install grub to /dev/sdb.

Let me know if I need to post any more information.

Here are my Boot Info Script results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

Ubuntu-Root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

Ubuntu-Swap: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

Ubuntu-tmp: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

Ubuntu-usr: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

Ubuntu-var: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

Ubuntu-usrlocal: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

Ubuntu-Home: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    66,052,095    66,050,048   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       963,899       963,837  83 Linux
/dev/sdb2             976,896   312,498,175   311,521,280  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/test 6oQkX9-E3pG-ezMb-EHrU-e0gn-J5PZ-sprJuj LVM2_member                               
/dev/mapper/Ubuntu-Home b0aa8032-9f52-4427-acee-ce508f65606f   ext4                                     
/dev/mapper/Ubuntu-Root 68e816f5-f2b3-408f-8645-7b6dc3e4c683   ext4                                     
/dev/mapper/Ubuntu-tmp aef7def0-891b-4b70-9a02-8d24840c4daa   ext4                                     
/dev/mapper/Ubuntu-usr 30e20962-5af7-414e-9a45-e6326f103ca2   ext4                                     
/dev/mapper/Ubuntu-usrlocal 33062bf0-2d1e-4869-9232-79e04fcb7441   ext4                                     
/dev/mapper/Ubuntu-var 24bab8e5-cfca-4d3d-b9c4-5f30c5553521   ext4                                     
/dev/sda1        4836FBBA36FBA75A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        df487720-4629-4bb5-aed0-32563f362c9a   ext2                                     
/dev/sdb2        df03bc74-a8be-4d2c-aba0-71193382b062   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
test
Ubuntu-Home
Ubuntu-Root
Ubuntu-Swap
Ubuntu-tmp
Ubuntu-usr
Ubuntu-usrlocal
Ubuntu-var

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/Ubuntu-Root /mnt                     ext4       (rw)
/dev/sdb1        /mnt/boot                ext2       (rw)
/dev             /mnt/dev                 none       (rw,bind)


============================ Ubuntu-Root/etc/fstab: ============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Ubuntu-Root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=caae870d-61e2-4f9b-b1a9-6b1e345384a0 /boot           ext2    defaults        0       2
/dev/mapper/Ubuntu-Home /home           ext4    defaults        0       2
/dev/mapper/Ubuntu-tmp /tmp            ext4    defaults        0       2
/dev/mapper/Ubuntu-usr /usr            ext4    defaults        0       2
/dev/mapper/Ubuntu-usrlocal /usr/local      ext4    defaults        0       2
/dev/mapper/Ubuntu-var /var            ext4    defaults        0       2
/dev/mapper/Ubuntu-Swap none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  3c 15 4f 34 c7 f9 c7 3e  81 4a f6 99 80 ff 73 fa  |<.O4...>.J....s.|
00000080  17 c5 09 d5 9f 5b cc 77  d5 5a 43 4f 77 3f c4 3e  |.....[.w.ZCOw?.>|
00000090  e8 df 17 77 70 c9 1f a3  a3 17 6d 56 79 5a bb 95  |...wp.....mVyZ..|
000000a0  fe f1 7d ef 00 00 76 a7  64 66 30 33 62 63 37 34  |..}...v.df03bc74|
000000b0  2d 61 38 62 65 2d 34 64  32 63 2d 61 62 61 30 2d  |-a8be-4d2c-aba0-|
000000c0  37 31 31 39 33 33 38 32  62 30 36 32 00 00 00 00  |71193382b062....|
000000d0  00 ac 71 f3 00 01 db fb  d9 34 2f 2c 50 41 e3 ab  |..q......4/,PA..|
000000e0  24 f6 c4 6d d5 0e 73 8e  f1 a2 6f 0b fe f4 8d 52  |$..m..s...o....R|
000000f0  a3 d3 de 43 15 7e 97 a3  00 00 00 08 00 00 0f a0  |...C.~..........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```Here's what's in grub (/etc/default/grub):
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Thanks for the help!

---

### Post by shadowofblood on 2010-11-15
I added my Boot Info Script results for more information.

I noticed at the top, it says I have Grub2 installed on /dev/sda looking at partition #2 and also installed on /dev/sdb looking at partition #1.

It shouldn't be installed on /dev/sda.  I never did that.  Should I remove it?

FYI: /dev/sda doesn't have an OS installed; it's just temporary storage ATM.

---

### Post by shadowofblood on 2010-11-15
Any ideas?
I haven't been able to use my computer for several days now :(

EDIT: I added the contents of /etc/default/grub to the first post.

---

### Post by shadowofblood on 2010-11-15
Any Ubuntu gurus out there willing to give this a shot? :confused:

I'm still trying to figure it out, but I'm getting nowhere.  Every attempt I make either fails to install, or brings up that annoying "minimal bash" grub screen. :(

---

### Post by shadowofblood on 2010-11-16
3rd page bump.

Still no answers? :confused:

EDIT: Sorry about all the bumps; I just now learned about the unanswered search feature =\

---

### Post by dino99 on 2010-11-16
its easier :)

boot on partedmagic ( [http://partedmagic.com/](http://partedmagic.com/) ) to create 3 partitions:

- / : which is "root", make it bootable, ext4, ~ 12 Gb (take note of its name, something like /dev/sd?, the installer in manual mode will ask about it )

- swap : ~ 2 Gb

- /home : ext3 or ext4, unlimited space to store your data and settings

then use the "alternate" iso to install it on / , and install grub2 on /dev/sd? ( ? is a letter )

then you can choose to boot on hdd into the bios.

about luks:
[http://blog.kumina.nl/2010/07/two-factor-luks-using-ubuntu/](http://blog.kumina.nl/2010/07/two-factor-luks-using-ubuntu/)

---

### Post by Quackers on 2010-11-16
In your ubuntu-root partition you have the only ubuntu boot file on your system (etc/fstab) but there should be 3 boot files in total. 
Grub on sdb is looking at sdb1 for the boot files because that's where you told it to look when you mounted sdb1 and installed grub to sdb.
I would say that you need to boot from the live cd and mount the ubuntu-root partition then purge and re-install grub then install grub to the root-directory of sda and sdb (if your bios is setup to look at the first HDD as the boot device).
Having said all that, I don't know if /dev/mapper/Ubuntu-Root can be mounted in the same way as /dev/sdb1 is. 
Your partition structure is, to say the least, complicated, and I suspect this is the problem.
The guide for purging/re-installing grub is below, but as I have said, I don't know whether those commands will work for your situation.
Maybe somebody else can comment on that.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by shadowofblood on 2010-11-16
I booted back into the alternate cd and started over.  For some reason it worked fine this time.  I think it couldn't properly install the bootloader the first time because the "/boot" partition didn't end on a cylinder boundary.  I fixed that and it installed just fine :)

Thanks for the help!

---

### Post by Quackers on 2010-11-16
That's great :-) Another happy Ubunuer!

---

