---
title: "any alternative of &quot;hp usb disk storage format tool&quot;"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by pelerin21 on 2012-05-20
Hi,

Is there any alternative (which is open source) of "hp usb disk storage format tool" on Linux? (and for other OSes too)

Thanks!

---

### Post by Cheesemill on 2012-05-20
What are you trying to do?

If you just want to format a USB drive you can use Disk Utility which comes with Ubuntu.
If you want to do more sophisticated partitioning then install Gparted.

---

### Post by pelerin21 on 2012-05-20
> **Cheesemill said:**
> What are you trying to do?

If you just want to format a USB drive you can use Disk Utility which comes with Ubuntu.
If you want to do more sophisticated partitioning then install Gparted.

The tool that Im talking about is little bit different. It formats the usb but also makes the usb **bootable** for all BIOSes.

I was talked about bootability ( how to say ) of USB on many linux forums. But most of answers did not make my USB bootable for my BIOS (mainboard). But I format my USB with this tool and now It is bootable.

So I am asking now about an open source alternative (if possible cross platform).

Thanks!

---

### Post by lkraemer on 2012-05-21
pelerin21,
All that the HP USB Storage Format Utility did was allow you to Check a Box for FAT/FAT 32 Format &:   Creating a DOS Startup Disk by

1.  Using internal MS-DOS System Files

2.  Using DOS System files located at:___________________

There were two version of that software V2.00.xx & V2.1.8.x, but it did allow me to repair several USB Flash Drives that were somehow trashed and couldn't be formatted.

I've tried running it under Wine & Crossover and it doesn't work correctly.

I'd suggest looking at the following packages which will can also write the MS-DOS (or similar) boot files.

1.  GRUB - Ver .97
    [http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

2.  ms-sys File Manager  (may not be in Repository)
    [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
```

sudo apt-get install ms-sys 

```
then........
```

sudo blkid
sudo ms-sys --mbr /dev/sdX

```
or whatever your drive is, to find that out type sudo fidsk -l or sudo blkid

3.  syslinux  (probably in Repository)
It should be easy to use any of the above to create a Bootable USB Drive that works the same as the HP Utility.

4.  Another option is to build one as a SEED unit and then use DD to make an Image File of the MBR.  You would use DD each time
you wanted the Image File written to a fresh formatted USB Flash Drive.

lk

---

### Post by pelerin21 on 2012-05-28
> **lkraemer said:**
> pelerin21,
All that the HP USB Storage Format Utility did was allow you to Check a Box for FAT/FAT 32 Format &:   Creating a DOS Startup Disk by

1.  Using internal MS-DOS System Files

2.  Using DOS System files located at:___________________

There were two version of that software V2.00.xx & V2.1.8.x, but it did allow me to repair several USB Flash Drives that were somehow trashed and couldn't be formatted.

I've tried running it under Wine & Crossover and it doesn't work correctly.

I'd suggest looking at the following packages which will can also write the MS-DOS (or similar) boot files.

1.  GRUB - Ver .97
    [http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

2.  ms-sys File Manager  (may not be in Repository)
    [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
```

sudo apt-get install ms-sys 

```then........
```

sudo blkid
sudo ms-sys --mbr /dev/sdX

```or whatever your drive is, to find that out type sudo fidsk -l or sudo blkid

3.  syslinux  (probably in Repository)
It should be easy to use any of the above to create a Bootable USB Drive that works the same as the HP Utility.

4.  Another option is to build one as a SEED unit and then use DD to make an Image File of the MBR.  You would use DD each time
you wanted the Image File written to a fresh formatted USB Flash Drive.

lk

1)I did not understand how we can solve this problem about GRUB. Because I need to boot this USB also some other peoples machines.

2) I get this error when I install the ms-sys File Manager:
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127

3)  syslinux is just for windows OS.
 
4)I did not understand anything from this option :(

---

### Post by ottosykora on 2012-05-28
the HP tool does indeed little bit of something more then just format and include some boot files from a floppy image.

Many usb sticks on the market, are formated in a way, that there is no mbr or not even traces of it in the formating. It still provides a partition with beginning and end, but that is abt all.

The HP tool takes care of such strange formated sticks and provides them normal classical format with mbr and this space to write the needed codes there.

One can ni general achieve similar with writing one time something to it with thigs like unetbootin or similar utility. This will also completely reformat the usb stick and give it a format with proper fields for mbr etc prepared.

Not all stick need this treatment, but some do.

Note also, if the stick is badly formated from the manufacturer in a way that there is no space for mbr etc reserveed, the gparted etc will also not help much here.

---

### Post by pelerin21 on 2012-05-29
> **ottosykora said:**
> the HP tool does indeed little bit of something more then just format and include some boot files from a floppy image.

Many usb sticks on the market, are formated in a way, that there is no mbr or not even traces of it in the formating. It still provides a partition with beginning and end, but that is abt all.

The HP tool takes care of such strange formated sticks and provides them normal classical format with mbr and this space to write the needed codes there.

One can ni general achieve similar with writing one time something to it with thigs like unetbootin or similar utility. This will also completely reformat the usb stick and give it a format with proper fields for mbr etc prepared.

Not all stick need this treatment, but some do.

Note also, if the stick is badly formated from the manufacturer in a way that there is no space for mbr etc reserveed, the gparted etc will also not help much here.

I already unetbootin...

---

### Post by lkraemer on 2012-05-29
pelerin21,
> 
1)I did not understand how we can solve this problem about GRUB. Because I need to boot this USB also some other peoples machines.

Keep Reading...............Because I tried to follow your path
> 

2) I get this error when I install the ms-sys File Manager:
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127

It appears you didn't install ms-sys, but rather are trying to compile it from source.  You will need
to have build-essential and the correct headers for your Kernel to get make to execute properly.
Please open the ms-sys-*.tar.gz file and read this file: README

Also REF:
[http://ubuntuforums.org/showthread.php?t=1901733&highlight=fortran&page=2](http://ubuntuforums.org/showthread.php?t=1901733&highlight=fortran&page=2)
Starting at:  **INSTALL REQUIRED SOFTWARE FOR COMPILE:**

> 
3) syslinux is just for windows OS.

syslinux is *nix and it can be used to create what you need for the USB Flash Drive.
> 
SYSLINUX is a collection of boot loaders which operates off Linux ext2/3/4 or
btrfs filesystems, MS-DOS FAT filesystems, network servers using PXE firmware,
or from CD-ROMs.


> 
4)I did not understand anything from this option

Keep Reading...............Because I tried to follow your path


Let's take a step backwards in time.  Assume you have a MSDOS 3.3 Machine, with a Floppy Drive that boots from a
1.2G Hard Drive with MSDOS 3.3 installed.  Now, you want to create a boot floppy................

How would/could you do that?

I'd stick a fresh floppy in my Floppy Drive and then format it with:
```

C:/> format a:

```
That will format the floppy in "A" Drive.  But, will it boot?  Mine doesn't.  It's missing some system files and the MBR.

How do I make it boot?  Well I need to have a Initial Program Loader (IPL) and some system files, and a Master Boot Record (MBR) created on the Formatted Floppy. (Formatting the floppy just creates the filesystem, and layout (FAT or FAT32) for the storage.)

I can do that in one of two ways in MSDOS 3.3:
1.  C:/> format a:/s
2.  C:/> format a:
2.a C:/> sys a:
    If the hidden system files, MSDOS.SYS and IO.SYS aren't on the Floppy it won't boot.  There will also be COMMAND.COM on the
floppy.  I always copy SYS.COM to every floppy too!

Now the floppy boots, but the config.sys and autoexec.bat and other needed files are still missing.  But, you can copy those and continue building your system disk.

So, with this bit of knowledge, can you now build a floppy or Hard Drive that boots MSDOS?   

Linux works the same, except there are different commands, and lots more choices..........  mkdosfs, mkfs.ext2, mkfs.ext3,
mkfs.msdos, mkfs.vfat
You can use:
```

man mkdosfs
man mkfs.vfat

```
to check out what the commands do.  (ie. same as DOS format a:)

The command ms-sys in *nix does the same thing as sys a: in MSDOS 3.3.
> 
NAME
       ms-sys - write Microsoft boot block

SYNOPSIS
       ms-sys [options] [device]

DESCRIPTION
       ms-sys is for writing Microsoft compatible boot records.

OPTIONS
       A summary of options is included below.

       -1, --fat12
              Write a FAT12 floppy boot record to device.

       -2, --fat32nt
              Write a FAT32 partition NT boot record to device.

       -3, --fat32
              Write a FAT32 partition DOS (Win9x) boot record to device.

       -4, --fat32free
              Write a FAT32 partition FreeDOS boot record to device.

       -5, --fat16free
              Write a FAT16 partition FreeDOS boot record to device.

       -6, --fat16
              Write a FAT16 partition DOS (Win9x) boot record to device.

       -l, --wipelabel
              Reset partition disk label in boot record.

       -p, --partition
              Write  partition  info  (hidden  sectors, heads and drive id) to
              boot record. This might be needed on some  partitions  depending
              on which program was used to create the file system.

       -H <n>, --heads <n>
              Set number of heads written with -p switch.

       -7, --mbr7
              Write a Windows 7 master boot record to device.  Does not change
              Windows Disk Signature (bytes 01b8-01bd).  This  MBR  will  boot
              certain  partition types beyond cylinder 1024 using LBA address&#8208;
              ing.

       -i, --mbrvista
              Write a Windows Vista master boot record to  device.   Does  not
              change  Windows Disk Signature (bytes 01b8-01bd).  This MBR will
              boot certain partition types  beyond  cylinder  1024  using  LBA
              addressing.

       -m, --mbr
              Write a Windows 2000/XP/2003 master boot record to device.  Does
              not change Windows Disk Signature (bytes 01b8-01bd).   This  MBR
              will boot certain partition types beyond cylinder 1024 using LBA
              addressing.

       -9, --mbr95b
              Write a Windows 95B/98/98SE/ME master  boot  record  to  device.
              Does not change Windows Disk Signature (bytes 01b8-01bd) or boot
              drive and time (bytes 00da-00df).  This MBR  will  boot  FAT-LBA
              partition  types  0c  and  0e  beyond  cylinder  1024  using LBA
              addressing.

       -d, --mbrdos
              Write a DOS/Windows NT master boot record to device.   Does  not
              change  Windows Disk Signature (bytes 01b8-01bd).  This MBR will
              not boot beyond  cylinder  1024  as  it  does  not  support  LBA
              addressing.

       -s, --mbrsyslinux
              Write  a  public  domain  syslinux master boot record to device.
              Does not change Windows Disk Signature (bytes 01b8-01bd).   This
              MBR will boot any partition types beyond cylinder 1024 using LBA
              addressing.

       -z, --mbrzero
              Write an empty (zeroed,  non-bootable)  master  boot  record  to
              device.  Zeroes all bytes except the partition map and signature
              (bytes 01be-01ff).  Similar to the  empty  DOS  partition  table
              that fdisk creates.

       -f, --force
              Force writing of boot record.

       -h, --help
              Show summary of options.

       -v, --version
              Show program version.

       -w, --write
              Write automatically selected boot record to device.

       If  ms-sys  is  started  without any options a simple diagnosis will be
       done on the given device.

EXAMPLES
       Please note that  Windows  ME  is  not  useful  for  making  standalone
       bootable floppies. However, Win9x and DOS works fine with the first two
       examples.

       Creating a 1.68 MB bootable floppy

       This example assumes that you have your windows installation mounted at
       /dosc and also have mtools and fdformat installed.

       fdformat /dev/fd0u1680
       mformat a:
       ms-sys -w /dev/fd0
       mcopy /dosc/io.sys a:
       mcopy /dosc/msdos.sys a:
       mcopy /dosc/command.com a:

       Creating  a  bootable  2.8  MB  floppy  image  to use with an el-torito
       bootable CD

       dd if=/dev/zero of=floppy288.img bs=1024 count=2880
       /sbin/mkdosfs floppy288.img
       ms-sys -1 -f floppy288.img
       su
       mount -o loop floppy288.img /mnt
       cp msdos.sys /mnt/
       cp io.sys /mnt/
       cp command.com /mnt/
       (it might also be a good idea to add a config.sys and autoexec.bat with
       CDROM support)
       umount /mnt
       exit
       cp floppy288.img cd-files/boot.img
       mkisofs -b boot.img -c boot.cat -o cdimage.iso cd-files
       (burn the file cdimage.iso to a CD with cdrecord or another program)

       restoring a backup of Win9x or Win ME to a fresh hard disk

       Step 1, use GNU parted to create your FAT32 partition and file system:

       parted (then create partition and file system)

       Step 2, write the MBR:

       ms-sys -w /dev/hda

       Step 3, write the FAT32 partition boot record:

       ms-sys -w /dev/hda1

       Step 4, mount your new filesystem:

       mount /dev/hda1 /mnt

       Step 5, read your backup

       cd /mnt; tar -xzvf /path/to/my_windows_backup_file.tgz


SEE ALSO
       mformat(1)  fdformat(8)  mkdosfs(8)  mkisofs(8)


Does that make sense?  And that is just one option of the many I listed.  You could also use Grand Unified Boot Loader (GRUB), syslinux, or Windows to make a SEED unit with the HP Format utility.

Once you have a SEED Unit, created in WinXX, you can copy it to a File in *nix with DD.  Then, insert a Fresh USB Flash Drive, and copy the file to the Fresh USB Flash Drive.
```

sudo blkid                        ##find /dev/sd[abcde]
dd if=/dev/sdx of=pendrive.img conv=notrunc; sync       ##copy to file
                                                        ##insert new USB Flash
dd if=pendrive.img of=/dev/sdx conv=notrunc; sync       ##copy file to New USB Flash

```
Boot the new USB Flash.

REF:
[http://www.mayrhofer.eu.org/making-usb-sticks-bootable](http://www.mayrhofer.eu.org/making-usb-sticks-bootable)


lk

---

### Post by pelerin21 on 2012-05-29
@lkraemer first thank you for helping me...

1) I installed the required packages here: 
[http://ubuntuforums.org/showthread.php?t=1901733&highlight=fortran&page=2](http://ubuntuforums.org/showthread.php?t=1901733&highlight=fortran&page=2)

Also I have the liblocale-msgfmt-perl package. But I face my old problem when I run "make" command:

```
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127
```

I could not understand you exactly bacause of my bad English. Sorry...

Please add note that "ms-sys" will work on Windows too...

Thanks...

---

### Post by lkraemer on 2012-05-29
pelerin21,
I'm assuming you downloaded the following tar.gz package:
> 
ms-sys-2.2.1.tar.gz

and that you saved it in a folder named ms-sys on your Desktop.
That path would be ~/Desktop/ms-sys

Extract the files to a subdirectory with:
```

cd ~/Desktop/ms-sys
tar -xzvf ms-sys-2.2.1.tar.gz
cd ms-sys-2.2.1

```
Now you are ready to compile the source.........assuming that all the libs and requirements are met.
I haven't a clue as to what Version of *nix you are using, or if ms-sys is supported, or if your 
system is set up to compile code.

If you can locate a package for ms-sys that you can download it might be the quick way get it installed.
I do know that Debian 6 "Squeeze" does have it available, because that is what I've been running since
it was released.  I just downloaded the source, compiled the code, and created the deb and installed.


**COMPILE ms-sys FROM SOURCE:**

1. Execute the following code:
```

make clean
make

```
make cean won't do anything the first time you execute it.......................
If you don't get any errors continue, otherwise locate what is causing the errors and fix the problems.  Then repeat step #1.

If you get errors post the output of:
```

env
cat .bashrc

```

When it compiles without errors do:
```

sudo make install

```
Then locate the binary and execute the software with:
```

sudo updatedb
which ms-sys
ms-sys

```
From there refer to:
```

man ms-sys

```


LK

---

### Post by pelerin21 on 2012-05-29
@lkraemer I solve the installation problem. Now ms-sys works fine. Now which command should I type?

---

### Post by lkraemer on 2012-05-29
pelerin21,
That depends on what you want to do.  I haven't a clue as to what your intent is/was or where you are headed.  I was just offering support to
your questions, and giving suggestions/guidance.  

As Cheesemill previously stated, "What are you trying to do?"

If it were me, I'd create a USB Flash Drive in WinXX with the HP Format Utility.  Then I'd do a SAFE REMOVE from Windows, and boot *nix.  From there I'd plug in the USB Flash Drive and make me a SEED unit, and use dd to copy the file to *nix.  That way you can write the file back to any USB Flash Drive and have a duplicate.  But, I'm willing to bet I think different than you.

And, if you have the HP format Utility, why not just format and prepare 4-6 USB drives and skip doing it in *nix?

Maybe you want to try a couple of different ways to see if the USB Flash Drive boots when you are finished.  Just be
extra careful when you use the /dev/sd [abcd] designations and use the fdisk -l or sudo blkid first so you don't blow
away a hard drive or external USB drive by typing the wrong /dev/sdX command.

You could try any of the following (or some combination of) to prepare a test USB Flash Drive:

SmartBootManager
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

Gparted
Grub
lilo
ms-sys
syslinux


Maybe it takes a total SLOW re-reading of all postings to get a grasp on where you are wanting to be, and the path you'll take to get there.

I don't mean to be rude......

LK

---

### Post by pelerin21 on 2012-05-30
> **lkraemer said:**
> pelerin21,
That depends on what you want to do.
...


My (some) USB flash drive does not boot on (some) computers. Someone told me to try to format these USB flash drives with "hp usb disk storage format tool", and than put the iso inside (with any app like unetbootin), and than try to boot. And it works perfect. 
(Additional note: If the bootable USB (which formatted by "hp usb disk storage format tool") will format again with Windows default formatter ( [http://www.bablotech.com/wp-content/uploads/2009/08/usb-drive-format.jpg](http://www.bablotech.com/wp-content/uploads/2009/08/usb-drive-format.jpg) ) , the USB losts the bootability. That's why I am formatting it always with "hp usb disk storage format tool". )

Nowadays I am thinking to use just Linux. I will remove the Windows from my computers. So I just asked an alternative for "hp usb disk storage format tool". You told me to install the "ms-sys" which I installed yesterday.

Now I'm asking with which command (ms-sys -bla -bla) I can format my USB flash drives to make them bootable on all machines (computers).

Thank you!

---

### Post by lkraemer on 2012-05-31
pelerin21,
Try as I might I haven't got ms-sys or syslinux to create one that boots.
So, there is something else going on that I haven't found yet.

But, I did find another program that works good in Windows.

[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Rufus.exe does work good in Linux, running Windows XP in Virtualbox.
I've tested that. (The HP USB Format Utility works good if you run
Virtualbox (non-ose Version), then run Windows XP, with a filter
set for the USB port.)

Also:
[http://www.rmprepusb.com/home/what-you-can-do-with-rmprepusb](http://www.rmprepusb.com/home/what-you-can-do-with-rmprepusb)

RMPrepUSB & FlashBoot......

I also found a site that explains about C H S having to be set like a
Hard Disk, and slightly smaller than the USB Flash Drive's Size.
> 
# partition the USB stick so that H=255,Sec=63, and C*H*S is
# the size of the disk (or slightly smaller). This is KEY.

[http://www.rmprepusb.com/tutorials/usbpreplinux](http://www.rmprepusb.com/tutorials/usbpreplinux)

But once again I haven't got that to work yet!


lk

---

### Post by pelerin21 on 2012-06-01
@lkraemer I open the gparted after I format with default Windows formatter. I get all informations. I open also gparted after I format the USB with "hp usb disk storage format tool". I see that Windows creates a very very small un-formatted partition. But HP tool has just one partition.

So now I understand the reason :)

Thank you for you interest...

---

