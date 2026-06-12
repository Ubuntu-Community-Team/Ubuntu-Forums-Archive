---
title: "Lubuntu Install on 8gb stick only using 4gb"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by gerald12 on 2016-04-24
Hello,
I'm trying to install Lubuntu (64 bit) onto an 8gb stick, but use the full capacity.
I am booting from a live cd and running the install program. When I follow all the default options, its installs, but only formats the stick to 4gb (and I am then unable to install updates etc as it says there is no space left).
I tried fat32 (with a known 4gb limit) and ext3, still only see 4gb.
I tried (dismally) to change the format options, but only managed to screw up my HDD OS (and have had to reinstall everything :-( ).

Can someone step-by-step me thought installing Lubuntu onto a 8gb stick, but get it to use the full capacity, not the 4gb patition it seems to want to use ?

thanks in advance

---

### Post by sudodus on 2016-04-24
Welcome to the Ubuntu Forums :-)

Do you want a normally installed Ubuntu system (but installed to the USB stick)?

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You should be able to use the whole USB stick. Please check the size and partition structure on it with the following command. Copy and paste the output into a reply.

```
df
sudo parted -ls
sudo lsblk -fm
```

If you are running in ***BIOS*** mode, you can use ***mkusb*** to wipe the first megabyte of the USB stick and or ***gparted*** to create a suitable partition table. When you run the installer, select ***Something else*** at the partitioning window and install the bootloader into the head of the USB stick (not into the internal disk, and not into any partition).

If your computer is running in ***UEFI*** mode there are complications, and I suggest that you make a system according to the following link

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

But the compressed image file wants a USB stick of 16 GB or more, so you can't use it, but you can use the instructions at the sub-page

[stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

and make it yourself :-)

-o-

An alternative is to make a persistent live drive, which is straight-forward with [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent). With only 8 GB it might be a better alternative.

---

### Post by gerald12 on 2016-04-25
Hi Sudodus,
my plan was to disconnect the HDD in some of the lesser PCs at work and use Lubuntu (because it's minimal and boots quick) on a 8gb usb as the primary boot device. To have it auto login (got that working), hide the tool bar etc (done that also) and auto run Remmina (cause it's a nice RDP client , and I couldn't find one that and cope with dual screens ). Check. 
But Lunbuntu then says it needed updating , but (because the usb drive was 1/2 the actual size, there was not enough disc space).
I'm not sure what BIOS mode is , sorry ( I'm booting from a live cd,and installing onto usb from there).

i'll look at your first link when I'm at work and see what happens.
thanks

---

### Post by sudodus on 2016-04-25
It is a good idea to disconnect the HDD when you boot the computer in BIOS mode. But in UEFI mode I'm afraid that it works only until you connect the internal drive again, unless you do some special tricks.

BIOS is the traditional boot system (that starts before the operating system is started). UEFI is a new boot system, that replaces BIOS on many newer computers. Windows 8 and 10 are usually installed in UEFI mode from the manufacturer or vendor. If you want a dual boot system with Windows, you had better run Lubuntu in the same mode (UEFI or {BIOS alias CSM}), otherwise you have to switch mode in the UEFI/BIOS menus every time you switch between Lubuntu and Windows.

When booted in UEFI mode there is a directory /sys/firmware/efi, so you can run the following command line,

```
test -d /sys/firmware/efi && echo efi || echo bios
```

to check which mode you are running.

---

### Post by gerald12 on 2016-04-28
HI,

Her is the output from the from the commands :-

DF
> NAME   FSTYPE   LABEL               UUID                                 MOUNTPOINT                                          NAME     SIZE OWNER GROUP MODE
sdb                                                                                                                          sdb      7.2G root  disk  brw-rw----
&#9492;&#9472;sdb1 ext4                         4911f792-2291-42d5-a636-62f36bb65d07 /media/lubuntu/4911f792-2291-42d5-a636-62f36bb65d07 &#9492;&#9472;sdb1   5.7G root  disk  brw-rw----
sdc                                                                                                                          sdc      1.9G root  disk  brw-rw----
&#9492;&#9472;sdc1 vfat                         BCAD-615D                            /media/lubuntu/BCAD-615D                            &#9492;&#9472;sdc1   1.9G root  disk  brw-rw----
sr0    iso9660  Lubuntu 15.10 amd64 2015-10-21-16-39-39-00               /cdrom                                              sr0      4.4G root  cdrom brw-rw----
loop0  squashfs                                                          /rofs                                               loop0  670.8M root  disk  brw-rw----
zram0                                                                    [SWAP]                                              zram0  962.1M root  disk  brw-rw----
zram1                                                                    [SWAP]                                              zram1  962.1M root  disk  brw-rw----


LSBLK
> NAME   FSTYPE   LABEL               UUID                                 MOUNTPOINT                                          NAME     SIZE OWNER GROUP MODE
sdb                                                                                                                          sdb      7.2G root  disk  brw-rw----
&#9492;&#9472;sdb1 ext4                         4911f792-2291-42d5-a636-62f36bb65d07 /media/lubuntu/4911f792-2291-42d5-a636-62f36bb65d07 &#9492;&#9472;sdb1   5.7G root  disk  brw-rw----
sdc                                                                                                                          sdc      1.9G root  disk  brw-rw----
&#9492;&#9472;sdc1 vfat                         BCAD-615D                            /media/lubuntu/BCAD-615D                            &#9492;&#9472;sdc1   1.9G root  disk  brw-rw----
sr0    iso9660  Lubuntu 15.10 amd64 2015-10-21-16-39-39-00               /cdrom                                              sr0      4.4G root  cdrom brw-rw----
loop0  squashfs                                                          /rofs                                               loop0  670.8M root  disk  brw-rw----
zram0                                                                    [SWAP]                                              zram0  962.1M root  disk  brw-rw----
zram1                                                                    [SWAP]                                              zram1  962.1M root  disk  brw-rw----


parted
> Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdb: 7759MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  6144MB  6143MB  primary  ext4

Model: Lenovo Slim_USB_Burner (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 
Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      3754kB  6081kB  2327kB               EFI

Model: Unknown (unknown)
Disk /dev/zram0: 1009MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 
Number  Start  End     Size    File system     Flags
 1      0.00B  1009MB  1009MB  linux-swap(v1)

Model: Unknown (unknown)
Disk /dev/zram1: 1009MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 
Number  Start  End     Size    File system     Flags
 1      0.00B  1009MB  1009MB  linux-swap(v1)

 


I tried selecting the "Something else" option when tried to install to the UDB from a lunbuntu live cd, and set the partitions to 6/2 rather than the 4/4 it is defaulting to (which causes an issue when it want to upgrade/date the OS). It seemed to start fine, but then errored saying there wasn't enough disk space to coy the files (I am assuming it copys the files to the swap partition, then installs on the Primary one?).
if this is the case, could/can I let it install with the 4gb/4gb partition of the 8gb disk, then resize the partitions afterwards ? ( if Lunbuntu still needs the swap file, else, use the whole USB) ?

Sorry... I'm worse than a Noob :-)... but at least I'm trying :-)

---

### Post by sudodus on 2016-04-28
We need to know more about your computer and the iso file in order to get further.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Is the computer running in BIOS or UEFI mode? This is important to know.

Which version of Lubuntu are you testing? 14.04.x LTS or some other version?

Have you checked with md5sum that the download was good?

-o-

No drive /dev/sda is shown in the output. Is there an internal drive, but it is not recognized? Or have you deleted the information about it?

You forgot the output of ***df***, instead there is double output from lsblk -fm

Please put the output within [noparse]```
tags
```[/noparse]. That makes it easier to read.

-o-

It was a good idea to use 6 GB for the root partition and 2 GB for swap. I suggest that you go further in that direction, and use only 512 MB for swap. You should use an 'ext4 file system' in the root partition and 'linux swap' in the swap partition.

After installing, it is very important to let the computer shut down completely before you unplug the pendrive. This is also the case after booting from it. If you unplug it before it has saved the buffered data from RAM to the pendrive, the file system will be corrupted.

If you still have problems, you should try with another pendrive. Most but not all pendrives work well as boot drives. There are several faster USB 3 drives with size 16 GB, while most 8 GB drives are rather slow (even if they are USB 3 drives), because the flash memory is cheap and slow.

---

### Post by gerald12 on 2016-04-28
HI,
- Brand name and model - Lenovo x200
 - CPU - Core 2 duo p8400 2.26ghz 800mhz
 - RAM (size) - 4gb
 - graphics chip/card - 
 - wifi chip/card - intel ultimate n wifi link

Computer is running BIOS (the HDD does have w10 on it thought)

Hard disk has been removed (seeing as last time I Fubared the Windows 10 install :-) ).

lunbuntu image is lubuntu-15.10-desktop-amd64.

Download is/was fine.

I'm just trying to install again (using the partition sizes you suggested). I'll report any success' / failures (inc the Df output...sorry about that).

---

### Post by sudodus on 2016-04-28
Thanks for this information :-)

I think Lubuntu should run well in this computer. (With 4 GB RAM) 512 MB swap will be OK but you will not be able to hibernate.

There might be issues with the most recent versions of Ubuntu and some graphics hardware. Is it possible for you to find you the brand name and model, maybe via the internet? Or via ***hardinfo***, that you can run from the Lubuntu live system 'Try Lubuntu'.

-o-

An alternative to a conventional installation is to flash an 'already installed system' from a compressed image file with [mkusb](https://help.ubuntu.com/community/mkusb) or compressed tar file alias tarball with the [One Button Installer](https://help.ubuntu.com/community/OBI).

Maybe you can start with a text only mini-system and add the Lubuntu desktop afterwards (if that is what you want). If your pendrive has at least 7.8 GB, you can install from the following compressed image file with mkusb.

**dd_Xenial-32-txt.img.xz (16.04 LTS)**

[http://phillw.net/isos/linux-tools/compressed-images/dd_Xenial-32-txt.img.xz]()

Otherwise you can install from the following tarballs

[B]Trusty-mini-txt6.tar.xz (14.04 LTS)
Xenial-32-txt.tar.xz (16.04 LTS)[/B]

[http://phillw.net/isos/linux-tools/OBI/trusty/](http://phillw.net/isos/linux-tools/OBI/trusty/) or directly via the starter menu of the One Button Installer.

-o-

Find more details at

[https://help.ubuntu.com/community/OBI/Trusty-mini-txt](https://help.ubuntu.com/community/OBI/Trusty-mini-txt)

[https://help.ubuntu.com/community/OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by sudodus on 2016-04-28
```
sudo lsblk -fm
NAME FSTYPE LABEL UUID MOUNTPOINT NAME SIZE OWNER GROUP MODE
sdb sdb 7.2G root disk brw-rw----
&#9492;&#9472;sdb1 ext4 4911f792-2291-42d5-a636-62f36bb65d07 /media/lubuntu/4911f792-2291-42d5-a636-62f36bb65d07 &#9492;&#9472;sdb1 5.7G root disk brw-rw----
[COLOR="#FF0000"]-----<  no swap partition here  >-----[/COLOR]
sdc sdc 1.9G root disk brw-rw----
&#9492;&#9472;sdc1 vfat BCAD-615D /media/lubuntu/BCAD-615D &#9492;&#9472;sdc1 1.9G root disk brw-rw----
sr0 iso9660 Lubuntu 15.10 amd64 2015-10-21-16-39-39-00 /cdrom sr0 4.4G root cdrom brw-rw----
loop0 squashfs /rofs loop0 670.8M root disk brw-rw----
zram0 [SWAP] zram0 962.1M root disk brw-rw----
zram1 [SWAP] zram1 962.1M root disk brw-rw----

sudo parted -ls
Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdb: [COLOR="#FF0000"]**7759**[/COLOR]MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type File system Flags
1 1049kB 6144MB 6143MB primary ext4
```

1. I see no swap partition. The tail end of TOSHIBA TransMemory seems unallocated.

2. The size of the TOSHIBA TransMemory is too small (it is severely undersized, below the 8 GB specification)

7759 MB < 7800 MB

You can see the uncompressed size in bytes in column #5 of the output of the following command line:

```
xz --robot --list dd_Xenial-32-txt.img.xz
name	dd_Xenial-32-txt.img.xz
file	1	1	296787092	7[COLOR="#FF0000"]800[/COLOR][COLOR="#0000FF"]356[/COLOR]864	0.038	CRC64	0
totals	1	1	296787092	7800356864	0.038	CRC64	0	1
```

So you cannot use the compressed image file. But you can still use the tarballs. Try both and continue with the one that works better in your computer.

***Edit:*** ... or you can get a fast USB 3 pendrive with 16 GB or more memory :-)

---

### Post by gerald12 on 2016-04-28
Hi,

I did want you suggested re the partitioning, and it installed without an issue. It's currently updating to 16.04 "installing the upgrades".

THANK YOU EVERSO MUCH for you help.

In the future, I'll get bigger drives :-)

---

### Post by sudodus on 2016-04-28
Good luck with "installing the upgrades" :-)

If the installation and upgrades are successful, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by gerald12 on 2016-04-29
HI,

Updates installed without an issue. Thank you again.

---

