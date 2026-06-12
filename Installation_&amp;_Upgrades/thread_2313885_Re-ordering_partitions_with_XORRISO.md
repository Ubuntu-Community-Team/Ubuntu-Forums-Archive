---
title: "Re-ordering partitions with XORRISO"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by goldstein2 on 2016-02-16
Hello,

I have successfully generated a new custom build Ubuntu live image with xorriso to be used with USB stick. Furthermore, I was also able to append a partition to the end of the partition table using xorriso. 

```
Device     Boot   Start     End Sectors  Size Id Type
/dev/sde1  *          0 3002879 3002880  1.4G  0 Empty
/dev/sde2          9492   14035    4544  2.2M ef EFI (FAT-12/16/32)
/dev/sde3       3002880 3102879  100000 48.8M  b W95 FAT32
```

Is it possible to add yet another FAT32 partition to the beginning of the partition table as /dev/sdX1? Bellow is a preferred partition order:
 
[LIST=1]
[*]FAT32 extra partition for persistent storage ( to allow USB disk to by mounted by MS Windows ) 
[*]System partition <boot> 
[*]EFI partition 
[*]FAT32 extra partition for persistent storage 
[/LIST]

Lastly, would the above preferred partition layout of the live system limit its ability to boot in EFI/Legacy mode on some hardware?

thank you

---

### Post by scdbackup on 2016-02-17
Hi,

there is no feature in xorriso which would prepend a partition
before the partition which covers the ISO 9660 filesystem.

Such a feature would not match easily with the main goal to make
the ISO bootable via El Torito from CD/DVD/BD. This goal demands
that block 17 contains the El Torito Boot Record. Further the
boot loaders expect the ISO to be mountable by the base device
/dev/sde if it is presented on HDD (hard disk, USB stick, ...).

So - more or less - xorriso is bound to let the ISO filesystem
begin at the start of the device. I am not sure whether this
absolutely prevents a FAT32 partition at the start of the device,
but it certainly makes the task quite tricky.

Why must it be the first partition ?
Would MS-Windows refuse to mount partition 4 ?

-----------------------------------------------------------------

Possible hack:

One could replace partition entry 1 (overall ISO filesystem) by an
entry which points to a large data file inside the ISO filesystem.

Sketch (to be elaborated):

- Create a FAT32 fileystem image file of desired size on hard disk.

- Add this file to the ISO when xorriso packs it up.
  Use option --sort-weight to force it to be stored before the
  image file of the EFI System Partition.

- When the ISO image is written, inquire the block address of the file
in the ISO by
```

xorriso -indev ...path.to.ISO... -find ...path.of.FAT.in.ISO... -exec report_lba --

```
which will report something like
```

Report layout: xt , Startlba ,   Blocks , Filesize , ISO image path
File data lba:  0 ,     9512 ,   131072 , 67108864 , '...path.of.FAT.in.ISO...'

```

- Multiply the "Startlba" (here 9512) by 4 to convert from ISO block
  size 2048 to partition table block size 512. Divide the "Filesize"
  (here 67108864) by 512 to get the block count. Round up, if the
  result is not integer.
  
- Use a partition editor to replace partition 1 by a new partition entry
  which shows the computed start address and block count.
  Set the boot/active flag, because some BIOS want to see it at
  some partition of the table.

This is quite similar to what xorriso does internally with the EFI
System Partition image file, when option -e gets modified by option
-isohybrid-gpt-basdat.

You would get

1. FAT32 for MS-Windows (with boot flag)
2. EFI System Partition.
3. FAT32 extra partition

-----------------------------------------------------------------------

> Lastly, would the above preferred partition layout of the live system
> limit its ability to boot in EFI/Legacy mode on some hardware?

Unless the lack of a mountable ISO partition confuses ISOLINUX,
it should work. GRUB2's grub-mkrescue produces no mountable ISO
partition and GRUB2 boots fine from those images.

Except the possible desire for a boot/active flag, the legacy (BIOS)
firmware mode of booting does not refer to partition tables but rather
relies on executable x86 machine code at the very beginning of the
disk device.
But this only brings up the first stage of the boot loader, which then
is free to do and demand what it wants.

Of course you lose the opportunity to mount the ISO as partition
and thus to omit -o loop when additionally mounting other partitions.

Have a nice day :)

Thomas

---

### Post by sudodus on 2016-02-17
1. Make a persistent live drive with mkusb (from an Ubuntu based or Debian Jessie based iso file)

2. See how it works and check the partition table.

Notice how I make it work with partition number one with an NTFS file system in order for it to mount in Windows. It is partition number one, but located at the end of the drive. This system works with 4 TB USB drives (I have tested it). So you get a persistent live drive which is compatible with Windows.

3. Look into the code of mkusb (it is a simple bash script, so there is no compiled code). Maybe you can borrow ideas from it.

-o-

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by scdbackup on 2016-02-17
Hi,

is there a way to let mkusb-nox perform Persistent Live ?
(I did let it perform the Install job, but that's only a flat
copy of the ISO.)

./mkusb -h proposes "p" as second argument. But if i give this
to mkusb-nox, i only get the help text.
mkusb on the other hand wants me to install "zenity", which looks
like half a graphcal desktop with its dependencies:
  [https://packages.debian.org/jessie/zenity](https://packages.debian.org/jessie/zenity)

webkit ... isn't that the thing which needs a day to compile on amd64 ?
Ah no. Only 7 to 11 hours. (buildd must have gotten better CPUs.)

I want to test on a small Jessie VM. Best without the need to
open my workstation X to its inhabitants. 

--------------------------------------------------------------------------------------

If this is not possible without GUI, could you please post a fdisk -l of
an example Persistent Live ?

Have a nice day :)

Thomas

---

### Post by sudodus on 2016-02-17
No, mkusb-nox is simple. It only clones. You need mkusb (with a GUI) to make persistent live drives 'the mkusb way'. But you can install mkusb temporarily to a live USB drive and from there make a persistent live system in another USB drive, so you need not touch your installed system.

There are also the following alternatives (compressed image files) with simpler partition tables, that can be installed with mkusb-nox,

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

---

### Post by sudodus on 2016-02-17
Lists of the partition table of a persistent live drive made by mkusb, in this case I selected 9% of the remaining drive space for persistence (and 91% for the 'usbdata' ntfs partition).

```
$ [COLOR="#0000FF"]**sudo lsblk -fm /dev/sdd**[/COLOR]
NAME   FSTYPE  LABEL                     MOUNTPOINT                  NAME     SIZE OWNER GROUP MODE
sdd                                                                  sdd    119,2G root  disk  brw-rw----
&#9500;&#9472;sdd1 ntfs    usbdata                   /media/usbdata              &#9500;&#9472;sdd1 107,7G root  disk  brw-rw----
&#9500;&#9472;sdd2                                                               &#9500;&#9472;sdd2     1M root  disk  brw-rw----
&#9500;&#9472;sdd3 vfat    trusty64                                              &#9500;&#9472;sdd3   122M root  disk  brw-rw----
&#9500;&#9472;sdd4 iso9660 Lubuntu 14.04.4 LTS amd64 /media/Lubuntu 14.04.4 LTS  &#9500;&#9472;sdd4   755M root  disk  brw-rw----
&#9492;&#9472;sdd5 ext4    casper-rw                 /media/casper-rw            &#9492;&#9472;sdd5  10,7G root  disk  brw-rw----
$ [COLOR="#0000FF"]**sudo parted /dev/sdd print**[/COLOR]
Modell: SanDisk ExtremePro (scsi)
Disk /dev/sdd: 128GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: gpt

Nummer  Början  Slutet  Storlek  Filsystem  Namn     Flaggor
 2      1049kB  2097kB  1049kB              primary  bios_grub
 3      2097kB  130MB   128MB    fat32      primary  startbar
 4      130MB   922MB   792MB               primary
 5      922MB   12,4GB  11,4GB   ext4       primary
 1      12,4GB  128GB   116GB    ntfs       primary  msftdata

$ [COLOR="#0000FF"]**sudo gdisk -l /dev/sdd**[/COLOR]
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A43BC65D-AC86-42C1-A228-A55EC3FF85AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1        24143872       250068991   107.7 GiB   0700  primary
   2            2048            4095   1024.0 KiB  EF02  primary
   3            4096          253951   122.0 MiB   EF00  primary
   4          253952         1800191   755.0 MiB   8300  primary
   5         1800192        24143871   10.7 GiB    8300  primary
$ 
```

---

### Post by scdbackup on 2016-02-17
Hi,

real GPT, not the ignorable one of isohybrid, about which i still
wonder whether it is actually a historical remnant of mjg's
development effort.

Do i get it right that a GRUB2 installation in /dev/sdd2 has
a configuration file which offers to chainload the MBR
(now in this case: EBR) of the ISO image in /dev/sdd4 ?

Have a nice day :)

Thomas

---

### Post by sudodus on 2016-02-17
Partition number 2, with a bios_grub flag is the location in GPT for grub corresponding to the 'unallocated space' before the partitions for grub in an MSDOS partition table to boot in BIOS mode. The configuration files are located in partition number 3 with a fat32 file system.

I think you are too interested to abstain from installing mkusb somewhere and make some persistent live systems. I think you need hands on experience ;-)

---

### Post by scdbackup on 2016-02-17
Hi,

first a note to goldstein2, our original poster:

The result of mkusb looks quite like what you want, doesn't it ?

-------------------------------------------------------------------

sudodus wrote:
> I think you are too interested to abstain from installing mkusb
> somewhere and make some persistent live systems. I think you
> need hands on experience

I am curious, indeed. After all, i assume my xorriso packs up
at least half of the ISOs which mkusb puts onto USB sticks.

But really, webkit et.al. just to do some elaborate data plumbing ?
That's overdone. (Says the guy with the 4000 lines man page ... cough.)

A command line interface would be benefitial for paranoid old people
from upstream userland. With an option -batch (or so) which would
keep zenith from being used. If the job is not described sufficiently
by the other arguments, then mkusb may well complain and fail.

I can understand why superuser authority is needed to run a smart
USB stick creator. But letting the superuser run all that stuff
which is dangling underneath zenith ?
Urgh ... nurse ... bring my beta blockers ...

Have a nice day :)

Thomas

---

### Post by sudodus on 2016-02-17
For a long time mkusb was only what mkusb-nox is today - and it was enough for me. But several people asked for a GUI and user friendliness. They told me, that most people won't even try it, unless it 'looks like a real program' alias 'has a fancy GUI'. And people wanted mkusb to make persistent live drives too, because the current tools are rather limited.

You 'paranoid old people from upstream userland' are rather few, and maybe you don't need mkusb. You can harness ***dd*** and you can create casper-rw partitions manually whenever and wherever you want it.

You are very welcome to take the code (the shell-script) and

1. Remove all the GUI stuff or maybe downgrade it to ***dialog*** instead of ***zenity***.

2. Run mkusb without elevated permissions (and use sudo locally only for the commands that really need it to work)

or if you would rather start from the very beginning and only borrow some concepts :-)

---

### Post by scdbackup on 2016-02-17
Hi,

>  They told me, that most people won't even try it,

Yeah. It's sad.
I have to fish for entertaining problem reports of Brasero or Xfburn
in order to meet my users of libburn and libisofs.

Cheers to goldstein2 for advanced toughness !

Have a nice day :)

Thomas

---

### Post by sudodus on 2016-02-17
> **scdbackup said:**
> ...

Cheers to goldstein2 for advanced toughness !

Have a nice day :)

Thomas

+1 :-)

---

### Post by goldstein2 on 2016-02-25
Hi Guys,

Thanks for all your input, it is much appreciated. I'm still fighting with this. At the moment it appears that the simplest solution ( not sure about the best ) is to first use xorriso to create isohybrid image of customized ubuntu and then use customized mkusb to put it on USB. This is what I have ended up with so far:

```

MODEL            NAME   FSTYPE  LABEL    MOUNTPOINT  SIZE
Ultra            sdd                                14.9G
                 &#9500;&#9472;sdd1 exfat   msdata              136M
                 &#9500;&#9472;sdd2                                1M
                 &#9500;&#9472;sdd3 vfat    boot                 122M
                 &#9500;&#9472;sdd4 iso9660 ISOIMAGE             1.5G
                 &#9500;&#9472;sdd5 vfat    data                100M
                 &#9492;&#9472;sdd6 vfat    data                100M
```

or:
```
Device       Start     End Sectors  Size Type
/dev/sdd1  3500032 3778559  278528  136M Microsoft basic data
/dev/sdd2     2048    4095    2048    1M BIOS boot
/dev/sdd3     4096  253951  249856  122M EFI System
/dev/sdd4   253952 3295231 3041280  1.5G Linux filesystem
/dev/sdd5  3295232 3500031  204800  100M Microsoft basic data
/dev/sdd6  3778560 3983359  204800  100M Microsoft basic data
```

I have slightly hacked the mkusb to remove persistence mode with altered grub config and yet add first partition for M$ Windows. The other partitions labeled "data" are just additional partitions to comply with project's requirements.

By default mkusb creates "ntfs" filesystem on the fist partition which is fine with linux or windows. However, it is not by default mountable on Mac OS without additional system tinkering and thus I have formated sdx1 with fat32 filesystem. However, from some reason I have lost an ability to boot with "SecureBoot" when first partition is formated as FAT32 or FAT16. The moment I format the first partition back to ntfs, ext4 or exfat it works again.

Command used to format sdx1 to FAT32:

```
mkfs.vfat -v -F 32 -n LABEL /dev/sdx1
```

I would still prefer to have FAT32 filesystem on sdx1. Can think of any particular reason for this behavior?

thank you

---

### Post by sudodus on 2016-02-25
Nice work :KS

I would be happy to get a copy of your version of mkusb. Please upload it (for example compressed) somewhere :-)

Maybe the boot system get confused by several partitions with a  FAT file system (even if you have the boot flag only on the correct one.

---

### Post by goldstein2 on 2016-02-29
> **sudodus said:**
> Nice work

I would be happy to get a copy of your version of mkusb. Please upload it (for example compressed) somewhere

Maybe the boot system get confused by several partitions with a FAT file system (even if you have the boot flag only on the correct one.

Hi sudodus,
What are you saying is that the system looks for a first FAT16/32 partition available and attempts to boot from it? If this is the case what's the point of the 
boot flag :-) I tried two different laptops and both failed to boot with FAT32 on the first partition. 

Anyway, I'm not sure if there is anything to upload as I only did few rather crude looking hacks to the mkusb script:
1) Create FAT32 on the first partition

Find the line ( approx line number 3608):
```
mkfs.ntfs -v -f -L "usbdata" "${2}1" 2>&1
```
comment it and add line:
```
mkfs.vfat -v -F 32 -n "usbdata" "${2}1" 2>&1
```  

2)Remove persistent boot mode
Find line ( approx line number 4624 ):
```

IFS=$old_IFS # restore default field separator

```

and under this line add line:
```

cat /path/to/your/cust_grub/config > $2

```
This will overwrite mkusb's default grub config with yours custom config. That is all, just select persistence mode when running mkusb script. It will still create the casper-rw partition but you can simply use parted 
to remove it if required and you are done. 
Sample grub config to get you started:


```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
menuentry "MyCustomUbuntu 1.0" {
 set root=(hd0,4)
    set gfxpayload=keep
    linux    ($root)/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    ($root)/casper/initrd.lz
}
```

Feel free to PM me if you need something more specific. 

thank you

---

### Post by goldstein2 on 2016-02-29
Hi Thomas,

I thought to give mkusb a fair try before your solution as it appeared simpler to me. As you can read above I've got a partial success with it however I would like to try your method before I move on. I would like to ask you to provide me with some beginner xorriso syntax to help me to accomplish the  following:

> **scdbackup said:**
> 
- Add this file to the ISO when xorriso packs it up.
  Use option --sort-weight to force it to be stored before the
  image file of the EFI System Partition.


Is there any chance to elaborate more about the above? 

> **scdbackup said:**
> 
Why must it be the first partition ?
Would MS-Windows refuse to mount partition 4 ?

My current understanding is that Windows recognizes two USB media types. USB hard disk drive and USB removable media. If USB removable is present windows only mounts first partition. Most of the USB sticks are USB removable media type. Do not quote me on this as I do not use windows for more than a decade now and my knowledge is outdated. [Reference]("http://ubuntuforums.org/showthread.php?t=1020293&p=9416480#post9416480"). 

I know there are workarounds to get mounted all partitions but this solution would not work for everyone.

thank you

---

### Post by yancek on 2016-02-29
> If USB removable is present windows only mounts first partition

Windows will only show/see the first partition on a pendrive/flash drive and it doesn't matter the filesystem type.  If you have other ntfs, vfat or windows partitions, they will not show.  Tested all this a few months ago.  Some people consider this a problem, microsoft doesn't and they are fully aware and have no intention of changing this.  You can find all kinds of sites discussing this if you care to.

---

### Post by sudodus on 2016-03-01
> **goldstein2 said:**
> Hi sudodus,
What are you saying is that the system looks for a first FAT16/32 partition available and attempts to boot from it? If this is the case what's the point of the 
boot flag :-) I tried two different laptops and both failed to boot with FAT32 on the first partition. 

Anyway, I'm not sure if there is anything to upload as I only did few rather crude looking hacks to the mkusb script:
1) Create FAT32 on the first partition

Find the line ( approx line number 3608):
```
mkfs.ntfs -v -f -L "usbdata" "${2}1" 2>&1
```
comment it and add line:
```
mkfs.vfat -v -F 32 -n "usbdata" "${2}1" 2>&1
```  

2)Remove persistent boot mode
Find line ( approx line number 4624 ):
```

IFS=$old_IFS # restore default field separator

```

and under this line add line:
```

cat /path/to/your/cust_grub/config > $2

```
This will overwrite mkusb's default grub config with yours custom config. That is all, just select persistence mode when running mkusb script. It will still create the casper-rw partition but you can simply use parted 
to remove it if required and you are done. 
Sample grub config to get you started:


```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
menuentry "MyCustomUbuntu 1.0" {
 set root=(hd0,4)
    set gfxpayload=keep
    linux    ($root)/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    ($root)/casper/initrd.lz
}
```

Feel free to PM me if you need something more specific. 

thank you

Thank *you* :-)

---

### Post by sudodus on 2016-03-01
> **yancek said:**
> Windows will only show/see the first partition on a pendrive/flash drive and it doesn't matter the filesystem type.  If you have other ntfs, vfat or windows partitions, they will not show.  Tested all this a few months ago.  Some people consider this a problem, microsoft doesn't and they are fully aware and have no intention of changing this.  You can find all kinds of sites discussing this if you care to.

+1

---

### Post by goldstein2 on 2016-03-06
Hi Guys,

I have tested the image made with mkusb on different laptop and it failed to boot. The Laptop has only UEFI and Legacy boot option but no secure boot. Using Legacy boot option I do not even get to Grub menu.  Using UEFI mode I get to the Grub Menu however, the following error message appears when selecting any of the boot items from the Grub menu list: 
```
error: disk `hd0,4' not found.
alloc magic is broken at 0xad0b9dc0: acf4a380
Aborted, Press any key to exit.
```

 The test ISO image works perfectly in all three boot modes on my other laptop. What could be the difference? I have also tested a fresh Ubuntu 14.04 image as a source image for mkusb and got the same result...

Any hints on what can be the issue?

thank you

---

### Post by sudodus on 2016-03-07
What computer is it (brand name and model)?

I know that some middle-aged HP computers are unwilling to boot to grub from USB. I can manage to boot from USB, If I make a similar system with an MSDOS partition table, and set the boot flag on the boot partition (even though grub should not need any boot flag). See the systems described in the following link (post #6 and the following posts),

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

Post #8 is a rather detailed description of how to do it, [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278)

---

### Post by scdbackup on 2016-03-07
Hi,

i got a message from goldstein2

> I would be really grateful if you could please provide an additional xorriso
> syntax help on your post

I guess you mean the first reply i gave to this thread:
[http://ubuntuforums.org/showthread.php?t=2313885&p=13441319#post13441319](http://ubuntuforums.org/showthread.php?t=2313885&p=13441319#post13441319)


I wrote:
> - Create a FAT32 fileystem image file of desired size on hard disk.

I understand that mkdosfs is the tool for this step.
Let's call this file $HOME/partition_image.fat

> - Add this file to the ISO when xorriso packs it up.
> Use option --sort-weight to force it to be stored before the
> image file of the EFI System Partition.

Assumed that you use the -as "mkisofs" emulation command this would be
```

  xorriso -as mkisofs ...other.options.and.filepaths... $HOME/partition_image.fat --sort-weight 2000000000 /partition_image.fat

```
Check whether your xorriso -as mkisofs run already contains
--sort-weight options. Surpass their weight numbers by the one
for /partition_image.fat.

> - When the ISO image is written, inquire the block address of the file
> in the ISO

```

  xorriso -indev ...path.to.iso... -find /partition_image.fat -exec report_lba --

```
will report something like
```

Report layout: xt , Startlba ,   Blocks , Filesize , ISO image path
File data lba:  0 ,      326 ,     4096 ,  8388608 , '/partition_image.fat'

```


> - Multiply the "Startlba" by 4 [...] Divide the "Filesize" by 512

Yields 1304 and 16384.


> - Use a partition editor to replace partition 1 by a new partition entry
> which shows the computed start address and block count.
> Set the boot/active flag, because some BIOS want to see it at
> some partition of the table.

/sbin/fdisk would be the tool to use.

If you need help with mkdosfs or fdisk, i am quite sure that there are
more skilled experts for them, than i am.

Have a nice day :)

Thomas

---

